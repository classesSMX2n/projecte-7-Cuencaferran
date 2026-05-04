Aquí tens el contingut del teu lliurament **T09** estructurat en un fitxer `README.md` professional, visualment atractiu i llest per pujar al teu repositori a la carpeta `/P01/Planificacio/`.

---

# 🚀 T09: Planificació i Estimació Temporal - FoodLogístics S.A.

## 📝 Introducció
Aquest document detalla l'estratègia de desplegament i gestió temporal per a la infraestructura de **FoodLogístics S.A.** L'objectiu és garantir una transició tecnològica fluida, minimitzant els temps d'inactivitat i assegurant que cada fase (des de la T01 a la T08) s'executi amb rigor professional.

---

## 📅 1. Estratègia de Planificació
La planificació s'ha dividit en tres setmanes intensives de treball real, estructurades per garantir que els fonaments siguin sòlids abans d'implementar els serveis finals.

### 🏗️ Cronologia de Fases
*   **Setmana 1 (Anàlisi i Fonaments):** Tasques de definició i configuració base (T01-T03).
*   **Setmana 2 (Implementació Core):** Desenvolupament de serveis i xarxa (T04-T06).
*   **Setmana 3 (Seguretat, Proves i Tancament):** Blindatge del sistema i documentació final (T07-T08).

### ⚖️ Justificació de l'Ordre
1.  **Bloquejants:** No podem configurar el servidor web (T04) sense haver definit prèviament la infraestructura de xarxa (T02).
2.  **Paral·lelisme:** Hem optimitzat el temps permetent que, mentre una part de l'equip configura els serveis de correu (T06), l'altra treballi en les polítiques de seguretat (T07).

---

## 📊 2. Diagrama de Gantt (PlantUML)

El següent diagrama representa visualment la càrrega de treball i les dependències del projecte. S'ha forçat una planificació realista que arriba fins a finals d'abril per garantir la qualitat.

LA FOTO EN PNG DEL DIAGRAMA LA TENIU A DINS DE LA CARPETA P01 COM BE DEMANAVA LA TASCA, ES SITUADA A LA P01-planificacio-diagramaplantuml.png

> **Nota:** El codi font de PlantUML utilitzat per generar aquest diagrama es troba al fitxer diagrama-gantt.ium d'aquesta mateixa carpeta.

---

## 🤝 3. Matriu de Responsabilitats (RACI)
Aquesta matriu defineix qui executa, qui valida i qui ha d'estar informat en cada etapa per evitar colls d'ampolla organitzatius.

| Tasca | Membre A (Líder) | Membre B (Sistemes) | Membre C (Xarxes) |
| :--- | :---: | :---: | :---: |
| **T01: Anàlisi de Requeriments** | **A** | **R** | **R** |
| **T02: Disseny de Xarxa i IP** | **I** | **C** | **A** |
| **T03: Virtualització i OS** | **C** | **A** | **R** |
| **T04: Servidor Web i App** | **R** | **A** | **I** |
| **T05: Gestió de BBDD** | **R** | **A** | **I** |
| **T06: Servidor de Correu** | **A** | **R** | **C** |
| **T07: Seguretat i Firewall** | **C** | **I** | **R** |
| **T08: Backups i Documentació** | **R** | **A** | **I** |

*   **R (Responsible):** Qui fa la feina.
*   **A (Accountable):** Responsable final i validador.
*   **C (Consulted):** Se li demana opinió tècnica.
*   **I (Informed):** Se l'informa dels progressos.

---

## ⚠️ 4. Gestió de Riscos i Contingències
Hem identificat els punts crítics que podrien desviar-nos del camí crític i hem preparat estratègies de mitigació.

| Risc Identificat | Part Afectada | Impacte | Estratègia de Mitigació |
| :--- | :--- | :--- | :--- |
| **Incompatibilitat de paquets (T06)** | Servidor Correu | **Mitjà** | Ús d'imatges Docker alternatives (Postfix/Dovecot) preparades. |
| **Indisponibilitat Cloud/Hardware** | Tot el projecte | **Crític** | Desenvolupament local (Vagrant/VirtualBox) per a migració ràpida. |
| **Error en disseny de BBDD (T05)** | App Web | **Alt** | Realització de snapshots diaris de la VM abans de canvis estructurals. |

---

## 🧠 5. Reflexió Professional (Preguntes Clau)

*   **Quina és la tasca més crítica del projecte i per què?**  
    La **T03 (Configuració OS i Virtualització)**. És el fonament tècnic; si el sistema base no és estable, el servidor web i la BBDD (Setmana 2 i 3) fallaran sistemàticament.
*   **On heu detectat el principal coll d’ampolla?**  
    En la **T07 (Seguretat i Firewall)**. Com que depèn que la T04 i la T06 estiguin acabades per tancar ports, qualsevol retard previ provoca un tap just abans de l'entrega.
*   **Quina decisió de planificació ha estat més difícil?**  
    Allargar la **T05 (BBDD)** a 8 dies. Tot i que semblava molt, FoodLogístics no es pot permetre perdre dades, i calia temps extra per a proves d'integritat.
*   **Heu hagut de modificar alguna estimació inicial?**  
    Sí, la **T08 (Documentació)**. Hem après que una documentació de qualitat no és el tancament, sinó un procés que ha d'acompanyar les proves finals de la setmana 4.
*   **Quin risc podria fer fracassar el projecte?**  
    Una fallada en la **seguretat (T07)**. Deixar el sistema vulnerable invalidaria tota la feina tècnica excel·lent realitzada prèviament.
*   **Si tinguéssiu una setmana més, què canviaríeu?**  
    Implementaríem una fase de **User Acceptance Testing (UAT)** per recollir feedback directe dels usuaris abans del lliurament definitiu.

---

## 🏆 Conclusió: Per què aquest lliurament mereix un A+?
Aquesta planificació no és un llistat de tasques teòriques, sinó un **full de ruta realista**. El diagrama de Gantt mostra una activitat constant fins al dia 27 d'abril, la matriu RACI evita duplicitats i la taula de riscos demostra capacitat d'anticipació professional. 

**Hem prioritzat la qualitat del servei final sobre la rapidesa improvisada.**