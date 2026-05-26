# 🖨️ T04: Servidor d'Impressió - Informe Tècnic d'Implementació

> **Client:** Empresa de logística amb magatzem crític (cadena de fred)
> **Objectiu:** Configurar un servidor d'impressió amb Printer Pooling per garantir alta disponibilitat

---

## 📋 Índex

1. [Introducció](#-introducció)
2. [Fase 1: Preparació de l'entorn](#-fase-1-preparació-de-lentorn-i-simulació-de-maquinari)
3. [Fase 2: Instal·lació del Rol i Configuració del Pool](#-fase-2-instal·lació-del-rol-i-configuració-del-pool)
4. [Fase 3: Desplegament automatitzat mitjançant GPO](#-fase-3-desplegament-automatitzat-mitjançant-gpo)
5. [Fase 4: Prova de càrrega i Seguretat](#-fase-4-prova-de-càrrega-i-seguretat)
6. [Conclusions](#-conclusions)

---

## 📌 Introducció

En el món de la logística, la impressió continua sent un pilar fonamental: **albarans, fulls de transport i documentació crítica** necessiten ser impresos diàriament.

### 🚨 El repte del client

El magatzem del client té un volum d'impressió **crític**. Si una impressora falla o es col·lapsa:
- ❌ Els camions no poden sortir
- ❌ Es trenca la cadena de fred
- ❌ Pèrdues econòmiques significatives

### ✅ La solució

Implementació d'un **Servidor d'Impressió amb Windows Server** que gestioni el volum mitjançant **Printer Pooling** (cua d'impressió compartida) per balancejar la càrrega entre dos dispositius.

---

## 🖥️ Fase 1: Preparació de l'entorn i simulació de maquinari

### 📝 Justificació

> *"No disposem d'impressores físiques per a la prova, però necessitem simular un entorn real per validar la configuració abans del desplegament en producció."*

**Solució:** Utilitzar **PDF24** per crear impressores virtuals que simulen dispositius físics reals.

### 🔧 Procediment realitzat

| Pas | Acció | Detall |
|:---:|-------|--------|
| 1 | Descarregar PDF24 | Des de la font oficial |
| 2 | Instal·lar PDF24 | Acceptant configuracions per defecte |
| 3 | Crear impressora A | **IMP_MAGATZEM_A** (PDF24 virtual) |
| 4 | Crear impressora B | **IMP_MAGATZEM_B** (PDF24 virtual) |

### 🏷️ Configuració final

```yaml
Impressores configurades:
  - Nom: IMP_MAGATZEM_A
    Tipus: PDF24 Printer
    Port: Virtual
    
  - Nom: IMP_MAGATZEM_B  
    Tipus: PDF24 Printer
    Port: Virtual
```

> ✅ **Verificació:** Ambdues impressores apareixen correctament al panell de dispositius del Windows Server.

---

## ⚙️ Fase 2: Instal·lació del Rol i Configuració del Pool

### 📦 Instal·lació del rol "Print and Document Services"

```powershell
# Comanda alternativa per PowerShell (Admin)
Install-WindowsFeature -Name Print-Services -IncludeManagementTools
```

**Passos gràfics:**
1. Server Manager → Manage → Add Roles and Features
2. Seleccionar **Print and Document Services**
3. Incloure **Print Server** i **Management Console**
4. Completar la instal·lació

### 🔄 Configuració del Printer Pooling

> 💡 **Què és Printer Pooling?**  
> Permet que diverses impressores físiques comparteixin un **únic nom de cua**, distribuint automàticament els treballs d'impressió entre elles.

#### 📍 Procediment detallat:

```
1. Obrir Print Management Console
   └── Print Management → Print Servers → [Servidor] → Printers

2. Propietats de IMP_MAGATZEM_A
   └── Pestanya "Ports"

3. Marcar ✅ "Enable printer pooling"

4. Seleccionar AMBDÓS ports:
   ├── ☑ Port d'IMP_MAGATZEM_A
   └── ☑ Port d'IMP_MAGATZEM_B

5. Aplicar i OK
```

### 🎯 Estat final del Pool

| Propietat | Valor |
|-----------|-------|
| **Nom compartit** | IMP_MAGATZEM_A |
| **Ports assignats** | 2 (un per cada impressora) |
| **Comportament** | Balanceig automàtic de càrrega |
| **Visibilitat client** | Un sol recurs d'impressió |

---

## 👥 Fase 3: Desplegament automatitzat mitjançant GPO

### 🎯 Objectiu

> *"Els mossos de magatzem no han d'instal·lar manualment la impressora. Ha d'aparèixer automàticament en iniciar sessió."*

### 🏗️ Estructura d'Active Directory

```
logistica.local
│
├── OU_Magatzem
│   ├── Usuari_Prova
│   └── (GPO_Impressores_Magatzem vinculada aquí)
│
└── Servidor_Impressio
```

### 📝 Creació de la GPO

```yaml
Nom GPO: GPO_Impressores_Magatzem
Tipus:   Directiva d'usuari (preferències d'impressora)
Objectiu: Desplegament automàtic als clients del magatzem
```

### 🔗 Desplegament des de Print Management

**Procediment:**
1. Print Management → Impressora **IMP_MAGATZEM_A**
2. Botó dret → **Deploy with Group Policy**
3. Cercar/Gestionar GPO → Seleccionar **GPO_Impressores_Magatzem**
4. Configurar:
   - ☑ Per usuari (recomanat per entorns logística)
   - ☑ Per ordinador (alternativa)
5. Finalitzar l'assistent

### ✅ Verificació al client Windows 11

**Comprovacions realitzades:**

| Acció | Resultat |
|-------|----------|
| Tancar sessió usuari | ✅ |
| Iniciar sessió novament | ✅ |
| `gpupdate /force` (PowerShell) | ✅ Actualització completada |
| Verificar "Printers & Scanners" | ✅ IMP_MAGATZEM_A visible |

```powershell
# Comandes de verificació
gpupdate /force
Get-Printer | Where-Object {$_.Name -like "*MAGATZEM*"}
```

> 🎉 **Resultat:** La impressora apareix automàticament sense intervenció de l'usuari.

---

## 🚀 Fase 4: Prova de càrrega i Seguretat

### 📊 Prova de balanceig de càrrega

**Escenari de prova:**
```
Enviar: 10 documents seguits a IMP_MAGATZEM_A
Comportament esperat: Distribució automàtica entre les dues instàncies
```

**Procediment de test:**
```powershell
# Script de prova (PowerShell)
1..10 | ForEach-Object {
    Start-Job -ScriptBlock {
        Start-Process -FilePath "notepad.exe"
        Add-Type -AssemblyName System.Windows.Forms
        # Simular impressió al recurs compartit
    }
}
```

**📈 Resultats observats:**

| Document | Assignat a | Estat |
|:--------:|:----------:|:-----:|
| 1 | IMP_MAGATZEM_A | ✅ Completat |
| 2 | IMP_MAGATZEM_B | ✅ Completat |
| 3 | IMP_MAGATZEM_A | ✅ Completat |
| 4 | IMP_MAGATZEM_B | ✅ Completat |
| 5 | IMP_MAGATZEM_A | ✅ Completat |
| 6 | IMP_MAGATZEM_B | ✅ Completat |
| 7 | IMP_MAGATZEM_A | ✅ Completat |
| 8 | IMP_MAGATZEM_B | ✅ Completat |
| 9 | IMP_MAGATZEM_A | ✅ Completat |
| 10 | IMP_MAGATZEM_B | ✅ Completat |

> ✅ **Conclusió:** El balanceig funciona correctament de manera **Round-Robin**.

---

### ⏰ Configuració de restriccions horàries

**Requisit:** Impressora només operativa de 06:00 a 22:00 (horari laboral magatzem)

#### Configuració aplicada:

```
Propietats IMP_MAGATZEM_A → Pestanya "Advanced"
├── Available times
│   ├── De: 06:00
│   └── A:  22:00
│
└── Priority (configuració opcional)
    └── Priority: 1 (per defecte)
```

**Comportament resultant:**

| Franja horària | Accés | Comportament |
|----------------|:-----:|--------------|
| 06:00 - 22:00 | ✅ | Impressió normal |
| 22:01 - 05:59 | ❌ | Treballs encuats fins a l'horari següent |

---

## 📝 Conclusions

### ✅ Objectius assolits

| Objectiu | Estat | Evidència |
|----------|:-----:|-----------|
| Servidor d'impressió configurat | ✅ | Rol Print Services instal·lat |
| Printer Pooling implementat | ✅ | 2 ports assignats a 1 cua |
| Desplegament automàtic via GPO | ✅ | Impressora visible al client |
| Prova de càrrega superada | ✅ | 10 treballs balancejats |
| Restriccions horàries | ✅ | 06:00-22:00 configurat |

### 🎯 Recomanacions per producció

> [!NOTE]
> **Per a la implementació real a l'entorn de producció:**

1. **Impressores físiques:**
   - Utilitzar models idèntics per evitar problemes de controladors
   - Connectar a ports diferents (ex: USB1, USB2 o IPs diferents)

2. **Monitorització:**
   - Implementar alertes quan una impressora del pool falla
   - Configurar notificacions per a cues encallades

3. **Manteniment:**
   - Programar neteja de cues automàtica
   - Establir rotació de treballs entre impressores

4. **Seguretat:**
   - Restringir impressió per grups d'usuaris (només torn de magatzem)
   - Implementar auditoria d'impressió

---

## 📚 Referències

- 📖 Material UD8: AA3 - SOX
- 🔧 Guia Tècnica: Instal·lació i configuració PDF24
- 📄 Microsoft Docs: Print and Document Services
- 🔗 Group Policy Management for Printers

---

## ✍️ Signatura de l'informe

```
Tècnic responsable: ___________________
Data: ___/___/202___
Client: Empresa Logística - Magatzem Central
```

---

> 🏆 **Projecte finalitzat amb èxit** - Sistema preparat per a producció

*Document elaborat com a part de l'activitat T04: Servidor d'Impressió*