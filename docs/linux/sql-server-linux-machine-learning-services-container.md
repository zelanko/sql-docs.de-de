---
title: Führen Sie SQL Server Machine Learning-Dienste in einem Container | Microsoft-Dokumentation
description: In diesem Tutorial erfahren Sie, wie Sie mit der SQL Server-Machine-Learning-Services in einem Linux-Container ausführen unter Docker.
author: uc-msft
ms.author: umajay
manager: craigg
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 3e654e29d6c49d3bf68cdfe7c4e3b479b47a973c
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67840469"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Führen Sie SQL Server Machine Learning-Dienste in einem Container

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieses Tutorial veranschaulicht das Erstellen von Docker-Container mit SQL Server-Machine Learning-Dienste und Ausführen von Machine Learning-Skripts über Transact-SQL.

> [!div class="checklist"]
> * Der Mssql-Docker-Repository zu klonen.
> * Erstellen Sie SQL Server Linux-containerimage mit Machine Learning-Dienste.
> * Führen Sie SQL Server Linux-Container-Abbild mit Machine Learning-Dienste an.
> * Führen Sie R- oder Python-Skripts, die mithilfe von Transact-SQL-Anweisungen.
> * Beenden Sie und entfernen Sie den SQL Server Linux-Container. 

## <a name="prerequisites"></a>Vorraussetzungen

* Git-Befehlszeilenschnittstelle.
* Docker-Engine 1.8 und höher auf unterstütztem Linux-Betriebssystem oder Docker für Mac bzw. Windows. Weitere Informationen finden Sie unter [Install Docker (Installieren von Docker)](https://docs.docker.com/engine/installation/).
* Mindestens 2 GB Speicherplatz auf dem Datenträger.
* Mindestens 2 GB RAM.
* [Systemanforderungen von SQL Server unter Linux](sql-server-linux-setup.md#system)

## <a name="clone-the-mssql-docker-repository"></a>Klonen Sie das Mssql-Docker-repository

1. Öffnen Sie ein Bash-Terminal auf Linux/Mac oder WSL Terminalserver unter Windows.

1. Erstellen Sie ein lokales Verzeichnis aus, um eine Kopie der Mssql-Docker-Repository lokal zu speichern.
1. Führen Sie den Git-Klon-Befehl, um das Mssql-Docker-Repository klonen.

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Erstellen Sie SQL Server Linux-containerimage in Machine Learning Services

1. Wechseln Sie in das Verzeichnis für die Mssql-Mlservices.

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Ausführen von Skript "Build.sh".

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Erstellen das Docker-Image erfordert die Installation von Paketen, die mehrere GB groß sind. Das Skript kann je nach Netzwerkbandbreite bis zu 20 Minuten dauern.

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Führen Sie SQL Server Linux-containerimage in Machine Learning Services

1. Festlegen von Umgebungsvariablen vor dem Ausführen des Containers. Legen Sie PATH_TO_MSSQL-Umgebungsvariable, auf einem Hostverzeichnis.

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Führen Sie run.sh Skript.

   ```bash
   ./run.sh
   ```

   Dieser Befehl erstellt einen SQL Server-Container mit Machine Learning-Dienste, mit der Developer Edition (Standard). SQL Server-Port **1433** verfügbar gemacht wird, werden auf dem Host als Port **1401**.

   > [!NOTE]
   > Der Prozess zum Ausführen von SQL Server-produktionseditionen in Containern ist etwas anders. Weitere Informationen finden Sie unter [Run production container images (Ausführen von Containerimages für Produktionsumgebungen)](sql-server-linux-configure-docker.md#production). Wenn Sie die gleichen Containernamen und die Ports verwenden, funktioniert die restlichen in dieser exemplarischen Vorgehensweise weiterhin mit Produktions-Containern.

1. Verwenden Sie den Befehl `docker ps`, um Ihre Docker-Container anzeigen zu lassen.

   ```bash
   sudo docker ps -a
   ```

1. Wenn in der Spalte **STATUS** **Up** (Aktiv) eingetragen ist, wird SQL Server im Container ausgeführt und überwacht den Port, der in der Spalte **PORTS** angegeben ist. Wenn in der Spalte **STATUS** Ihres SQL Server-Containers **Exited** (Beendet) steht, lesen Sie bitte im [Abschnitt „Problembehebung“ im Konfigurationshandbuch](sql-server-linux-configure-docker.md#troubleshooting) nach.

   ```bash
   $ sudo docker ps -a
   ```

    Ausgabe: 
    
    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="change-the-sa-password"></a>Ändern des Systemadministratorkennworts

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="execute-r--python-scripts-from-transact-sql"></a>Ausführen von R / Python-Skripts über Transact-SQL

1. Verbinden mit SQL Server in den Container aus, und aktivieren Sie die externen Skript-Konfigurationsoption, indem Sie die folgende T-SQL-Anweisung ausführen.

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Stellen Sie sicher, dass Machine Learning-Dienste ausgeführt wird, indem Sie die folgenden einfachen Sp_execute_external_script für R/Python ausführen.

    ```sql
    execute sp_execute_external_script 
    @language = N'R',
    @script = N'
    print("Hello World!")
    print(R.version)
    print(Revo.version)
    OutputDataSet <- InputDataSet', 
    @input_data_1 = N'select 1'
    with result sets((i int));
    go
    ```

    ```sql
    execute sp_execute_external_script 
    @language = N'Python',
    @script = N'
    import sys
    print(sys.version)
    print("Hello World!")
    OutputDataSet = InputDataSet',
    @input_data_1 = N'select 1'
    with result sets((i int));
    go 
    ```

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie folgende Schritte ausführen:

> [!div class="checklist"]
> * Der Mssql-Docker-Repository zu klonen.
> * Erstellen Sie SQL Server Linux-containerimage mit Machine Learning-Dienste.
> * Führen Sie SQL Server Linux-Container-Abbild mit Machine Learning-Dienste an.
> * Führen Sie R- oder Python-Skripts, die mithilfe von Transact-SQL-Anweisungen.
> * Beenden Sie und entfernen Sie den SQL Server Linux-Container.

Überprüfen Sie dann die anderen Docker-Konfiguration und Problembehandlung von Szenarien:

> [!div class="nextstepaction"]
>[Konfigurationshandbuch für SQL Server unter Docker](sql-server-linux-configure-docker.md)
