# PASSCamp2019
## Azure Kubernetes Services
### Deployment via Portal

#### Ausgangslage für das Deployment via Portal/PowerShell
Zuvor wurde das Thema **SQL on Linux** und **SQL on Docker** behandelt, darauf aufbauend wird diese Session sich nur mit dem Deployment und Handling von Containern mittels Kubernetes bzw Kubernetes on Azure befassen!

Um damit zu starten, setze ich voraus, dass man eine aktive Azure Subscription besitzt und in dieser über die Berechtigung zum Deployen von Services verfügt!

#### Wir starten also im Azure Portal
Suchen und Auswahl der entsprechenden Services
- Eingabe des Suchbegriffes "**Kubernetes Service**"
<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-01-e1574693334808.png" alt="Azure Portal" title="Startseite im Azure Portal" />

Mit einem Klick auf "**Create**" wählt man den Service aus und man gelangt auf die erste Seite des Deployments bzw der Konfiguration des zu deployenden Azure Kubernetes Services

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-02-e1574693363601.png" alt="Azure Portal" title="Suchen des Azure Services - Azure Kubernetes Services" />

Hier starten wir mit der Auswahl der zu nutzenden Subscription, damit eine Zuordnung der Kosten zur jeweiligen "Kreditkarte" erfolgen kann.
Danach geht es weiter mit der Auswahl einer vorhandenen Ressourcengruppe bzw der Erstellung einer neuen Ressourcengruppe 
  - Klick auf "Neues Element erstellen" -> es öffnet sich ein neues Popup
  - Namen der neuen Ressourcengruppe eingeben
  - mit "**OK**" bestätigen
  
  - für dieses HandsOn reicht die kleinste verfügbare Knoten-Größe für die Worker-Knoten
  - ebenso die Anzahl der Worker-Knoten kann reduziert werden, um Kosten zu sparen

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-04-e1574693396126.png" alt="Azure Portal" title="Erstellen des Azure Kubernetes Services" />
  
Unten geht es weiter mit dem Button "**Weiter: Skalieren**".
 
Auf der neuen Seite kann man das Skalierungsverhalten des Kubernetes-Clusters konfigurieren... Ob nun über das "Serverless" Skalieren mittels "Azure Container Instances" oder ob man das ganze Cluster "variabel" aufstellen möchte und die Rahmenbedingungen definieren möchte, damit Azure bei Laständerungen automatisch skaliert.

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-05-e1574693418471.png" alt="Azure Portal" title="Azure Kubernetes Services - Vergabe der weiteren Namen/Region/Clustergröße/KubernetesVersion" />

Für diese HandsOn-Session können die Angaben unverändert bleiben, beides wird hier erst einmal nicht benötigt!

Unten geht es weiter mit dem Button "**Weiter: Authentifizierung**".

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-06-e1574693446289.png" alt="Azure Portal" title="Azure Kubernetes Services - Aktivieren der Features für virtuelleKnoten oder Skalierungsgruppen" />

Auf der neuen Seite kann man das Verhalten des Azure Kubernetes Cluster bezogen auf zu verwendende User konfiguriert. Einmal der ServiceUser, der das Cluster aus Infrastruktursicht über Kubernetes skalieren/konfigurieren kann. Zum anderen, wie man den Zugriff auf  das Cluster gestalten möchte, hier nutzt man überlicherweise den Rollenbasierten Ansatz um den Zugriff und die Rechte der einzelnen User zu beschränken. => **R**ole**B**ase**A**ccess**C**ontrol (RBAC) aktivieren

Für diese HandsOn-Session können die Angaben unverändert bleiben, beides wird hier erst einmal nicht benötigt!

Unten geht es weiter mit dem Button "**Weiter: Netzwerk**".

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-07-e1574693471895.png" alt="Azure Portal" title="Azure Kubernetes Services - Aktivieren von RoleBasedAccessControl und Definition des ServicePrincipals" />

Unten geht es weiter mit dem Button "**Weiter: Überwachung**".

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-08-e1574696725689.png" alt="Azure Portal" title="Azure Kubernetes Services - Konfiguration und Aktivierung der unterschiedlichen Netzwerk-Bereiche sowie Loadbalancing und Endpunkte" />

Unten geht es weiter mit dem Button "**Weiter: Tags**".

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-09-e1574696838673.png" alt="Azure Portal" title="Azure Kubernetes Services - Konfiguration und Aktivierung der unterschiedlichen Netzwerk-Bereiche sowie Loadbalancing und Endpunkte" />

Unten geht es weiter mit dem Button "**Weiter: Überprüfen + Erstellen**".

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-10-e1574696945895.png" alt="Azure Portal" title="Azure Kubernetes Services - Konfiguration und Aktivierung der unterschiedlichen Netzwerk-Bereiche sowie Loadbalancing und Endpunkte" />

Jetzt heißt es warten bis das Deployment abgeschlossen ist...

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-11-e1574696982938.png" alt="Azure Portal" title="Azure Kubernetes Services - Konfiguration und Aktivierung der unterschiedlichen Netzwerk-Bereiche sowie Loadbalancing und Endpunkte" />

<img src="https://www.sql-aus-hamburg.de/wp-content/uploads/2019/11/22-11-2019-13-e1574697052974.png" alt="Azure Portal" title="Azure Kubernetes Services - Konfiguration und Aktivierung der unterschiedlichen Netzwerk-Bereiche sowie Loadbalancing und Endpunkte" />

[weiter mit HandsOn 2](https://github.com/sql-aus-hh/PASSCamp2019/blob/master/HandsOn-2.md)
