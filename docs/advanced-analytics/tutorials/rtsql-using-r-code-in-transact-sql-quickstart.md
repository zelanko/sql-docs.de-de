---
title: Schnellstart für eine "Hello World" grundlegende R-codeausführung in T-SQL (SQL Server-Machine Learning) | Microsoft-Dokumentation
description: Schnellstart für R-Skript in SQL Server. Enthält die Grundlagen des Aufrufens von R-Skripts mithilfe der gespeicherten Systemprozedur Sp_execute_external_script in einer Hallo-Welt-Übung.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/08/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1a51fcb9e67bef48346ff74ebfb1e911a6ee3365
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878083"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Schnellstart: "Hello World"-R-Skript in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server umfasst die Unterstützung der Sprache R für Data Science-Analyse in residenten SQL Server-Daten. Ihr R-Skript kann der Open-Source-R-Funktionen, die R-Bibliotheken von Drittanbietern oder die integrierte Microsoft-R-Bibliotheken bestehen, z. B. [RevoScaleR](../r/revoscaler-overview.md) für predictive Analytics nach Maß. 

Ausführung des Skripts wird mithilfe von gespeicherten Prozeduren, die mit einem der folgenden Methoden:

+ Integrierte [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) gespeicherte Prozedur, die R-Skript im als Eingabeparameter übergeben.
+ Umschließen von R-Skript in einem [benutzerdefinierte gespeicherte Prozedur](sqldev-in-database-r-for-sql-developers.md) , die Sie erstellen.

In dieser schnellstartanleitung erfahren Sie, wichtige Konzepte, die durch Ausführen einer "Hello World" R-Skript InT-SQL, um eine Einführung in die **Sp_execute_external_script** gespeicherten Systemprozedur. 

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser Übung erfordert Zugriff auf eine Instanz von SQL Server mit einem der folgenden bereits installiert:

+ [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), mit der installierten R-Sprache
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

  Ihre SQL Server-Instanz kann in einer Azure-VM oder lokal sein. Machen Sie sich bewusst, dass das Feature "external Skripterstellung" standardmäßig deaktiviert ist. Sie müssen möglicherweise [aktivieren externer Skripts](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) und überprüfen Sie, ob **SQL Server Launchpad-Dienst** ausgeführt wird, bevor Sie beginnen.

+ Ein Tool für die Ausführung von SQL-Abfragen. Sie können jede Anwendung, die eine Verbindung mit SQL Server-Datenbank herstellen und T-SQL-Code ausführen können. SQL-Experten können SQL Server Management Studio (SSMS) oder Visual Studio verwenden.

