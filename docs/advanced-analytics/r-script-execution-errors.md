---
title: R-Skripterstellung Fehler und Problembehandlung – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2df4fa2fd9ef52fe5edbca9440f73f351553f1ed
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511527"
---
# <a name="r-scripting-errors-in-sql-server"></a>R-Skript-Fehler in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel werden mehrere Scriptin Gerrors, bei der R-Code in SQL Server ausgeführt wird. Die Liste ist nicht vollständig. Es gibt viele Pakete, und Fehler können zwischen verschiedenen Versionen desselben Pakets variieren. Es wird empfohlen, Posten Skriptfehler auf die [Machine Learning-Server-Forum](https://social.msdn.microsoft.com/Forums/en-US/home?category=MicrosoftR), Machine learning-Komponenten, die in R Services (Datenbankintern), Microsoft R Client und Microsoft R Server unterstützt.

**Gilt für:** SQL Server 2016 R Services, SQL Server 2017-Machine Learning-Dienste


## <a name="valid-script-fails-in-t-sql-or-in-stored-procedures"></a>Gültige Skript fehlschlägt, in T-SQL oder in gespeicherten Prozeduren

Vor dem umschließen Ihrer R-Codes in einer gespeicherten Prozedur, ist es eine gute Idee, Ihren R-Code in einer externen IDE oder in einem von der R-Tools wie z. B. RTerm oder RGui auszuführen. Mithilfe dieser Methoden können können Sie testen und Debuggen von Code mithilfe von detaillierte Fehlermeldungen, die von r zurückgegeben werden

Allerdings manchmal Code, der in einer externen IDE oder das Hilfsprogramm perfekt funktioniert möglicherweise führen Sie in einer gespeicherten Prozedur oder in einer SQL Server-computekontext. In diesem Fall stehen eine Reihe von Problemen, suchen Sie nach, bevor Sie davon ausgehen können, dass das Paket in SQL Server funktionieren nicht.

1. Überprüfen Sie, ob Sie Launchpad ausgeführt wird.

2. Überprüfen Sie die Nachrichten, um festzustellen, ob entweder den Eingabedaten oder die Ausgabedaten Spalten mit nicht kompatibel oder nicht unterstützter Datentypen enthält. Beispielsweise zurückgeben Abfragen für eine SQL-Datenbank häufig, GUIDs oder RowGUIDs, beide nicht unterstützt werden. Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

