# PASSCamp2019
## Azure Kubernetes Services
### Push SQL Server Container to ACR and create your first SQL Server running high-available on AKS

#### Ausgangslage für das Deployment via Portal/PowerShell
Zuvor wurde das Thema **SQL on Linux** und **SQL on Docker** behandelt, darauf aufbauend wird diese Session sich nur mit dem Deployment und Handling von Containern mittles Kubernetes bzw Kubernetes on Azure befassen!

Um damit zu starten, setze ich voraus, dass man eine aktive Azure Subscription besitzt und in dieser über die Berechtigung zum Deployen von Services verfügt!

Und die Handson-Session 1&2 wurden erfolgreich absolviert

#### Wir starten also auf der virtuellen Maschine


Bitte eigenständig die Kommandozeile zusammenstellen (nicht cheaten ;-) )
#### Tagged euren SQL-Server-Container (aus dem Handson mit Frank&Ben) mit der Version 1 (V1)
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
    docker tag %ImageName% passcampacr.azurecr.io/%ImageName%:v1
```
    </p>
</details>

#### Lasst euch noch einmal - zur Überprüfung - die vorhandenen lokalen Docker-Images anzeigen
#### Hat sich was geändert?
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
    docker images
```
</p>
</details>

#### Pushed eure Version 1 des SQL Server Container in die Registry
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
    docker push %LogonServer%/%ImageName%:v1
```
    </p>
</details>

#### Lasst euch den Erfolg eurer Push-Aktion mit einer Abfrage eurer Registry anzeigen
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
    az acr repository show-tags --name PASSCamp-ACR --repository %ImageName% --output table
```
    </p>
</details>
