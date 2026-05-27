# 🔍 T01: Coneixent la Competència i el Sector (FoodLogistic S.A.)

---

## 🏢 1. Introducció i Context del Cas

Com a socis fundadors d'**EverPia Solutions**, la nostra cooperativa de serveis informàtics a Mataró, ens trobem davant del nostre primer gran repte comercial: **FoodLogístic S.A.**, una potència en la distribució alimentària ubicada al Polígon de les Hortes del Camí Ral. 

Aquest client requereix una modernització integral de la seva infraestructura (sistemes, xarxes i ciberseguretat LOPD). Per garantir que som l'opció escollida enfront de la competència local del Maresme, hem realitzat un estudi de mercat, una radiografia estructural del sector i la definició de la nostra proposta de valor.

---

## 📊 Fase 1: Anàlisi de Mercat i Competència Local

### 🏢 1.1 Recerca i Classificació d'Empreses del Sector al Maresme

Per conèixer el terreny on competim, hem identificat tres empreses reals del sector IT que operen a Mataró i rodalies:

| Empresa | Ubicació | Mida | Serveis Principals |
| :--- | :--- | :--- | :--- |
| **Grup CBS Quality** | Mataró (Centre) | PIME | Manteniment informàtic integral, auditories de seguretat, xarxes i telefonia IP corporativa. |
| **Inforestudio** | Mataró (Via Europa) | Microempresa | Suport tècnic de proximitat, configuració de servidors locals i gestió de còpies de seguretat. |
| **Maresme Connect** | Premià de Mar / Mataró | PIME | Infraestructura de xarxes de comunicacions, connectivitat industrial i cloud computing. |

---

### 📉 1.2 L'Organigrama de la Competència Tipus (PlantUML)

A continuació, es representa l'estructura organitzativa d'una PIME tipus del sector de serveis informàtics de la comarca, dissenyada per donar suport a clients industrials i logístics:

```plantuml
@startuml
skinparam monochrome false
skinparam packageStyle rectangle
skinparam shadowing false

title Organigrama Tipus - PIME de Serveis IT (Maresme)

node "Direcció General (CEO)" as CEO #DDFFFF

package "Àrea de Negoci i Gestió" {
    agent "Departament Comercial" as Comercial #FFF0F5
    agent "Administració i RH" as Admin #FFF0F5
}

package "Àrea Tècnica i Operacions" {
    agent "Departament de Sistemes i Cloud" as Sistemes #E6F2FF
    agent "Departament de Seguretat i LOPD" as Seguretat #E6F2FF
    agent "Suport Tècnic / Helpdesk" as Helpdesk #E6F2FF
}

CEO --> Comercial
CEO --> Admin
CEO --> Sistemes
CEO --> Seguretat

Sistemes --> Helpdesk : Escalat N2/N3
Seguretat --> Helpdesk : Polítiques
@enduml