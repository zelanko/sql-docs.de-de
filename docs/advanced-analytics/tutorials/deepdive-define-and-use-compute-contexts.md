---
title: Definieren Sie und verwenden Sie der RevoScaleR-computekontexten – SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Definieren eines computekontexts Verwendung der Sprache R auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c0ae593264abad52873cfc152da721b6c0867109
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645081"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>Definieren und Verwenden von berechneten Kontexten (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In der vorherigen Lektion haben Sie verwendet **RevoScaleR** Funktionen, um Datenobjekte zu überprüfen. Diese Lektion führt die [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) -Funktion, die Sie einen computekontext für einen Remotecomputer mit SQL Server definieren kann. Mit einem remotecomputekontext können Sie R-Ausführung über eine lokale Sitzung an eine Remotesitzung auf dem Server verlagern. 

> [!div class="checklist"]
> * Erfahren Sie, dass die Elemente von einem Remotecomputer mit SQL Server-rechenkontext
> * Aktivieren der Ablaufverfolgung für einen computekontext-Objekt

**RevoScaleR** unterstützt mehrere computekontexte: Hadoop, Spark auf HDFS und SQLServer in der Datenbank. Für SQL Server die **RxInSqlServer** Funktion wird verwendet, für die Server-Verbindungen und übergeben von Objekten zwischen dem lokalen Computer und die remote-Ausführungskontext.

## <a name="create-and-set-a-compute-context"></a>Erstellen und Festlegen eines computekontexts

Die **RxInSqlServer** -Funktion, die den SQL Server-computekontext erstellt, verwendet die folgenden Informationen:

+ Verbindungszeichenfolge für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz
+ Spezifikation der, wie die Ausgabe behandelt werden sollen
+ Optionale Spezifikation von einem freigegebenen Verzeichnis
+ Optionale Argumente, die die Ablaufverfolgung aktivieren, oder geben Sie die Ablaufverfolgung an

Dieser Abschnitt führt Sie durch die einzelnen Bereiche.

1. Geben Sie die Verbindungszeichenfolge für die Instanz, in dem Berechnungen ausgeführt werden. Sie können die Verbindungszeichenfolge erneut verwenden, die Sie zuvor erstellt haben.

    **Verwenden einer SQL-Anmeldung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Verwenden der Windows-Authentifizierung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. Geben Sie an, wie die Ausgabe behandelt werden soll. Das folgende Skript, weist die lokale R-Sitzung auf dem Server für R-Auftragsergebnisse warten, bevor der nächste Vorgang verarbeitet. Sie unterdrückt auch die Ausgabe aus remoteberechnungen in die lokale Sitzung angezeigt werden.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    Das Argument *wait* für **RxInSqlServer** unterstützt diese Optionen:
  
    -   **TRUE**. Der Auftrag als blockiert konfiguriert ist und nicht zurückgegeben, bis er abgeschlossen wurde oder ein Fehler aufgetreten.  Weitere Informationen finden Sie unter [verteilt und parallel computing in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Aufträge werden als nicht blockierende konfiguriert und sofort zurück, sodass Sie weiterhin anderen R-Code ausführen. Jedoch auch im nicht blockierenden Modus muss die Clientverbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufrechterhalten werden, während der Auftrag ausgeführt wird.

3. Geben Sie optional den Speicherort eines lokalen Verzeichnisses für die gemeinsame Nutzung von der lokalen R-Sitzung und vom Remotehost [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und dessen Konten.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   Wenn Sie ein bestimmtes Verzeichnis für die Freigabe manuell erstellen möchten, können Sie eine Zeile wie folgt hinzufügen:

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Übergeben Sie Argumente für die **RxInSqlServer** Konstruktor zur Erstellung der *computekontext-Objekt*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    Die Syntax für **RxInSqlServer** sieht fast identisch mit der **RxSqlServerData** -Funktion, die Sie zuvor zum Definieren der Datenquelle verwendet. Es gibt jedoch auch wichtige Unterschiede.
      
    - Das Datenquellenobjekt (mithilfe der Funktion [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)definiert) gibt an, wo die Daten gespeichert werden.
    
    - Im Gegensatz dazu im rechenkontext definiert, mit der Funktion [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) gibt an, wo Aggregationen und andere Berechnungen durchgeführt werden.
    
    Das Definieren eines Computekontexts wirkt sich nicht auf andere generische R-Berechnungen aus, die Sie auf Ihrer Arbeitsstation ausführen können, und ändert nicht die Quelle der Daten. Sie können z.B. eine lokale Textdatei als Datenquelle definieren, aber SQL Server als Computekontext verwenden und alle Lesevorgänge und Zusammenfassungen der Daten auf dem SQL Server-Computer ausführen.

5. Aktivieren Sie den entfernten computekontext.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. Zurückgeben von Informationen zu den computekontext, einschließlich der zugehörigen Eigenschaften.

    ```R
    rxGetComputeContext()
    ```

7. Zurücksetzen von den computekontext auf dem lokalen Computer durch das Schlüsselwort "local" (die nächste Lektion wird veranschaulicht, mit dem entfernten computekontext) angeben.

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> Sie erhalten eine Liste der Schlüsselwörter, die von dieser Funktion unterstützt werden, indem Sie `help("rxSetComputeContext")` in der Befehlszeile von R eingeben.

## <a name="enable-tracing"></a>Aktivieren der Ablaufverfolgung

Es kann vorkommen, dass Vorgänge, die in Ihrem lokalen Kontext funktionieren, jedoch Probleme bei der Ausführung in einem Remotecomputekontext haben. Wenn Sie Probleme analysieren oder die Leistung überwachen möchten, können Sie die Ablaufverfolgung im computekontext, zur Unterstützung der Problembehandlung zur Laufzeit aktivieren.

1. Erstellen Sie einen neuen computekontext, die die gleiche Verbindungszeichenfolge verwendet, aber fügen Sie die Argumente *TraceEnabled* und *TraceLevel* auf die **RxInSqlServer** Konstruktor.

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

2. Verwenden der [RxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) Funktion, um die Ablaufverfolgung aktivierte computekontext anhand des Namens anzugeben.

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie computekontexte, die zum Ausführen von R-Code auf dem Server oder lokal zu wechseln.

> [!div class="nextstepaction"]
> [Compute-zusammenfassungsstatistiken in lokalen und Remote computekontexte](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)