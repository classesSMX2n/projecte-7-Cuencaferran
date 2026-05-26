---

# 📑 Memòria Tècnica de la Proposta: FoodLogístic S.A.

## 📝 1. Introducció i Objectius
Aquest document constitueix la memòria tècnica detallada de la solució d'infraestructura i serveis proposada per a **FoodLogístic S.A.**. L'objectiu és proporcionar una visió integral de la solució, justificant les decisions tecnològiques i demostrant la viabilitat del projecte abans de la seva implementació.

La proposta se centra en quatre pilars fonamentals:
1.  **Robustesa:** Infraestructura de xarxa i servidors d'alta disponibilitat.
2.  **Seguretat:** Protecció de dades i control d'accessos rigorós.
3.  **Eficiència:** Optimització de recursos mitjançant la virtualització.
4.  **Escalabilitat:** Disseny preparat per al creixement futur de l'empresa.

---

## 🏗️ 2. Arquitectura de la Solució

### 🌐 2.1 Topologia de Xarxa
S'ha dissenyat una topologia segmentada per garantir la seguretat i el rendiment. El disseny inclou:
*   **VLANs segmentades:** Separació de trànsit de gestió, servidors i clients.
*   **Adreçament IP:** Esquema jeràrquic i documentat per evitar col·lisions.
*   **DMZ (Zona Desmilitaritzada):** Per als serveis amb accés extern (Web, Correu).

### 🖥️ 2.2 Infraestructura de Servidors
La solució es basa en un entorn virtualitzat que permet una gestió centralitzada:
*   **Hipervisor:** (Ex: Proxmox / VMware / VirtualBox) per a la gestió de màquines virtuals (VM).
*   **Sistemes Operatius:** Ús de distribucions Linux (Debian/Ubuntu Server) per a la seva estabilitat i seguretat.
*   **Contenidors:** Implementació de Docker per a serveis lleugers i fàcilment desplegables.

---

## 🛠️ 3. Serveis Implementats
La proposta inclou el desplegament i configuració dels següents serveis crítics:

| Servei | Tecnologia Proposada | Finalitat |
| :--- | :--- | :--- |
| **Servidor Web** | Nginx / Apache | Allotjament de l'aplicació logística. |
| **Base de Dades** | MariaDB / PostgreSQL | Gestió d'inventari i dades de clients. |
| **Correu Electrònic** | Postfix / Dovecot | Comunicació interna i externa segura. |
| **Monitoratge** | Zabbix / Prometheus | Vigilància de l'estat dels serveis 24/7. |
| **Seguretat** | Iptables / UFW / Fail2Ban | Protecció activa contra accessos no autoritzats. |

---

## 🔒 4. Seguretat i Protecció de Dades
Per a FoodLogístic S.A., la integritat de la informació és prioritària:
*   **Firewall:** Configuració de regles estrictes de trànsit d'entrada i sortida.
*   **Backups:** Estratègia de còpies de seguretat periòdiques i automatitzades (Regla 3-2-1).
*   **Certificats SSL/TLS:** Encriptació de totes les comunicacions web i de correu.

---

## 📅 5. Viabilitat i Planificació
La implementació de la memòria tècnica està estretament lligada a la planificació temporal detallada en el [Diagrama de Gantt (T09)](../Planificacio/README.md).

*   **Fase d'Anàlisi:** Validació de requeriments amb el client.
*   **Fase de Desplegament:** Instal·lació i configuració base.
*   **Fase de Testeig:** Proves d'estrès i validació de seguretat.
*   **Fase de Lliurament:** Formació i traspàs de documentació.

---

## 📈 6. Conclusió
Aquesta memòria tècnica garanteix que la solució proposada no només respon a les necessitats actuals de **FoodLogístic S.A.**, sinó que ofereix un marc tecnològic sòlid, segur i escalable. La combinació d'eines professionals i una planificació rigorosa asseguren l'èxit de la implementació intermodular.

---

## 📂 Annexos i Evidències
Dins d'aquest directori o enllaçat, es poden trobar:
*   [ ] Esquema de la Topologia (Imatges/PDF)
*   [ ] Taula detallada d'adreçament IP
*   [ ] Manuals de configuració bàsica
*   [ ] Resultats de les proves de concepte (PoC)

---
