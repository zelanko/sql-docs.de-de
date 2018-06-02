---
title: R-Skriptfehler in SQL Server-Machine Learning und R Services | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0b695111849b234f6ca38fc89c538e905f187fb6
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34709101"
---
# <a name="r-scripting-errors-in-sql-server"></a>R-Skript-Fehler in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt mehrere Scriptin Gerrors auf, wenn R-Code in SQL Server ausgeführt wird. Die Liste ist nicht vollständig. Es gibt viele Pakete und Fehler können zwischen verschiedenen Versionen des gleichen Pakets variieren. Es wird empfohlen, Skriptfehler auf Bereitstellen der [Machine Learning-Server-Forum](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR), Machine learning-Komponenten, die zum R-Services (Datenbankintern), Microsoft R-Client und Microsoft R Server unterstützt.

**Gilt für:** SQL Server 2016-R-Services, SqlServer 2017 Machine Learning-Dienste


## <a name="valid-script-fails-in-t-sql-or-in-stored-procedures"></a>Gültiges Skript fehlschlägt, in T-SQL oder in gespeicherten Prozeduren

Vor dem umschließen Ihrer R-Codes in einer gespeicherten Prozedur, ist es ratsam, Ihre R-Code in einer externen IDE oder in einem R-Tools, z. B. RTerm oder "rgui.exe" ausgeführt. Mithilfe dieser Methoden können können Sie testen und Debuggen von Code mithilfe der detaillierte Fehlermeldungen, die von r zurückgegeben werden

Allerdings manchmal Code, der in einem externen IDE oder Hilfsprogramm perfekt funktioniert möglicherweise nicht in einer gespeicherten Prozedur ausführen oder in einer SQL Server-computekontext. In diesem Fall stehen eine Reihe von Problemen, der gesucht werden soll, bevor Sie davon ausgehen können, dass das Paket in SQL Server funktionieren nicht.

1. Überprüfen, ob Sie Launchpad ausgeführt wird.

2. Überprüfen Sie die Nachrichten, um festzustellen, ob die Eingabedaten oder die Ausgabedaten Spalten mit Datentypen nicht kompatibel oder nicht unterstützt enthält. Beispielsweise zurückgeben Abfragen für eine SQL­Datenbank häufig GUIDs oder aktualisieren, die nicht unterstützt werden. Weitere Informationen finden Sie unter [R-Bibliotheken und Datentypen](r/r-libraries-and-data-types.md).

