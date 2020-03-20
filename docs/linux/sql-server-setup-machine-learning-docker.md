---
title: Installation in Docker
titleSuffix: SQL Server Machine Learning Services
description: Hier erfahren Sie, wie Sie SQL Server Machine Learning Services (Python und R) in Docker installieren.
author: cawrites
ms.author: chadam
ms.reviewer: davidph
manager: cgronlun
ms.date: 02/18/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 767df0ec19f0749eab78a757db5bc92eb66cab49
ms.sourcegitcommit: 39d8d2d504d0ab70bac5ae3e981657e15dfb7bee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "78964518"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-docker"></a>Installieren von SQL Server Machine Learning Services (Python und R) in Docker

In diesem Artikel wird die Installation von SQL Server Machine Learning Services in Docker erläutert. Sie können Machine Learning Services verwenden, um Python- und R-Skripts in einer Datenbank auszuführen. Mit Machine Learning Services werden keine vorgefertigten Container bereitgestellt. Sie können einen Container mithilfe einer [Beispielvorlage auf GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices) aus den SQL Server-Containern erstellen.

## <a name="prerequisites"></a>Voraussetzungen

- Git-Befehlszeilenschnittstelle.
- Docker Engine 1.8 oder höher für eine beliebige unterstützte Linux-Distribution oder Docker für Mac/Windows. Weitere Informationen finden Sie unter [Install Docker (Installieren von Docker)](https://docs.docker.com/engine/install/).
- [Systemanforderungen von SQL Server unter Linux](sql-server-linux-setup.md#system)

## <a name="clone-the-mssql-docker-repository"></a>Klonen des mssql-docker-Repositorys

1. Öffnen Sie ein Bash-Terminal unter Linux oder Mac, oder öffnen Sie ein Windows-Subsystem für ein Linux-Terminal unter Windows.

2. Erstellen Sie ein lokales Verzeichnis, um eine lokale Kopie des mssql-docker-Repositorys zu speichern.

3. Führen Sie den Befehl „git clone“ aus, um das mssql-docker-Repository zu klonen:

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-a-sql-server-linux-container-image"></a>Erstellen eines SQL Server-Linux-Containerimage

1. Wechseln Sie zum Verzeichnis „mssql-mlservices“:

2. Führen Sie im gleichen Verzeichnis den folgenden Befehl aus:

    ```bash
       docker builds -t mssql-server-mlservices
    ```

3. Führen Sie den folgenden Befehl aus:

    ```bash
       docker runs -d -e MSSQL_PID=Developer -e ACCEPT_EULA=Y -e ACCEPT_EULA_ML=Y -e SA_PASSWORD=  -v OS>:/var/opt/mssql -p 1433:1433 mssql-server-mlservices
    ```

    Fügen Sie Werte für SA_PASSWORD und den Pfad für „-v“ ein. 

4. Bestätigen Sie die Änderung, indem Sie den folgenden Befehl ausführen:

    ```bash
       docker ps -a
    ```

   > [!NOTE]
   > Zum Erstellen des Docker-Images müssen Sie Pakete installieren, die mehrere GB groß sind. Abhängig von der Netzwerkbandbreite kann es bis zu 20 Minuten dauern, bis die Skriptausführung abgeschlossen ist.

## <a name="run-the-sql-server-linux-container-image"></a>Ausführen des SQL Server-Linux-Containerimages

1. Legen Sie vor dem Ausführen des Containers Ihre Umgebungsvariablen fest. Legen Sie PATH_TO_MSSQL-Umgebungsvariable auf ein Hostverzeichnis fest:

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

2. Führen Sie das run.sh-Skript aus:

   ```bash
   ./run.sh
   ```

   Mit diesem Befehl wird ein SQL Server-Container mit Machine Learning Services mit der Developer-Edition erstellt (Standard). Der SQL Server-Port **1433** wird auf dem Host als Port **1401** bereitgestellt.

   > [!NOTE]
   > Die Vorgehensweise zum Ausführen von SQL Server-Produktionseditionen in Containern weicht hiervon minimal ab. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server-Containerimages in Docker](sql-server-linux-configure-docker.md). Bei Verwendung derselben Containernamen und Ports können Sie die restlichen Schritte dieser exemplarischen Vorgehensweise auch mit Containern für Produktionsumgebungen ausführen.

3. Führen Sie den Befehl `docker ps` aus, um Ihre Docker-Container anzuzeigen:

   ```bash
   sudo docker ps -a
   ```

4. Wenn die Spalte **STATUS** den Wert **Up** (Aktiv) enthält, wird SQL Server im Container ausgeführt und überwacht den in der Spalte **PORTS** angegebenen Port. Wenn in der Spalte **STATUS** Ihres SQL Server-Containers **Exited** (Beendet) steht, lesen Sie bitte im [Abschnitt „Problembehebung“ im Konfigurationshandbuch](sql-server-linux-configure-docker.md#troubleshooting) nach.

   ```bash
   $ sudo docker ps -a
   ```
    Ausgabe:

    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="run-in-a-container"></a>Ausführen in einem Container

[Ausführen von SQL Server-Containerimages mit Docker](quickstart-install-connect-docker.md)

## <a name="connect-to-linux-sql-server-in-the-container"></a>Herstellen einer Verbindung mit SQL Server unter Linux im Container

```sql
EXEC sp_configure  'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE
```

## <a name="next-steps"></a>Nächste Schritte

Python-Entwickler können in den folgenden Tutorials erfahren, wie Python mit SQL Server verwendet werden kann:

+ [Tutorial: Ausführen von Python in T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Praxisbeispiele für die Verwendung von Machine Learning finden Sie unter [Tutorials für Machine Learning](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).

R-Entwickler können mit einigen einfachen Beispielen loslegen und die Grundlagen der Funktionen von R unter SQL Server kennenlernen. Informationen zu den nächsten Schritten finden Sie unter den folgenden Links:

+ [Tutorial: Ausführen von R in T-SQL](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)