3. Überprüfen Sie die Hilfeseiten für einzelne R-Funktionen, um zu bestimmen, ob alle Parameter für den SQL Server-computekontext unterstützt werden. ScaleR-Hilfe, verwenden Sie die Inline-R-Help-Befehle oder finden Sie unter [Paketverweis](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

Wenn die R-Laufzeit funktioniert, aber das Skript gibt Fehler zurück, empfehlen wir, dass Sie versuchen, das Skript in eine dedizierte R-Entwicklungsumgebung, z.B. R Tools für Visual Studio debuggen.

Außerdem wird empfohlen, dass Sie etwas schreiben Sie das Skript aus, um Probleme mit Datentypen, die auftreten können, beim Verschieben von Daten zwischen R und die Datenbank-Engine zu beheben und überprüfen. Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

Des Sqlrutils-Pakets können Sie außerdem um Ihr R-Skript in einem Format zu bündeln, die mehr leicht verwendbaren als gespeicherte Prozedur ist. Weitere Informationen finden Sie in den folgenden Themen:
* [Sqlrutils-Pakets](r/ref-r-sqlrutils.md)
* [Erstellen einer gespeicherten Prozedur mithilfe von sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="script-returns-inconsistent-results"></a>Skript gibt inkonsistente Ergebnisse zurück.

R-Skripts können unterschiedliche Werte in einem SQL Server-Kontext, verschiedene Ursachen zurückgeben:

- Implizite typkonvertierung ist für einige Datentypen automatisch ausgeführt, wenn die Daten zwischen SQL Server und r übergeben wird Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

- Bestimmen Sie, ob die Bitanzahl für das ein Faktor ist. Es gibt z. B. häufig Unterschiede in den Ergebnissen aus mathematischen Vorgängen für 32-Bit und 64-Bit-floating Point-Bibliotheken.

- Bestimmen Sie, ob die NaN-Werte in jeder Vorgang erzeugt wurden. Dies kann sich die Ergebnisse ungültig machen.

- Wenn Sie eine Kehrwert einer Zahl in der Nähe von 0 (null) erstellen, können geringfügige Unterschiede verstärkt werden.

- Kumulierte Rundungsfehler, können z. B. Werte verursachen, die sind kleiner als 0 (null) anstelle von 0 (null).

## <a name="implied-authentication-for-remote-execution-via-odbc"></a>Implizite Authentifizierung für die Remoteausführung über ODBC

Wenn Sie zum Verbinden der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Computer zum Ausführen von R-Befehle mithilfe der **RevoScaleR** Funktionen erhalten Sie möglicherweise eine Fehlermeldung bei Verwendung von ODBC-Aufrufe, die Daten an den Server zu schreiben. Dieser Fehler tritt nur auf, wenn Sie die Windows-Authentifizierung verwenden.

Der Grund ist, dass die workerkonten, die für R Services erstellt wurden keine Berechtigung zur Verbindung mit des Servers. Aus diesem Grund können die ODBC-Aufrufe in Ihrem Namen ausgeführt werden. Das Problem tritt nicht mit SQL-Anmeldungen, da mit SQL-Anmeldungen, die Anmeldeinformationen explizit vom R-Client mit der SQL Server-Instanz und dann an ODBC übergeben werden. Es ist jedoch auch weniger sicher als die Windows-Authentifizierung, SQL-Anmeldungen verwenden.

Ihre Anmeldeinformationen muss emulieren, um Ihre Windows-Anmeldeinformationen auf sichere Weise aus einem Skript übergeben werden, die Remote SQL Server initiiert hat zu aktivieren. Dieser Prozess wird als bezeichnet _implizite Authentifizierung_. Damit dies funktioniert, müssen die workerkonten, die R- oder Python-Skripts auf dem SQL Server-Computer ausgeführt, die richtigen Berechtigungen verfügen.

1. Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] als Administrator für die Instanz, in dem R-Code ausgeführt werden soll.

2. Führen Sie das folgende Skript aus: Achten Sie darauf, um den Benutzergruppennamen, wenn Sie die Standardeinstellung geändert haben, und die Computer und die Instanz-Namen zu bearbeiten.

    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

## <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>Vermeiden Sie den Arbeitsbereich löschen, während Sie R in einem SQL-rechenkontext ausführen

Obwohl das Löschen des Arbeitsbereichs häufig vorkommt, ist bei der Arbeit in der R-Konsole haben sie unbeabsichtigte Folgen in einer SQL-computekontext.

`revoScriptConnection` ist ein Objekt im R-Arbeitsbereich, der Informationen über eine R-Sitzung enthält, die von SQL Server aufgerufen wird. Aber wenn Ihr R-Code einen Befehl zum Löschen des Arbeitsbereichs enthält (z. B. `rm(list=ls())`), alle Informationen über die Sitzung und andere Objekte im R-Arbeitsbereich ebenfalls gelöscht.

Dieses Problem zu umgehen vermeiden Sie willkürliches Löschen von Variablen und anderen Objekten, während Sie R in SQL Server ausführen. Sie können bestimmte Variablen löschen, indem Sie mit der **entfernen** Funktion:

```R
remove('name1', 'name2', ...)
```

Wenn Sie mehrere Variablen löschen, wird empfohlen, dass Sie die Namen von temporären Variablen in einer Liste speichern, und Sie dann in der Liste regelmäßig Garbage Collections führen.



## <a name="next-steps"></a>Nächste Schritte

[Machine Learning-Dienste zur Problembehandlung und bekannte Probleme](machine-learning-troubleshooting-faq.md)

[Die Datensammlung für die Problembehandlung von Machine learning](data-collection-ml-troubleshooting-process.md)

[Häufig gestellte Fragen zu Upgrade und Installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Problembehandlung bei Datenbank-Engine-Verbindungen](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
