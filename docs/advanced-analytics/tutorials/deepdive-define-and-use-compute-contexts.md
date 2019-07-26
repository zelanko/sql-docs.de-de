---
title: Definieren und Verwenden von revoscaler-computekontexten
description: 'Tutorial: Exemplarische Vorgehensweise zum Definieren eines computekontexts mithilfe der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 053fc48c4117372eb3e3bebb715b4176ec1dd828
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469729"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>Definieren und Verwenden von computekontexten (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In der vorherigen Lektion haben Sie **revoscaler** -Funktionen verwendet, um Datenobjekte zu überprüfen. In dieser Lektion wird die [rxinsqlserver](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) -Funktion eingeführt, mit der Sie einen computekontext für eine Remote SQL Server definieren können. Mit einem remotecomputekontext können Sie die R-Ausführung von einer lokalen Sitzung zu einer Remote Sitzung auf dem Server verschieben. 

> [!div class="checklist"]
> * Erlernen der Elemente eines Remote SQL Server-computekontexts
> * Aktivieren der Ablauf Verfolgung für ein computecontext-Objekt

**Revoscaler** unterstützt mehrere computekontexte: Hadoop, Spark auf HDFS und SQL Server in-Database. Für SQL Server wird die **rxinsqlserver** -Funktion für Server Verbindungen und die Übergabe von Objekten zwischen dem lokalen Computer und dem Remote Ausführungs Kontext verwendet.

## <a name="create-and-set-a-compute-context"></a>Erstellen und Festlegen eines computekontexts

Die **rxinsqlserver** -Funktion, die den SQL Server computekontext erstellt, verwendet die folgenden Informationen:

+ Verbindungs Zeichenfolge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Instanz
+ Angabe, wie die Ausgabe behandelt werden soll
+ Optionale Angabe eines freigegebenen Datenverzeichnisses
+ Optionale Argumente, die die Ablauf Verfolgung aktivieren oder die Ablauf Verfolgungs Ebene angeben

In diesem Abschnitt werden die einzelnen Abschnitte erläutert.

1. Geben Sie die Verbindungs Zeichenfolge für die Instanz an, in der Berechnungen ausgeführt werden. Sie können die zuvor erstellte Verbindungs Zeichenfolge wieder verwenden.

    **Verwenden einer SQL-Anmeldung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Verwenden der Windows-Authentifizierung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. Geben Sie an, wie die Ausgabe behandelt werden soll. Mit dem folgenden Skript wird die lokale r-Sitzung angewiesen, auf den Server auf R-Auftrags Ergebnisse zu warten, bevor der nächste Vorgang verarbeitet wird. Außerdem wird die Ausgabe von Remote Berechnungen in der lokalen Sitzung unterdrückt.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    Das Argument *wait* für **RxInSqlServer** unterstützt diese Optionen:
  
    -   **TRUE**. Der Auftrag ist als Blockierung konfiguriert und wird erst nach Abschluss des Vorgangs zurückgegeben.  Weitere Informationen finden Sie unter [verteilte und parallele Verarbeitung in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Aufträge werden als nicht blockierend konfiguriert und sofort zurückgegeben, sodass Sie weiterhin anderen R-Code ausführen können. Jedoch auch im nicht blockierenden Modus muss die Clientverbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufrechterhalten werden, während der Auftrag ausgeführt wird.

3. Geben Sie optional den Speicherort eines lokalen Verzeichnisses für die gemeinsame Verwendung durch die lokale R-Sitzung und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Remote Computer und dessen Konten an.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   Wenn Sie manuell ein bestimmtes Verzeichnis für die Freigabe erstellen möchten, können Sie eine Zeile wie die folgende hinzufügen:

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Übergeben Sie Argumente an den **rxinsqlserver** -Konstruktor, um das *computecontext-Objekt*zu erstellen.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    Die Syntax für **rxinsqlserver** ist nahezu identisch mit der **rxsqlserverdata** -Funktion, die Sie zuvor zum Definieren der Datenquelle verwendet haben. Es gibt jedoch auch wichtige Unterschiede.
      
    - Das Datenquellenobjekt (mithilfe der Funktion [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)definiert) gibt an, wo die Daten gespeichert werden.
    
    - Im Gegensatz dazu gibt der mit der [rxinsqlserver](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) -Funktion definierte computekontext an, wo Aggregationen und andere Berechnungen durchgeführt werden sollen.
    
    Das Definieren eines Computekontexts wirkt sich nicht auf andere generische R-Berechnungen aus, die Sie auf Ihrer Arbeitsstation ausführen können, und ändert nicht die Quelle der Daten. Sie können z.B. eine lokale Textdatei als Datenquelle definieren, aber SQL Server als Computekontext verwenden und alle Lesevorgänge und Zusammenfassungen der Daten auf dem SQL Server-Computer ausführen.

5. Aktivieren Sie den remotecomputekontext.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. Gibt Informationen über den computekontext zurück, einschließlich der zugehörigen Eigenschaften.

    ```R
    rxGetComputeContext()
    ```

7. Setzen Sie den computekontext zurück auf den lokalen Computer, indem Sie das Schlüsselwort "local" angeben (in der nächsten Lektion wird die Verwendung des remotecomputekontexts veranschaulicht).

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> Sie erhalten eine Liste der Schlüsselwörter, die von dieser Funktion unterstützt werden, indem Sie `help("rxSetComputeContext")` in der Befehlszeile von R eingeben.

## <a name="enable-tracing"></a>Ablauf Verfolgung aktivieren

Es kann vorkommen, dass Vorgänge, die in Ihrem lokalen Kontext funktionieren, jedoch Probleme bei der Ausführung in einem Remotecomputekontext haben. Wenn Sie Probleme analysieren oder die Leistung überwachen möchten, können Sie die Ablauf Verfolgung im computekontext aktivieren, um die Problembehandlung bei der Laufzeit zu unterstützen.

1. Erstellen Sie einen neuen computekontext, der die gleiche Verbindungs Zeichenfolge verwendet, aber fügen Sie dem **rxinsqlserver** -Konstruktor die Argumente *traceaktivierte* und *TraceLevel* hinzu.

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

2. Verwenden Sie die Funktion [rxsetcomputecontext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) , um den für die Ablauf Verfolgung aktivierten computekontext anhand des Namens anzugeben.

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie computekontexte wechseln, um R-Code auf dem Server oder lokal auszuführen.

> [!div class="nextstepaction"]
> [Compute-Zusammenfassungs Statistiken in lokalen und remotecomputekontexten](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)