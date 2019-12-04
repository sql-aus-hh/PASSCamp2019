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

  '''posh
  az group create --name RG-AzureContainerRegistry --location eastus

</details>

az acr create --resource-group RG-AzureContainerRegistry --name PASSCamp-ACR --sku Basic

az acr login --name PASSCamp-ACR

docker images

az acr list --resource-group RG-AzureContainerRegistry --query "[].{acrLoginServer:loginServer}" --output table

docker tag azure-vote-front passcampacr.azurecr.io/azure-vote-front:v1

docker images

docker push passcampacr.azurecr.io/azure-vote-front:v1

az acr repository show-tags --name PASSCamp-ACR --repository azure-vote-front --output table
