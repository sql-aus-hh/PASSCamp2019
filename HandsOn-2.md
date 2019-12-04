# PASSCamp2019
## Azure Kubernetes Services
### Deployment via Portal

#### Ausgangslage für das Deployment via Portal/PowerShell
Zuvor wurde das Thema **SQL on Linux** und **SQL on Docker** behandelt, darauf aufbauend wird diese Session sich nur mit dem Deployment und Handling von Containern mittles Kubernetes bzw Kubernetes on Azure befassen!

Um damit zu starten, setze ich voraus, dass man eine aktive Azure Subscription besitzt und in dieser über die Berechtigung zum Deployen von Services verfügt!

#### Wir starten also auf der virtuellen Maschine
- Prüfen ob Visual Studio Code installiert ist, ggfs nachinstallieren (choco install vscode) - es geht auch die normale PowerShell ISE
- Prüfen ob Docker Desktop installiert ist, ggfs nachinstallieren (choco install docker-desktop --pre )
- die Visual Studio Code Extension für Docker installieren (choco install vscode-docker)
- die Visual Studio Code Extension für PowerShell installieren (choco install vscode-powershell)
- die Visual Studio Code Extension für Kubernetes installieren (choco install vscode-kubernetes-tools)

Auf eurer virtuellen Maschine Visual Studio Code (oder eine Powershell ISE) die Azure CLI installieren, damit ihr die nächste Aufgabe bearbeiten könnt.

Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'

Bitte eigenständig die Kommandozeile zusammenstellen (nicht cheaten ;-) )
#### Erstellen einer neuen Ressourcen-Gruppe 'RG-AzureContainerRegistry'
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
  az group create --name RG-AzureContainerRegistry --location eastus
```
</p>
</details>

#### Erstellen einer neuen Container Registry in der Ressourcen-Gruppe 'RG-AzureContainerRegistry'
<details>
  <summary>Hilfe</summary>
  <p>

    ```PowerShell
        az acr create --resource-group RG-AzureContainerRegistry --name PASSCamp-ACR --sku Basic
```
    </p>
</details>

#### Einloggen in die neue Container-Registry
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
        az acr login --name PASSCamp-ACR
```
    </p>
</details>

#### Lasst euch die vorhandenen lokalen Docker-Images anzeigen
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
    docker images
```
    </p>
</details>

#### Ermittelt den Login-Server eurer Contaier-Registry
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
    az acr list --resource-group RG-AzureContainerRegistry --query "[].{acrLoginServer:loginServer}" --output table
```
    </p>
</details>

#### Tagged euren SQL-Server-Container (aus dem Handson mit Frank&Ben) mit der Version 1 (V1)
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
    docker tag azure-vote-front passcampacr.azurecr.io/azure-vote-front:v1
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
    docker push passcampacr.azurecr.io/azure-vote-front:v1
```
    </p>
</details>

#### Lasst euch den Erfolg eurer Push-Aktion mit einer Abfrage eurer Registry anzeigen
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
    az acr repository show-tags --name PASSCamp-ACR --repository azure-vote-front --output table
```
    </p>
</details>
