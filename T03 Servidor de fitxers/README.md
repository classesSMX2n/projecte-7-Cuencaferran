Aquí tens l'informe tècnic detallat, estructurat i optimitzat en format **Markdown**, a punt per ser lliurat. Està dissenyat per ser visual, professional i fàcil de llegir.

---

# 📂 Informe Tècnic: Implementació de Servidor de Fitxers
**Projecte:** Infraestructura de dades per a **FoodLogistic** **Responsable:** Administrador de Sistemes  
**Data:** 13 d'abril de 2026  

---

## 📝 1. Resum de l'Estratègia
Aquest document detalla la centralització de les dades de **FoodLogistic**, passant d'emmagatzematge local a una infraestructura segura sota el domini `foodlogistic.test`. S'han aplicat polítiques de seguretat NTFS/SMB, control de quotes i filtratge de fitxers (FSRM).

### 📊 Taula de Recursos Compartits
| Carpeta | Camí UNC | Grup amb Accés | Mètode de Creació | Característiques |
| :--- | :--- | :--- | :--- | :--- |
| **Public** | `\\SRV\Public` | Tothom (Everyone) | Explorador d'arxius | Permisos lectura/escriptura |
| **Operacions** | `\\SRV\Operacions` | Transport | Server Manager | Access-Based Enumeration |
| **Confidencial**| `\\SRV\Direccio` | Direcció | PowerShell Avançat | Recurs ocult / Unitat Z: |

---

## 🛠️ 2. Preparació de l'Active Directory (AD)

S'ha dissenyat una estructura d'Unitats Organitzatives (OU) per facilitar l'administració:
* **OU FoodLogistic**: Conté totes les sub-unitats.
    * **OU Grups**: Grups de seguretat.
    * **OU Usuaris**: Comptes de treballadors.

### 👥 Grups de Seguretat Creats:
* **🛡️ Administracio**: Gestió de factures i albarans.
* **🚚 Transport**: Xofers i caps de flota.
* **💼 Direccio**: Gerència i alta direcció.

---

## 🚀 3. Implementació de Recursos Compartits

### A. Carpeta Public (Explorador de fitxers) 📂
Configuració ràpida per a intercanvi general:
1.  **SMB:** Permisos de "Lectura" per a `Everyone`.
2.  **NTFS:** Permisos de "Modificació" per a `Users` del domini.
> **Nota:** La seguretat efectiva és la més restrictiva. En aquest cas, l'usuari pot veure però no esborrar si l'SMB limita la lectura.

### B. Carpeta Operacions (Server Manager) 🖥️
Ús del rol *File and Storage Services*:
* Habilitat l'**Access-Based Enumeration (ABE)**: Si un usuari no és del grup **Transport**, ni tan sols veurà la carpeta a la xarxa.

### C/D. Carpeta Confidencial (PowerShell Avançat) 🐚
S'ha optat pel mètode D per la seva eficiència i automatització:

```powershell
# Creació de la carpeta física
New-Item -Path "D:\Dades\Direccio" -ItemType Directory

# Compartir amb Access-Based Enumeration habilitat
New-SmbShare -Name "Direccio" -Path "D:\Dades\Direccio" `
             -FullAccess "FOODLOGISTIC\Direccio" `
             -ReadAccess "Everyone" `
             -FolderEnumerationMode AccessBased

# Mapeig automàtic via GPO
# Configuració de la Unitat Z: mitjançant User Configuration > Preferences > Windows Settings > Drive Maps
```

---

## 💾 4. Control d'Emmagatzematge

### 📏 Quotes NTFS (Límit per Volum)
S'estableix un control preventiu a nivell de disc:
* **Límit per defecte:** 500 MB per usuari.
* **Acció:** Denegar espai de disc quan se superi el límit.

### 🛡️ FSRM (File Server Resource Manager)
S'han configurat regles específiques per evitar l'abús de l'emmagatzematge:

1.  **Quota de Carpeta (Public):**
    * **Límit:** 200 MB (Hard Quota).
    * **Notificació:** Al arribar al 90%, es dispara un missatge personalitzat: 
        > ⚠️ *Compte! FoodLogístic t'informa que estàs a punt d'esgotar l'espai compartit.*

2.  **Filtrat de Fitxers (Operacions):**
    * **Bloqueig actiu:** Fitxers Executables (`.exe`, `.msi`) i Multimèdia.
    * **Seguretat:** El filtratge actiu d'FSRM analitza la capçalera del fitxer; canviar l'extensió a `.txt` no permetrà saltar-se la restricció.

---

## ✅ 5. Verificació i Proves de Funcionament

| Prova | Resultat Esperat | Estat |
| :--- | :--- | :--- |
| **Accés Direcció** | Veu la unitat Z: i la carpeta Confidencial. | ✅ OK |
| **Accés Transport** | Veu Operacions; NO veu Confidencial (ABE). | ✅ OK |
| **Còpia .exe a Operacions** | El sistema denega l'operació (FSRM). | 🚫 Bloquejat |
| **Canvi extensió .exe -> .txt** | El servidor detecta el contingut i el bloqueja. | 🚫 Bloquejat |
| **Límit 200MB a Public** | En arribar a 180MB, salta l'avís d'alerta. | ⚠️ Alerta OK |

---

## 📸 6. Evidències (Captures suggerides)
1.  **AD:** Captura de la consola `dsa.msc` amb les OUs i Grups.
2.  **SMB:** Propietats de la carpeta compartida `Operacions` al Server Manager.
3.  **PS:** Pantallat de l'execució del cmdlet `New-SmbShare`.
4.  **FSRM:** Captura de la consola de *File Server Resource Manager* mostrant el filtre actiu.
