# Fase 1: Coneixement el terremy i la competència 

## 1. Recerca de mercat: 3 Competidors al Maresme

### Empresa 1: JSM Inforedes, S.L

Aquesta Empresa s´ubica al Polígon Balançó i Boter, a Mataró, es una empresa PIME petita.

Es dedica al manteniment, cloud, ciberseguretat i al programari de gestió. 



### Empresa 2: ESED (ciberseguretat)

Aquesta empresa s´ubica a Mataró (tecnocampus), es una empresa PIME especialitzada.

Aquesta empresa es dedica a la ciberseguretat pura: Hacking ètic, serveis gestionats, protecció de dades.



### Empresa 3: Grup Qualitat

Aquesta empresa té varias seus per tot al maresma, es una empresa PIME mitjana.

Es dediquen a la consultoria i sololucions TIC per la logística i administracions públiques. Són els mes importants de la comarca del maresme.



## 2. Organigrama:

Hem triat JSM inforedes com a model perquè es l´estructura més habitual  en una PIME de serveis informàtics d´uns 10 a 15 treballadors. Aqui deixem al codi PlanUML la pàgina web per veurel de manera gràfica:

Enllaç: https://www.plantuml.com/plantuml/uml/SyfFKj2rKt3CoKnELR1Io4ZDoSa700001

Codi ornanigrama:

 @startuml
!theme plain
title Organigrama - Empresa de Serveis Informàtics (PIME tipus a Mataró)

' Definició dels nodes
rectangle "Direcció General / Propietari" as Dir
rectangle "Administració\n(Finances i RRHH)" as Admin
rectangle "Cap de Sistemes i Xarxes" as CapTecnic
rectangle "Cap de Projectes / CTO" as CapProjectes
rectangle "Departament Comercial\n(Vendes i Màrqueting)" as Comercial

' Sub-departaments tècnics
rectangle "Equip de Suport (Helpdesk)\n(Nivell 1 i 2)" as Suport
rectangle "Equip de Desplegament\n(Xarxes i Hardware)" as Desplegament
rectangle "Equip de Ciberseguretat\n(Serveis Gestionats)" as Seguretat

' Relacions jeràrquiques
Dir -down-> Admin
Dir -down-> Comercial
Dir -down-> CapTecnic
Dir -down-> CapProjectes

CapTecnic -down-> Suport
CapTecnic -down-> Desplegament
CapTecnic -down-> Seguretat

' Notes explicatives (en català)
note right of Dir
  Pren decisions estratègiques.
  Busca socis (SAGE, Microsoft).
  És la cara visible.
end note

note bottom of Seguretat
  En una PIME petita,
  aquest rol pot ser extern
  o compartit amb el Cap Tècnic.
end note
@enduml


## Radiografia de departaments:

| Departament | Funcions principals | Per què és clau per a FoodLogístic? |
| :--- | :--- | :--- |
| **Direcció / Gerència** | Estratègia, gestió de personal, rendibilitat, ser la cara visible en reunions importants. | Transmet confiança. Un client gran vol parlar amb el cap, no amb un becari. |
| **Comercial i Màrqueting** | Captar clients, preparar pressupostos (RFPs), gestionar la relació. | Necessitaràs preparar una proposta competitiva. Si ets autònom, aquesta funció és teva. |
| **Departament Tècnic (Operacions)** | Helpdesk: Resoldre incidències remotes (correu, xarxa, programari). Desplegament: Instal·lació in situ de servidors, cablejat, routers. Ciberseguretat: Monitorització, còpies de seguretat, protecció de dades. | La logística no pot parar. Si cau el sistema, perden diners cada minut. Necessiten un equip tècnic ràpid. |
| **Infraestructura i Cloud** | Servidors, virtualització (VMware), núvol (Azure, AWS). | FoodLogístic vol "renovar a fons". Segur que volen migrar part al núvol. |
| **Administració (Backoffice)** | Facturació, compres a proveïdors (Ingram Micro, Sage...), gestió de personal. | Perquè tot funcioni per dins i tu puguis cobrar. |



