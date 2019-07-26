---
title: R-Skript Fehler und Problembehandlung
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 268b3df72d468170fbefae2557892c49fd15515c
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470292"
---
# <a name="r-scripting-errors-in-sql-server"></a>R-Skript Fehler in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden mehrere scriptin-gerroren dokumentiert, wenn R-Code in SQL Server ausgeführt wird. Die Liste ist nicht vollständig. Es gibt viele Pakete, und Fehler können zwischen den Versionen desselben Pakets variieren. Es wird empfohlen, Skript Fehler im [Machine Learning Server Forum](https://social.msdn.microsoft.com/Forums/en-US/home?category=MicrosoftR)zu veröffentlichen, das die Machine Learning-Komponenten unterstützt, die in R Services (in-Database), Microsoft R Client und Microsoft R Server verwendet werden.

**Gilt für:** SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services


## <a name="valid-script-fails-in-t-sql-or-in-stored-procedures"></a>Gültiger Skript Fehler in T-SQL oder in gespeicherten Prozeduren

Bevor Sie Ihren r-Code in einer gespeicherten Prozedur Umpacken, empfiehlt es sich, ihren r-Code in einer externen IDE oder in einem der r-Tools wie RTERM oder rgui auszuführen. Mithilfe dieser Methoden können Sie den Code testen und Debuggen, indem Sie die detaillierten Fehlermeldungen verwenden, die von R zurückgegeben werden.

Manchmal kann es jedoch vorkommen, dass Code, der in einer externen IDE oder einem Dienstprogramm einwandfrei funktioniert, nicht in einer gespeicherten Prozedur oder in einem SQL Server computekontext ausgeführt werden kann. Wenn dies der Fall ist, müssen Sie eine Vielzahl von Problemen suchen, bevor Sie davon ausgehen können, dass das Paket in SQL Server nicht funktioniert.

1. Überprüfen Sie, ob Launchpad ausgeführt wird.

2. Überprüfen Sie, ob die Eingabe-oder Ausgabedaten Spalten mit nicht kompatiblen oder nicht unterstützten Datentypen enthalten. Beispielsweise geben Abfragen für eine SQL-Datenbank häufig GUIDs oder ROWGUIDS zurück, die beide nicht unterstützt werden. Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

