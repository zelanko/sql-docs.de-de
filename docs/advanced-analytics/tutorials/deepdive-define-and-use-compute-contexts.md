---
title: Definieren und Verwenden von berechneten Kontexten (SQL und R tieferer) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6a76e07cb2ecd03a59112f6c39e3fa2f7895e0a2
ms.sourcegitcommit: aa9d2826e3c451f4699c0e69c9fcc8a2781c6213
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2018
ms.locfileid: "45975639"
---
# <a name="define-and-use-compute-contexts-sql-and-r-deep-dive"></a>Definieren und Verwenden von berechneten Kontexten (SQL und R tieferer)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil des Tutorials zur Verwendung von Data Science Deep Dive [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Diese Lektion führt die [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) -Funktion, die können Sie einen computekontext für SQL Server zu definieren und dann komplexe Berechnungen ausführen, auf dem Server statt auf dem lokalen Computer. 

RevoScaleR unterstützt mehrere computekontexte, damit Sie R-Code in Hadoop, Spark oder in der Datenbank ausführen können. Für SQL Server Sie definieren, dass des Servers, und die Funktion behandelt die Aufgaben bei der Erstellung der Datenbank-Verbindung und das Übergeben von Objekten zwischen dem lokalen Computer und die remote-Ausführungskontext.

Die Funktion, die SQL Server erstellt, compute-Kontext verwendet die folgende Informationen:

- Verbindungszeichenfolge für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz
- Spezifikation der, wie die Ausgabe behandelt werden sollen
- Optionale Argumente, die die Ablaufverfolgung aktivieren, oder geben Sie die Ablaufverfolgung an
- Optionale Spezifikation von einem freigegebenen Verzeichnis

## <a name="create-and-set-a-compute-context"></a>Erstellen und Festlegen eines computekontexts

1. Geben Sie die Verbindungszeichenfolge für die Instanz, in dem Berechnungen ausgeführt werden.  Sie können die Verbindungszeichenfolge erneut verwenden, die Sie zuvor erstellt haben. Sie können eine andere Verbindungszeichenfolge erstellen, wenn Sie die Berechnungen auf einen anderen Server verschieben oder ein anderen Anmeldenamens für einige Aufgaben verwenden möchten.

    **Verwenden einer SQL-Anmeldung**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user name>;Pwd=<password>"
      ```

    **Verwenden der Windows-Authentifizierung**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
      ```
2. Geben Sie an, wie die Ausgabe behandelt werden soll. Im folgenden Code geben Sie an, dass die R-Sitzung auf der Arbeitsstation immer auf R-Auftragsergebnisse warten soll, aber keine Konsolenausgaben aus Remoteberechnungen zurückgegeben werden sollen.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    Das Argument *wait* für **RxInSqlServer** unterstützt diese Optionen:
  
    -   **TRUE**. Der Auftrag als blockiert konfiguriert ist und nicht zurückgegeben, bis er abgeschlossen wurde oder ein Fehler aufgetreten.  Weitere Informationen finden Sie unter [verteilt und parallel computing in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Aufträge werden als nicht blockierende konfiguriert und sofort zurück, sodass Sie weiterhin anderen R-Code ausführen. Jedoch auch im nicht blockierenden Modus muss die Clientverbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufrechterhalten werden, während der Auftrag ausgeführt wird.

3. Optional können Sie angeben, den Speicherort eines lokalen Verzeichnisses für die gemeinsame Nutzung von der lokalen R-Sitzung und vom Remotehost [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und dessen Konten.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. Wenn Sie ein bestimmtes Verzeichnis für die Freigabe manuell erstellen möchten, können Sie eine Zeile wie folgt hinzufügen:

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

    Um zu bestimmen, welcher Ordner derzeit für die Freigabe verwendet wird, führen `rxGetComputeContext()`, die Details zum aktuellen computekontext zurückgibt. Weitere Informationen finden Sie unter [RxInSqlServer (in englischer Sprache)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/).

4. Nachdem alle Variablen vorbereitet sind Stellen Sie diese als Argumente für die **RxInSqlServer** Konstruktor zum Erstellen der *computekontext-Objekt*.

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

## <a name="enable-tracing-on-the-compute-context"></a>Aktivieren der Ablaufverfolgung für den computekontext

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

2. Um diesen Computekontext zu ändern, verwenden Sie die Funktion [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext), und geben Sie den Kontext anhand des Namens an.

    ```R
    rxSetComputeContext( sqlComputeTrace)
    ```

    > [!NOTE]
    > 
    > In diesem Tutorial verwenden Sie den computekontext, der keine Ablaufverfolgung aktiviert werden. 
    > 
    > Wenn Sie die Ablaufverfolgung verwenden möchten, Bedenken Sie jedoch, dass Ihre Umgebung durch die Netzwerkkonnektivität beeinträchtigt wird. Achten Sie auch, da die Leistung für die Ablaufverfolgung aktiviert-Option nicht für alle Vorgänge getestet wurde.

Im nächsten Schritt, den Sie erfahren, wie Sie computekontexte, zum Ausführen von R-Code auf dem Server oder lokal.

## <a name="next-step"></a>Nächster Schritt

[Erstellen und Ausführen von R-Skripts](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)

## <a name="previous-step"></a>Vorherigen Schritt

[Abfragen und Ändern der SQL Server-Daten](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