Für diesen Schnellstart um zu zeigen, wie einfach es ist zum Ausführen von R in SQL Server, wir haben verwendet die neue **Mssql-Erweiterung für Visual Studio Code**. Visual Studio Code ist eine kostenlose Entwicklungsumgebung, die auf Linux-, MacOS- oder Windows ausgeführt werden kann. Die **Mssql** Erweiterung ist eine einfache Erweiterung für die Ausführung von T-SQL-Abfragen. Visual Studio Code erhalten Sie unter [Download and install Visual Studio Code (Herunterladen und Installieren von Visual Studio Code)](https://code.visualstudio.com/Download). Hinzufügen der **Mssql** -Erweiterung finden Sie im Artikel: [verwenden der Mssql-Erweiterung für Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).

## <a name="connect-to-a-database-and-run-a-hello-world-test-script"></a>Verbinden mit Datenbank und Ausführen eines Hello World-Testskripts

1. Erstellen Sie in Visual Studio Code eine neue Textdatei, und nennen Sie sie „BasicRSQL.sql“.

2. Drücken Sie, während diese Datei geöffnet ist, STRG+UMSCHALT+P (COMMAND+P auf einem Mac OS), geben Sie **sql** ein, um die SQL-Befehle aufzulisten, und klicken Sie auf **Verbinden**. Visual Studio Code fordert Sie zum Erstellen eines Profils zum Herstellen der Verbindung mit einer bestimmten Datenbank verwendet wird. Dies ist optional, aber es erleichtert das Wechseln zwischen Datenbanken und Anmeldungen.
    + Wählen Sie einen Server oder die Instanz, in dem die R in SQL Server installiert wurde.
    + Verwenden Sie ein Konto mit Berechtigungen zum Erstellen einer neuen Datenbank, führen Sie SELECT-Anweisungen aus, und zeigen Sie Tabellendefinitionen an.

2. Wenn die Verbindung hergestellt wurde, sollten Server- und Datenbankname zusammen mit Ihren aktuellen Anmeldeinformationen in der Statusleiste angezeigt werden. Wenn keine Verbindung hergestellt werden konnte, sollten Sie überprüfen, ob der Computername und der Servername richtig sind.

3. Fügen Sie diese Anweisung ein, und führen Sie sie aus.

    ```sql
    EXEC sp_execute_external_script
      @language =N'R',
      @script=N'OutputDataSet<-InputDataSet',
      @input_data_1 =N'SELECT 1 AS hello'
      WITH RESULT SETS (([Hello World] int));
    GO
    ```

Eingaben für diese gespeicherte Prozedur gehören:

+ *@language* Parameter definiert, die in diesem Fall r aufrufen, durch die spracherweiterung
+ *@script* der Parameter definiert die Befehle, die an die R-Laufzeit übergeben. Ihr gesamtes R-Skript muss von diesem Argument als Unicode-Text umschlossen sein. Sie können den Text auch einer Variablen des Typs **nvarchar** hinzufügen und die Variable anschließend aufrufen.
+ *@input_data_1* werden Daten, die von der R-Laufzeit, die die Daten mit SQL Server als dataframe zurückgibt, die an der Abfrage zurückgegeben wird.
+ WITH RESULT SETS-Klausel definiert das Schema der zurückgegeben Datentabelle für SQL Server, Hinzufügen von "Hello World" als den Namen der Spalte, **Int** für den Datentyp.

**Ergebnisse**

![rsql_basictut_hello1](media/rsql-basictut-hello1.PNG)

Wenn Sie aus dieser Abfrage Fehler erhalten, Regel, die Sie alle Probleme bei der Installation. Konfiguration nach der Installation ist erforderlich, um die Verwendung externer Codebibliotheken zu aktivieren. Finden Sie unter [Installieren von SQL Server 2017-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md) oder [Installieren von SQL Server 2016 R Services](../install/sql-r-services-windows-install.md). Ebenso, stellen Sie sicher, dass der Launchpad-Dienst ausgeführt wird. 

Je nach Umgebung kann es erforderlich sein, dass Sie die R-Workerkonten für die Verbindung mit SQL Server aktivieren, zusätzliche Netzwerkbibliotheken installieren, Remotecodeausführung zulassen oder die Instanz neu starten, nachdem alles konfiguriert wurde. Weitere Informationen finden Sie unter [R Services – Installation und Upgrade – häufig gestellte Fragen](../r/upgrade-and-installation-faq-sql-server-r-services.md)

> [!TIP]
> In Visual Studio Code können Sie den Code markieren, den Sie ausführen möchten, und STRG+UMSCHALT+E drücken. Wenn dies für Sie schwer zu merken ist, können Sie es ändern. Siehe [Customize the shortcut key bindings (Anpassen der Tastenkombinationen)](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts).
> 
> ![rsql-basictut_hello1code](media/rsql-basictut-hello1code.PNG)
> 

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie bestätigt haben, dass die Instanz mit R arbeiten kann, nehmen Sie einen genaueren Blick auf die Strukturierung von Eingaben und Ausgaben.

> [!div class="nextstepaction"]
> [Schnellstart: Behandeln Sie, Eingaben und Ausgaben](rtsql-working-with-inputs-and-outputs.md)