3. Überprüfen Sie die Hilfeseiten für einzelne R-Funktionen, um zu bestimmen, ob alle Parameter für den SQL Server computekontext unterstützt werden. Verwenden Sie für die Scaler-Hilfe die Inline-R-Hilfe Befehle, oder lesen Sie den Abschnitt [Paket Verweis](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

Wenn die R-Laufzeit funktionsfähig ist, das Skript jedoch Fehler zurückgibt, empfiehlt es sich, das Skript in einer dedizierten R-Entwicklungsumgebung wie R Tools für Visual Studio zu debuggen.

Außerdem wird empfohlen, dass Sie das Skript überprüfen und leicht umschreiben, um Probleme mit Datentypen zu beheben, die auftreten können, wenn Sie Daten zwischen R und der Datenbank-Engine verschieben. Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

Darüber hinaus können Sie das sqlrutils-Paket verwenden, um Ihr R-Skript in einem Format zu bündeln, das leichter als gespeicherte Prozedur verwendet werden kann. Weitere Informationen finden Sie in den folgenden Themen:
* [sqlrutils-Paket](r/ref-r-sqlrutils.md)
* [Erstellen einer gespeicherten Prozedur mithilfe von sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="script-returns-inconsistent-results"></a>Skript gibt inkonsistente Ergebnisse zurück

R-Skripts können aus verschiedenen Gründen verschiedene Werte in einem SQL Server Kontext zurückgeben:

- Die implizite Typkonvertierung wird automatisch für einige Datentypen ausgeführt, wenn die Daten zwischen SQL Server und R übermittelt werden. Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

- Stellen Sie fest, ob Bitanzahl ein Faktor ist. Beispielsweise gibt es häufig Unterschiede in den Ergebnissen von mathematischen Vorgängen für 32-Bit-und 64-Bit-Gleit Komma Bibliotheken.

- Stellen Sie fest, ob Nane in einem beliebigen Vorgang erstellt wurden. Dadurch können die Ergebnisse ungültig werden.

- Kleine Unterschiede können vergrößert werden, wenn eine Zahl in der Nähe von 0 (null) erreicht wird.

- Akkumulierte Rundungsfehler können dazu führen, dass Werte kleiner als 0 (null) anstelle von NULL sind.

## <a name="implied-authentication-for-remote-execution-via-odbc"></a>Implizite Authentifizierung für die Remote Ausführung über ODBC

Wenn Sie eine Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dem Computer herstellen, um R-Befehle mithilfe der **revoscaler** -Funktionen auszuführen, erhalten Sie möglicherweise eine Fehlermeldung, wenn Sie ODBC-Aufrufe verwenden, die Daten auf den Server schreiben. Dieser Fehler tritt nur auf, wenn Sie die Windows-Authentifizierung verwenden.

Der Grund hierfür ist, dass die für R Services erstellten workerkonten nicht über die Berechtigung zum Herstellen einer Verbindung mit dem Server verfügen. Daher können ODBC-Aufrufe nicht in Ihrem Namen ausgeführt werden. Das Problem tritt nicht bei SQL-Anmeldungen auf, weil die Anmelde Informationen bei SQL-Anmeldungen explizit vom R-Client an die SQL Server Instanz und dann an ODBC weitergegeben werden. Allerdings ist die Verwendung von SQL-Anmeldungen auch weniger sicher als die Verwendung der Windows-Authentifizierung.

Um die sichere Übergabe Ihrer Windows-Anmelde Informationen aus einem Skript zu ermöglichen, das Remote initiiert wird, müssen SQL Server Ihre Anmelde Informationen emulieren. Dieser Prozess wird als _implizite Authentifizierung_bezeichnet. Um dies zu ermöglichen, müssen die workerkonten, die R-oder python-Skripts auf dem SQL Server Computer ausführen, über die richtigen Berechtigungen verfügen.

1. Öffnen [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Sie als Administrator auf der Instanz, auf der Sie R-Code ausführen möchten.

2. Führen Sie das folgende Skript aus: Achten Sie darauf, den Namen der Benutzergruppe zu bearbeiten, wenn Sie den Standardnamen und den Namen des Computers und der Instanz geändert haben.

    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

## <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>Vermeiden Sie das Löschen des Arbeitsbereichs während der Ausführung von R in einem SQL-computekontext.

Obwohl das Löschen des Arbeitsbereichs bei der Arbeit in der R-Konsole üblich ist, kann dies unbeabsichtigte Folgen in einem SQL-computekontext haben.

`revoScriptConnection`ist ein Objekt im R-Arbeitsbereich, das Informationen zu einer R-Sitzung enthält, die von SQL Server aufgerufen wird. Wenn Ihr R-Code jedoch einen Befehl zum Löschen des Arbeitsbereichs enthält (z `rm(list=ls())`. b.), werden alle Informationen zur Sitzung und anderen Objekten im R-Arbeitsbereich ebenfalls gelöscht.

Um dieses Problem zu umgehen, vermeiden Sie das willkürliche Löschen von Variablen und anderen Objekten während der Ausführung von R in SQL Server. Sie können bestimmte Variablen löschen, indem Sie die **Remove** -Funktion verwenden:

```R
remove('name1', 'name2', ...)
```

Wenn mehrere zu löschende Variablen vorhanden sind, wird empfohlen, dass Sie die Namen temporärer Variablen in einer Liste speichern und dann regelmäßige Garbage Collections in der Liste ausführen.



## <a name="next-steps"></a>Nächste Schritte

[Machine Learning Services Problembehandlung und bekannte Probleme](machine-learning-troubleshooting-faq.md)

[Datensammlung für die Problembehandlung von Machine Learning](data-collection-ml-troubleshooting-process.md)

[Häufig gestellte Fragen zu Upgrade und Installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Problembehandlung bei Datenbank-Engine-Verbindungen](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
