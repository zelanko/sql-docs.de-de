---
title: Schnellstart für eine "Hello World" grundlegende R-codeausführung in T-SQL (SQL Server-Machine Learning) | Microsoft-Dokumentation
description: In dieser schnellstartanleitung für R-Skript in SQL Server die Grundlagen der Sp_execute_external_script System gespeicherte Prozedur mit einer Hallo-Welt-Übung.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e738289b39f6d390bc4d6196606d242fa4803865
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086883"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Schnellstart: "Hello World"-R-Skript in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server umfasst Feature R-sprachunterstützung für residente SQL Server-Data-Analysen in der Datenbank. Sie können Open Source-R-Funktionen, Drittanbieter-Pakete und integrierte Microsoft-R-Pakete für predictive Analytics nach Maß verwenden.

In dieser schnellstartanleitung erfahren Sie, wichtige Konzepte, die durch Ausführen einer "Hello World" R-Skript InT-SQL, um eine Einführung in die **Sp_execute_external_script** gespeicherten Systemprozedur. R-skriptausführung erfolgt über gespeicherte Prozeduren. Sie können entweder die [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) gespeicherte Prozedur und übergeben Sie R in als Eingabeparameter in dieser schnellstartanleitung veranschaulicht bzw. umschließen R-Skript in einer [benutzerdefinierte gespeicherte Prozedur](sqldev-in-database-r-for-sql-developers.md). 

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser Übung erfordert Zugriff auf eine Instanz von SQL Server mit einem der folgenden bereits installiert:

+ [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), mit der installierten R-Sprache
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

  Ihre SQL Server-Instanz kann in einer Azure-VM oder lokal sein. Machen Sie sich bewusst, dass das Feature "external Skripterstellung" standardmäßig deaktiviert ist. Sie müssen möglicherweise [aktivieren externer Skripts](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) und überprüfen Sie, ob **SQL Server Launchpad-Dienst** ausgeführt wird, bevor Sie beginnen.

+ Ein Tool für die Ausführung von SQL-Abfragen. Sie können jede Anwendung, die eine Verbindung mit SQL Server-Datenbank herstellen und T-SQL-Code ausführen können. SQL-Experten können SQL Server Management Studio (SSMS) oder Visual Studio verwenden.

Für dieses Tutorial, um anzuzeigen, wie einfach es ist zum Ausführen von R in SQL Server, wir haben verwendet die neue **Mssql-Erweiterung für Visual Studio Code**. Visual Studio Code ist eine kostenlose Entwicklungsumgebung, die auf Linux-, MacOS- oder Windows ausgeführt werden kann. Die **Mssql** Erweiterung ist eine einfache Erweiterung für die Ausführung von T-SQL-Abfragen. Visual Studio Code erhalten Sie unter [Download and install Visual Studio Code (Herunterladen und Installieren von Visual Studio Code)](https://code.visualstudio.com/Download). Hinzufügen der **Mssql** -Erweiterung finden Sie im Artikel: [verwenden der Mssql-Erweiterung für Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).

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
