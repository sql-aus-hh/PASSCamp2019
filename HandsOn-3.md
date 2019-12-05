# PASSCamp2019
## Azure Kubernetes Services
### Push SQL Server Container to ACR and create your first SQL Server running high-available on AKS

#### Ausgangslage für das Deployment via Portal/PowerShell
Zuvor wurde das Thema **SQL on Linux** und **SQL on Docker** behandelt, darauf aufbauend wird diese Session sich nur mit dem Deployment und Handling von Containern mittles Kubernetes bzw Kubernetes on Azure befassen!

Um damit zu starten, setze ich voraus, dass man eine aktive Azure Subscription besitzt und in dieser über die Berechtigung zum Deployen von Services verfügt!

Und die Handson-Session 1&2 wurden erfolgreich absolviert

#### Wir starten also auf der virtuellen Maschine


Bitte eigenständig die Kommandozeile zusammenstellen (nicht cheaten ;-) )
#### Tagged euren SQL-Server-Container (aus dem Handson mit Frank&Ben) mit der Version 1 (V1)<br>Wer diese Aufgabe nicht fertiggestellt hat, kann auch einfach einen lokalen Docker-Container erstellen und diesen mit Version 1 (V1) taggen
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
  docker tag %ImageName% passcampacr.azurecr.io/%ImageName%:v1
```

Alternativ : Erstellen eines neuen Docker-Compose-Files 

    version: '3'
  
    services:
        sqlserver1:
            image: mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
            ports:  
              - "1433:1433"
            environment:
              SA_PASSWORD: "Testing1122"
              ACCEPT_EULA: "Y"
              MSSQL_DATA_DIR: "/var/opt/sqlserver/data"
              MSSQL_LOG_DIR: "/var/opt/sqlserver/log"
              MSSQL_BACKUP_DIR: "/var/opt/sqlserver/backup"
            volumes: 
              - sqlsystem:/var/opt/mssql/
              - sqldata:/var/opt/sqlserver/data
              - sqllog:/var/opt/sqlserver/log
    volumes:
      sqlsystem:
      sqldata:
      sqllog:
```
  docker-compose up
  docker tag %ImageName% passcampacr.azurecr.io/%ImageName%:v1
```

</p>
</details>

#### Lasst euch noch einmal - zur Überprüfung - die vorhandenen lokalen Docker-Images anzeigen<br>Hat sich was geändert?
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

#### euren neuen Container in euer Kubernetes Cluster deployen
#### Den Filenamen ggfs anpassen, je nach dem was ihr oben (Container von Frank&Ben oder selbsterstellter Container) verwendet habt.
<details>
  <summary>Hilfe</summary>
  <p>

  ```PowerShell
  kubectl apply -f .\sqlserver-deployment.yaml
```

  </p>
</details>
