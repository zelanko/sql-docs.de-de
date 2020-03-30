---
title: Verwenden von RevoScaleR-Computekontexten
description: 'Tutorial 4 zu RevoScaleR: Definieren eines Computekontexts mithilfe der R-Programmiersprache in SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c90c935f85584f8886ae112d5cfc03759c0a129a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "74947217"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>Definieren und Verwenden von Computekontexten (SQL Server und RevoScaleR-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Bei diesem Tutorial handelt es sich um das 4. Tutorial von [Lernprogramm: Verwenden von RevoScaleR-Funktionen für R mit SQL Server-Daten](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md). Hier erfahren Sie, wie Sie [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server verwenden.

Im vorherigen Tutorial haben Sie **RevoScaleR**-Funktionen zum Untersuchen von Datenobjekten verwendet. In diesem Tutorial wird die [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)-Funktion erläutert, mit der Sie einen Computekontext für einen Remote-SQL-Server definieren können. Mit einem Remotecomputekontext können Sie die R-Ausführung von einer lokalen Sitzung zu einer Remotesitzung auf dem Server verschieben. 

> [!div class="checklist"]
> * Grundlegendes zu SQL Server-Remotecomputekontext
> * Aktivieren der Ablaufverfolgung für ein Computecontextobjekt

**RevoScaleR** unterstützt mehrere Computekontexte: Hadoop, Spark in HDFS und datenbankinterne SQL Server. Für SQL Server wird die **RxInSqlServer**-Funktion für Serververbindungen und das Übergeben von Objekten zwischen dem lokalen Computer und dem Remoteausführungskontext verwendet.

## <a name="create-and-set-a-compute-context"></a>Erstellen und Festlegen eines Computekontexts

Die **RxInSqlServer**-Funktion, die den SQL Server-Computekontext erstellt, verwendet die folgenden Informationen:

+ Verbindungszeichenfolge für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz
+ Spezifikation zur Verarbeitung der Ausgabe
+ Optionale Spezifikation eines freigegebenen Datenverzeichnisses
+ Optionale Argumente, die die Ablaufverfolgung oder das Angeben der Ablaufverfolgungsebene ermöglichen

In diesem Abschnitt werden Sie durch die einzelnen Teile geführt.

1. Geben Sie die Verbindungszeichenfolge für die Instanz an, in der die Berechnungen durchgeführt werden sollen. Sie können die zuvor erstellte Verbindungszeichenfolge erneut verwenden.

    **Verwenden einer SQL-Anmeldung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Verwenden der Windows-Authentifizierung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. Geben Sie an, wie die Ausgabe behandelt werden soll. Mit dem folgenden Skript wird die lokale R-Sitzung angewiesen, auf R-Auftragsergebnisse auf dem Server zu warten, bevor der nächste Vorgang verarbeitet wird. Außerdem wird so die Ausgabe von Remoteberechnungen in der lokalen Sitzung unterdrückt.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    Das Argument *wait* für **RxInSqlServer** unterstützt diese Optionen:
  
    -   **TRUE**. Der Auftrag wird als „blockiert“ konfiguriert und wird nicht zurückgegeben, bis er abgeschlossen wurde oder ein Fehler aufgetreten ist.  Weitere Informationen finden Sie unter [Verteiltes und paralleles Computing in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Aufträge werden als „nicht blockierend“ konfiguriert und sofort zurückgegeben, sodass Sie weiterhin anderen R-Code ausführen können. Jedoch auch im nicht blockierenden Modus muss die Clientverbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufrechterhalten werden, während der Auftrag ausgeführt wird.

3. Optional können Sie den Speicherort eines lokalen Verzeichnisses angeben, das von der lokalen R-Sitzung und dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Remotecomputer und dessen Konten für den Gebrauch freigegeben wurde.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   Wenn Sie manuell ein bestimmtes Verzeichnis für die Freigabe erstellen möchten, können Sie eine Zeile wie die folgende hinzufügen:

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Übergeben Sie Argumente an den **RxInSqlServer**-Konstruktor, um das *Computecontextobjekt* zu erstellen.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    Die Syntax für **RxInSqlServer** ist fast identisch mit der Syntax der **RxSqlServerData**-Funktion, die Sie zuvor zum Definieren der Datenquelle verwendet haben. Es gibt jedoch auch wichtige Unterschiede.
      
    - Das Datenquellenobjekt (mithilfe der Funktion [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)definiert) gibt an, wo die Daten gespeichert werden.
    
    - Im Gegensatz dazu gibt der mit der [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)-Funktion definierte Computekontext an, wo Aggregationen und andere Berechnungen durchgeführt werden.
    
    Das Definieren eines Computekontexts wirkt sich nicht auf andere generische R-Berechnungen aus, die Sie auf Ihrer Arbeitsstation ausführen können, und ändert nicht die Quelle der Daten. Sie können z.B. eine lokale Textdatei als Datenquelle definieren, aber SQL Server als Computekontext verwenden und alle Lesevorgänge und Zusammenfassungen der Daten auf dem SQL Server-Computer ausführen.

5. Aktivieren Sie den Remotecomputekontext.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. Geben Sie Informationen über den Computekontext einschließlich der zugehörigen Eigenschaften zurück.

    ```R
    rxGetComputeContext()
    ```

7. Aktivieren Sie wieder den Computekontext des lokalen Computers, indem Sie das Schlüsselwort „local“ (lokal) angeben. Die Verwendung des Remotecomputekontexts wird im nächsten Tutorial erläutert.

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> Sie erhalten eine Liste der Schlüsselwörter, die von dieser Funktion unterstützt werden, indem Sie `help("rxSetComputeContext")` in der Befehlszeile von R eingeben.

## <a name="enable-tracing"></a>Aktivieren der Ablaufverfolgung

Es kann vorkommen, dass Vorgänge, die in Ihrem lokalen Kontext funktionieren, jedoch Probleme bei der Ausführung in einem Remotecomputekontext haben. Wenn Sie Probleme analysieren oder die Leistung überwachen möchten, können Sie die Ablaufverfolgung im Computekontext aktivieren, um die Problembehandlung der Laufzeit zu unterstützen.

1. Erstellen Sie einen neuen Computekontext, der die gleiche Verbindungszeichenfolge verwendet, aber fügen Sie dem **RxInSqlServer**-Konstruktor die Argumente *traceEnabled* und *traceLevel* hinzu.

    ```R
    sqlComputeTrace <- RxInSqlServer(
        connectionString = sqlConnString,
        #shareDir = sqlShareDir,
        wait = sqlWait,
        consoleOutput = sqlConsoleOutput,
        traceEnabled = TRUE,
        traceLevel = 7)
    ```
  
   In diesem Beispiel ist *traceLevel* auf 7 gesetzt, d.h. „alle Ablaufverfolgungsinformationen anzeigen“.

2. Verwenden Sie die [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext)-Funktion, um den für die Ablaufverfolgung aktivierten Computekontext anhand des Namens anzugeben.

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>Nächste Schritte

Informieren Sie sich, wie Sie Computekontexte wechseln, um R-Code auf dem Server oder lokal auszuführen.

> [!div class="nextstepaction"]
> [Berechnen von Zusammenfassungsstatistiken in lokalen und Remotecomputekontexten](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)