## Per què hem de saber tot això?

Vendre millor: Si ells tenen un problema de ciberseguretat, els pots dir que tu ho controles (com ESED). Si volen algú de confiança que ho faci tot, els dius que ets com JSM però més proper.

Per diferenciar-nos: La competència gran és lenta i cara. La petita (JSM) pot ser massa genèrica. Tu pots ser l'equilibri perfecte: tècnic, proper i amb ganes de demostrar que ets el millor.

# FASE 2: ESTRATÈGIA

## Definició de l’estratègia

Per aconseguir que **Foodlogístic S.A.** ens esculli davant la competència, definim una proposta de valor clara basada en tres pilars:

---

### 1. Proximitat i tracte personal

Som una empresa local de Mataró, cosa que ens permet:

- Intervencions ràpides in situ  
- Relació directa amb el client  
- Comunicació sense intermediaris  

A diferència d’empreses grans com Grup Qualitat, oferim un tracte més proper i flexible.

---

### 2. Servei ràpid i flexible (quasi 24/7)

- Temps de resposta molt baixos  
- Resolució remota immediata  
- Sistema d’urgències per incidències crítiques  

Per una empresa logística com Foodlogístic, cada minut compta.  
Si el sistema cau, es perden diners.

---

### 3. Especialització en seguretat + servei integral

Combinem dos models:

- Especialització en ciberseguretat (com ESED)  
- Servei global (com JSM)  

Oferim:

- Protecció contra ciberatacs  
- Migració al núvol (Azure / AWS)  
- Còpies de seguretat automatitzades  
- Manteniment complet  

Ens posicionem com l’equilibri perfecte:

- No tan genèrics com els petits  
- No tan cars ni lents com els grans  

---

### 4. Preu competitiu amb alt valor

- Tarifes ajustades a PIME  
- Packs de serveis (manteniment + seguretat + cloud)  
- Escalable segons el creixement  

No som els més barats, però sí els que ofereixen millor relació qualitat-preu.

---

## Estratègia resumida

Som una empresa local, ràpida i especialitzada que ofereix un servei complet, segur i adaptat a les necessitats reals d’una empresa logística.

---

## Recursos necessaris

Per donar servei a un client com FoodLogístic, necessitem un equip mínim amb aquests rols:

### Equip humà necessari

#### 1. Tècnic de sistemes (Cloud)

- Gestió de servidors i xarxes  
- Virtualització i cloud  
- Resolució d'incidències complexes  

**Clau per la infraestructura principal**

---

#### 2. Tècnic Helpdesk (Junior / Mid)

- Suport a usuaris  
- Resolució d'incidències habituals  
- Atenció remota  

---

#### 3. Especialista en ciberseguretat

- Monitorització  
- Auditories de seguretat  
- Gestió de backups i protecció de dades  

Pot ser:

- Intern (ideal)  
- Externalitzat (al principi)  

---

#### 4. Especialista en Cloud / DevOps *(opcional però recomanat)*

- Migració a Azure / AWS  
- Automatització  
- Optimització de recursos  

**Important si el client vol modernitzar-se**

---

#### 5. Comercial / Gestor de compte

- Relació amb el client  
- Seguiment del servei  
- Propostes de millora  

Si ets autònom, aquest rol és teu.

---

#### 6. Administració

- Facturació  
- Gestió de proveïdors  
- Control econòmic  

Pot ser parcial o externalitzat.

---

## Som suficients o cal contractar?

### Situació inicial (empresa petita)

Si esteu començant:

❌ No sou suficients per cobrir-ho tot  

✔️ Podeu assumir:

- 1 tècnic principal  
- 1 helpdesk  
- Comercial (vosaltres mateixos)  

### Solució realista

- Externalitzar ciberseguretat al principi  
- Contractar helpdesk quan creixi la càrrega  
- Escalar equip segons necessitats  

---

## Conclusió de recursos

No cal una gran empresa per guanyar el client, però sí:

- Bona organització  
- Suport extern intel·ligent  
- Capacitat de créixer ràpid  
