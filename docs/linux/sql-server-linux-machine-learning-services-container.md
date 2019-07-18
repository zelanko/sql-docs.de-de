---
title: Ausführen SQL Server Machine Learning Services in einem Container | Microsoft-Dokumentation
description: In diesem Tutorial wird gezeigt, wie Sie SQL Server Machine Learning Services in einem Linux-Container verwenden, der auf docker ausgeführt wird.
author: uc-msft
ms.author: umajay
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: f3d3774adf4bee07269b25c3359b031ca24eb99e
ms.sourcegitcommit: ef7834ed0f38c1712f45737018a0bfe892e894ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300426"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Ausführen SQL Server Machine Learning Services in einem Container

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Tutorial wird veranschaulicht, wie Sie einen docker-Container mit SQL Server Machine Learning Services erstellen und Machine Learning Skripts von Transact-SQL ausführen.

> [!div class="checklist"]
> * Klonen Sie das MSSQL-docker-Repository.
> * Erstellen Sie SQL Server Linux-Container Image mit Machine Learning Services.
> * Führen Sie SQL Server Linux-Container Image mit Machine Learning Services aus.
> * Ausführen von R-oder python-Skripts mithilfe von Transact-SQL-Anweisungen.
> * Beendet und entfernt den SQL Server Linux-Container. 

## <a name="prerequisites"></a>Vorraussetzungen

* Git-Befehlszeilenschnittstelle.
* Docker-Engine 1.8 und höher auf unterstütztem Linux-Betriebssystem oder Docker für Mac bzw. Windows. Weitere Informationen finden Sie unter [Install Docker (Installieren von Docker)](https://docs.docker.com/engine/installation/).
* Mindestens 2 GB Speicherplatz.
* Mindestens 2 GB RAM.
* [Systemanforderungen von SQL Server unter Linux](sql-server-linux-setup.md#system)

## <a name="clone-the-mssql-docker-repository"></a>Klonen des MSSQL-docker-Repository

1. Öffnen Sie ein Bash-Terminal unter Linux/Mac oder WSL-Terminal unter Windows.

1. Erstellen Sie ein lokales Verzeichnis, um eine Kopie des MSSQL-docker-Repository lokal zu speichern.
1. Führen Sie den Befehl git clone aus, um das MSSQL-docker-Repository zu klonen.

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Erstellen Sie SQL Server Linux-Container Image mit Machine Learning Services

1. Wechseln Sie in das Verzeichnis MSSQL-mlservices.

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Führen Sie Build.sh Script aus.

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Zum Entwickeln des docker-Images müssen Pakete installiert werden, die mehrere GB groß sind. Abhängig von der Netzwerkbandbreite kann es bis zu 20 Minuten dauern, bis das Skript abgeschlossen ist.

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Ausführen SQL Server Linux-Container Images mit Machine Learning Services

1. Legen Sie Umgebungsvariablen vor dem Ausführen des Containers fest. Legen Sie die Umgebungsvariable PATH_TO_MSSQL auf ein Host Verzeichnis fest.

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Führen Sie Run.sh Script aus.

   ```bash
   ./run.sh
   ```

   Dieser Befehl erstellt einen SQL Server Container mit Machine Learning Services mit der Developer Edition (Standard). SQL Server Port **1433** wird auf dem Host als Port **1401**verfügbar gemacht.

   > [!NOTE]
   > Der Prozess zum Ausführen von Produktions SQL Server Editionen in Containern unterscheidet sich geringfügig. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server Container Images in docker](sql-server-linux-configure-docker.md). Wenn Sie dieselben Container Namen und Ports verwenden, funktioniert der Rest dieser exemplarischen Vorgehensweise immer noch mit Produktions Containern.

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

## <a name="execute-r--python-scripts-from-transact-sql"></a>Ausführen von R/python-Skripts aus Transact-SQL

1. Stellen Sie eine Verbindung mit SQL Server im Container her, und aktivieren Sie die Konfigurationsoption externer Skript, indem Sie die folgende T-SQL-Anweisung ausführen.

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Überprüfen Sie, Machine Learning Services funktioniert, indem Sie die folgende einfache R/python-sp_execute_external_script ausführen.

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

In diesem Tutorial haben Sie Folgendes gelernt:

> [!div class="checklist"]
> * Klonen Sie das MSSQL-docker-Repository.
> * Erstellen Sie SQL Server Linux-Container Image mit Machine Learning Services.
> * Führen Sie SQL Server Linux-Container Image mit Machine Learning Services aus.
> * Ausführen von R-oder python-Skripts mithilfe von Transact-SQL-Anweisungen.
> * Beendet und entfernt den SQL Server Linux-Container.

Überprüfen Sie als nächstes andere docker-Konfigurations-und Problem behandlungsszenarien:

> [!div class="nextstepaction"]
>[Konfigurations Handbuch für SQL Server auf docker](sql-server-linux-configure-docker.md)
