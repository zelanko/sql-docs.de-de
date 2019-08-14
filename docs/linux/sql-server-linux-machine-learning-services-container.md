---
title: Ausführen der SQL Server-Machine Learning Services in einem Container | Microsoft-Dokumentation
description: In diesem Tutorial erfahren Sie, wie Sie SQL Server-Machine Learning Services in einem Linux-Container verwenden, der auf Docker ausgeführt wird.
author: uc-msft
ms.author: umajay
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: f3d3774adf4bee07269b25c3359b031ca24eb99e
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68300426"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Ausführen der SQL Server-Machine Learning Services in einem Container

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Tutorial wird veranschaulicht, wie Sie einen Docker-Container mit SQL Server-Machine Learning Services erstellen und Machine Learning-Skripts von Transact-SQL ausführen.

> [!div class="checklist"]
> * Klonen Sie das mssql-docker-Repository.
> * Erstellen Sie das SQL Server-Linux-Containerimage mit Machine Learning Services.
> * Führen Sie das SQL Server-Linux-Containerimage mit Machine Learning Services aus.
> * Führen Sie R- oder Python-Skripts mithilfe von Transact-SQL-Anweisungen aus.
> * Beenden und entfernen Sie den SQL Server-Linux-Container. 

## <a name="prerequisites"></a>Voraussetzungen

* Git-Befehlszeilenschnittstelle.
* Docker-Engine 1.8 und höher auf unterstütztem Linux-Betriebssystem oder Docker für Mac bzw. Windows. Weitere Informationen finden Sie unter [Install Docker (Installieren von Docker)](https://docs.docker.com/engine/installation/).
* Mindestens 2GB freier Speicherplatz auf dem Datenträger.
* Mindestens 2GB RAM.
* [Systemanforderungen von SQL Server unter Linux](sql-server-linux-setup.md#system)

## <a name="clone-the-mssql-docker-repository"></a>Klonen des mssql-docker-Repositorys

1. Öffnen Sie ein Bash-Terminal auf dem Linux-/Mac- oder WSL-Terminal unter Windows.

1. Erstellen Sie ein lokales Verzeichnis, um eine Kopie des mssql-docker-Repositorys lokal zu speichern.
1. Führen Sie den Befehl „git clone“ aus, um das mssql-docker-Repository zu klonen.

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Erstellen des SQL Server-Linux-Containerimages mit Machine Learning Services

1. Wechseln Sie in das Verzeichnis „mssql-mlservices“.

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Führen Sie das build.sh-Skript aus.

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Das Erstellen des Docker-Images setzt die Installation von Paketen voraus, die mehrere GB groß sind. Abhängig von der Netzwerkbandbreite kann es bis zu 20 Minuten dauern, bis das Skript abgeschlossen ist.

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Ausführen des SQL Server-Linux-Containerimages mit Machine Learning Services

1. Legen Sie vor dem Ausführen des Containers Umgebungsvariablen fest. Legen Sie für die Umgebungsvariable PATH_TO_MSSQL ein Hostverzeichnis fest.

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Führen Sie das run.sh-Skript aus.

   ```bash
   ./run.sh
   ```

   Mit diesem Befehl wird ein SQL Server-Container mit Machine Learning Services mit der Developer-Edition erstellt (Standard). Der SQL Server-Port **1433** wird auf dem Host als Port **1401** bereitgestellt.

   > [!NOTE]
   > Die Vorgehensweise zum Ausführen von SQL Server-Produktionseditionen in Containern weicht hiervon minimal ab. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server-Containerimages in Docker](sql-server-linux-configure-docker.md). Bei Verwendung derselben Containernamen und Ports können Sie die restlichen Schritte dieser exemplarischen Vorgehensweise auch mit Containern für Produktionsumgebungen ausführen.

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

## <a name="execute-r--python-scripts-from-transact-sql"></a>Ausführen von R-/Python-Skripts von Transact-SQL

1. Stellen Sie eine Verbindung mit SQL Server im Container her, und aktivieren Sie die Konfigurationsoption für externe Skripts, indem Sie die folgende T-SQL-Anweisung ausführen.

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Überprüfen Sie, ob Machine Learning Services funktioniert, indem Sie das folgende einfache R-/Python-Skript „sp_execute_external_script“ ausführen.

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

In diesem Tutorial führen Sie die folgenden Schritte aus:

> [!div class="checklist"]
> * Klonen Sie das mssql-docker-Repository.
> * Erstellen Sie das SQL Server-Linux-Containerimage mit Machine Learning Services.
> * Führen Sie das SQL Server-Linux-Containerimage mit Machine Learning Services aus.
> * Führen Sie R- oder Python-Skripts mithilfe von Transact-SQL-Anweisungen aus.
> * Beenden und entfernen Sie den SQL Server-Linux-Container.

Erfahren Sie nun mehr zu weiteren Szenarios für Docker-Konfigurationen und -Problembehandlung:

> [!div class="nextstepaction"]
>[Konfigurieren von SQL Server-Containerimages in Docker](sql-server-linux-configure-docker.md)