3. Überprüfen Sie die Hilfeseiten für einzelne R-Funktionen, um zu bestimmen, ob alle Parameter für die SQL Server-computekontext unterstützt werden. Für ScaleR Hilfe zu erhalten, verwenden Sie die Befehle der Inline-R-Hilfe oder finden Sie unter [Paket Verweis](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

Wenn die R-Laufzeit funktioniert, aber Ihr Skript gibt Fehler zurück, wird empfohlen, dass Sie das Skript in einer dedizierten R-Entwicklungsumgebung, z. B. R-Tools für Visual Studio Debugging.

Außerdem wird empfohlen, dass Sie überprüfen, und etwas schreiben Sie das Skript aus, um eventuelle Probleme mit den Datentypen zu beheben, die auftreten können, wenn das Verschieben von Daten zwischen R und das Datenbankmodul. Weitere Informationen finden Sie unter [R-Bibliotheken und Datentypen](r/r-libraries-and-data-types.md).

Darüber hinaus können Sie die Sqlrutils-Paket verwenden, zum Bündeln von R-Skript in einem Format, das mehr leicht verwendbaren als gespeicherte Prozedur ist. Weitere Informationen finden Sie in den folgenden Themen:
* [Generieren Sie eine gespeicherte Prozedur für R-Code mithilfe des Sqlrutils-Pakets](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
* [Erstellen einer gespeicherten Prozedur mithilfe von sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="script-returns-inconsistent-results"></a>Skript zurückgegeben inkonsistente Ergebnisse.

R-Skripts können unterschiedliche Werte in einem SQL Server-Kontext, verschiedene Ursachen zurückgeben:

- Implizite Typumwandlung ist für einige Datentypen automatisch ausgeführt, wenn die Daten zwischen SQL Server und r übergeben wird Weitere Informationen finden Sie unter [R-Bibliotheken und Datentypen](r/r-libraries-and-data-types.md).

- Bestimmen Sie, ob Bitanzahl ein Faktor ist. Es gibt z. B. häufig Unterschiede in den Ergebnissen aus mathematischen Vorgängen für 32-Bit und 64-Bit-floating Point-Bibliotheken.

- Bestimmen Sie, ob bei jedem Vorgang NaNs erzeugt wurden. Dadurch kann die Ergebnisse ungültig.

- Geringfügige Unterschiede können verstärkt werden, wenn Sie einen Kehrwert einer Zahl in der Nähe von 0 (null) erstellen.

- Akkumulierte Rundungsfehler kann u. a. die Werte, die sind kleiner als null statt 0 (null).

## <a name="implied-authentication-for-remote-execution-via-odbc"></a>Implizite Authentifizierung für die Remoteausführung über ODBC

Wenn Sie zum Verbinden der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Computer für die Ausführung von R-Befehle mithilfe der **"revoscaler"** Funktionen die, Sie erhalten möglicherweise eine Fehlermeldung bei Verwendung von ODBC-Aufrufe, die Daten an den Server zu schreiben. Dieser Fehler tritt nur auf, wenn Sie Windows-Authentifizierung verwenden.

Der Grund ist, dass die Konten, die für R Services erstellt werden nicht für die Verbindung mit dem Server berechtigt sind. Aus diesem Grund können die ODBC-Aufrufe in Ihrem Auftrag ausgeführt werden. Das Problem tritt nicht mit SQL-Anmeldungen, da mit SQL-Anmeldungen, die Anmeldeinformationen explizit von der R-Client in SQL Server-Instanz und dann in ODBC übergeben werden. Es ist jedoch auch weniger sicher als die Windows-Authentifizierung, SQL-Anmeldungen verwenden.

Ihre Anmeldeinformationen muss emulieren, zum Aktivieren der Windows-Anmeldeinformationen, die sicher aus einem Skript übergeben werden, die Remote SQL Server initiiert hat. Dieser Prozess wird als bezeichnet _implizite Authentifizierung_. Damit dies funktioniert, benötigen die Worker-Konten, die R oder Python-Skripts auf dem SQL Server-Computer ausgeführt, die richtigen Berechtigungen.

1. Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] als Administrator für die Instanz, auf dem R-Code ausgeführt werden soll.

2. Führen Sie das folgende Skript aus: Achten Sie darauf, um Benutzergruppennamen, wenn Sie die Standardeinstellung geändert haben und die Namen von Computern und die Instanz zu bearbeiten.

    ```SQL
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

## <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>Vermeiden Sie den Arbeitsbereich löschen, während Sie R in einer SQL-computekontext ausführen

Obwohl das Löschen des Arbeitsbereichs üblich ist, bei der Arbeit in der R-Konsole, haben sie unbeabsichtigte Folgen in einer SQL-computekontext.

`revoScriptConnection` ist ein Objekt in den R-Arbeitsbereich, der Informationen über eine R-Sitzung enthält, die von SQL Server aufgerufen wird. Jedoch Wenn R-Code einen Befehl zum Deaktivieren des Arbeitsbereichs enthält (z. B. `rm(list=ls())`), alle Informationen über die Sitzung und anderen Objekten im Arbeitsbereich "R" ist ebenfalls deaktiviert.

Vermeiden Sie dieses Problem zu umgehen die willkürliche Löschen von Variablen und andere Objekte während Sie R in SQL Server ausführen. Sie können bestimmte Variablen löschen, indem Sie mit der **entfernen** Funktion:

```R
remove('name1', 'name2', ...)
```

Wenn es mehrere Variablen sind löschen, wird empfohlen, dass Sie eine Liste der Namen von temporären Variablen speichern, und führen Sie regelmäßige Ausführung von Garbage Collections auf der Liste.



## <a name="next-steps"></a>Nächste Schritte

[Machine Learning Services Problembehandlung und bekannte Probleme](machine-learning-troubleshooting-faq.md)

[Die Datensammlung für die Problembehandlung von Machine learning](data-collection-ml-troubleshooting-process.md)

[Häufig gestellte Fragen zu Upgrade und Installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Problembehandlung bei Datenbank-Engine-Verbindungen](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
