A continuació tens una proposta de **README.md** professional i estructurada per a la tasca **T09**, dissenyada per ser el document central de la carpeta `/P01/Planificacio/`. 

Aquest document està redactat per transmetre el rigor que demana la direcció de *FoodLogístics S.A.*

---

# T09: Estimació Temporal i Planificació de Projecte - FoodLogístics S.A.

## 1. Introducció
Aquest document detalla la planificació estratègica per al desplegament de la solució tecnològica sol·licitada per **FoodLogístics S.A.** L'objectiu d'aquesta planificació no és només listar tasques, sinó garantir la viabilitat del projecte mitjançant una anàlisi rigorosa de dependències, càrrega de treball i gestió de riscos.

L'equip ha optat per una metodologia de treball en paral·lel en les fases de recerca, mantenint un flux seqüencial estricte en les fases d'implementació crítica per assegurar la integritat de la infraestructura.

## 2. Estratègia de Planificació i Dependències
La planificació s'estructura en un cicle de **3 setmanes**, dividit en quatre blocs lògics:

1.  **Fase d'Anàlisi i Disseny (T01-T02):** Fonaments teòrics i definició de l'arquitectura.
2.  **Fase d'Infraestructura Base (T03-T04):** Configuració de l'entorn virtual i xarxa. No es pot avançar sense aquests fonaments (bloqueig crític).
3.  **Fase de Serveis i Seguretat (T05-T07):** Implementació de serveis i blindatge del sistema. Moltes d'aquestes tasques es realitzen en paral·lel.
4.  **Fase de Proves i Tancament (T08):** Auditoria final i documentació de lliurament.

### Justificació de l'Ordre
S'ha prioritzat la **seguretat (T07)** i el **monitoratge (T06)** un cop la xarxa és estable, però abans de donar el projecte per finalitzat, assegurant que qualsevol vulnerabilitat es detecti en la fase de proves.

## 3. Estimació d'Esforç
Les estimacions no són arbitràries; cada tasca ha estat avaluada considerant:
* **Recerca i Comprensió:** 20% del temps.
* **Implementació Tècnica:** 50% del temps.
* **Proves i Depuració (Debugging):** 20% del temps.
* **Documentació:** 10% del temps.

*S'ha aplicat un marge de seguretat (buffer) del 15% en tasques d'infraestructura cloud per preveure latències o errors de configuració de tercers.*

## 4. Diagrama de Gantt (PlantUML)

A continuació es presenta la representació visual del projecte. El codi font es troba a l'arxiu `gantt.puml` d'aquesta mateixa carpeta.

![Diagrama de Gantt](ruta-a-la-teva-imatge.png)

*(Nota: Cal adjuntar aquí la captura del diagrama generat amb UMLTree)*

## 5. Matriu de Responsabilitats (RACI)

| Tasca | Responsable (R) | Responsable Final (A) | Consultat (C) | Informat (I) |
| :--- | :---: | :---: | :---: | :---: |
| T01: Anàlisi de Requisits | Membre A | Membre B | Equip | Direcció |
| T02: Disseny Arquitectura | Membre B | Membre A | Membre C | Direcció |
| T03: Configuració Servidors | Membre C | Membre B | Membre A | Direcció |
| T04: Desplegament Xarxa | Membre A | Membre B | Membre C | Direcció |
| T05: Serveis Interns | Membre B | Membre A | Equip | Direcció |
| T06: Monitoratge | Membre C | Membre A | Membre B | Direcció |
| T07: Seguretat i Firewall | Membre A | Membre B | Equip | Direcció |
| T08: Proves Finals | Equip | Membre B | Direcció | Direcció |

## 6. Gestió de Riscos i Contingències

| Risc Identificat | Impacte | Probabilitat | Mesura de Contingència |
| :--- | :--- | :--- | :--- |
| **Incompatibilitat de programari** | Alt (Retard en T05) | Mitjana | Ús de contenidors (Docker) per aïllar dependències. |
| **Caiguda del node principal** | Crític (Atura T03-T08) | Baixa | Disseny de clúster amb alta disponibilitat i backups diaris. |
| **Retard en el Camí Crític** | Mitjà (Retard entrega) | Mitjana | Reassignació de recursos de tasques no bloquejants cap a la tasca crítica. |

## 7. Preguntes de Reflexió (Key Insights)

* **Quina és la tasca més crítica del projecte i per què?**
    La tasca **T03 (Configuració de Servidors)**. És l'arrel de tota la implementació física/virtual; si els servidors no estan ben dimensionats o configurats, totes les tasques posteriors (T04-T08) arrossegaran errors de base.
* **On heu detectat el principal coll d’ampolla?**
    En la transició entre **T04 (Xarxa)** i **T05 (Serveis)**. Molts serveis depenen d'una configuració de DNS i IP específica que, si falla, impedeix provar qualsevol aplicació.
* **Quina decisió de planificació ha estat més difícil?**
    Decidir quines tasques podien anar en paral·lel. Vam haver de decidir si la Seguretat (T07) es feia al final o durant el procés; finalment es fa en paral·lel al monitoratge per guanyar temps.
* **Heu hagut de modificar alguna estimació inicial?**
    Sí, vam augmentar un 30% el temps de **T04** després de comprovar la complexitat de les VLANs requerides per FoodLogístics.
* **Quin risc podria fer fracassar el projecte?**
    Un desajust en el pressupost de recursos cloud o la pèrdua d'accés a les credencials administratives sense un pla de recuperació de desastres actiu.
* **Si tinguéssiu una setmana més, què canviaríeu?**
    Implementaríem una fase extra d'**Auditoria Externa de Seguretat (Penetration Testing)** i una formació més extensa per als empleats de FoodLogístics.

---

### Fitxers adjunts en aquesta carpeta:
* `README.md` (Aquest document)
* `planificacio.puml` (Codi font PlantUML)
* `gantt_chart.png` (Imatge exportada del diagrama)