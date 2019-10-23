---
title: Erweiterung der Python-Programmiersprache
description: Erfahren Sie mehr über die python-Codeausführung und integrierte python-Bibliotheken in SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f3825a2b5085bf5a6e144a602c36cb20ccaca430
ms.sourcegitcommit: 36c3ead6f2a3628f58040acf47f049f0b0957b8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2019
ms.locfileid: "71688283"
---
# <a name="python-language-extension-in-sql-server"></a>Python-Spracherweiterung in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die python-Erweiterung ist Teil des SQL Server Machine Learning Services-Add-ons für die relationale Datenbank-Engine. Es fügt eine python-Ausführungsumgebung, Anaconda-Verteilung mit der Python 3,5-Laufzeit und-Interpreter, Standardbibliotheken und-Tools sowie die Microsoft-Produkt Bibliotheken für python: [revoscalepy](../python/ref-py-revoscalepy.md) für Analysen in der Skala und [microsoftml](../python/ref-py-microsoftml.md) für Machine Learning-Algorithmen. 

Die python-Integration wird als [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)installiert.

Durch die Installation der Python 3,5-Laufzeit und des interpreters wird die nahezu umfassende Kompatibilität mit python-Standardlösungen sichergestellt. Python wird in einem separaten Prozess von SQL Server ausgeführt, um sicherzustellen, dass Daten Bank Vorgänge nicht beeinträchtigt werden.

## <a name="python-components"></a>Python-Komponenten

SQL Server enthält sowohl Open Source-als auch proprietäre Pakete. Die vom Setup installierte python-Laufzeit ist Anaconda 4,2 mit Python 3,5. Die python-Laufzeit wird unabhängig von SQL-Tools installiert und außerhalb der Kern-Engine-Prozesse im Erweiterbarkeits Framework ausgeführt. Im Rahmen der Installation von Machine Learning Services mit python müssen Sie den Bedingungen der öffentlichen GNU-Lizenz zustimmen. 

In SQL Server werden die ausführbaren Dateien von python nicht geändert. Sie müssen jedoch die Version von Python verwenden, die von Setup installiert wird, da es sich bei dieser Version um die Version handelt, auf der die proprietären Pakete erstellt und getestet werden. Eine Liste der Pakete, die von der Anaconda-Distribution unterstützt werden, finden Sie auf der Continuum Analytics-Website: [Anaconda-Paketliste](https://docs.continuum.io/anaconda/packages/pkg-docs).

Die Anaconda-Verteilung, die einer bestimmten Datenbank-Engine-Instanz zugeordnet ist, befindet sich im Ordner, der der Instanz zugeordnet ist. Wenn Sie z. b. SQL Server 2017-Datenbank-Engine mit Machine Learning Services und python auf der Standard Instanz installiert `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`haben, suchen Sie unter.

Die von Microsoft für parallele und verteilte Workloads hinzugefügten Python-Pakete enthalten die folgenden Bibliotheken.

| Library | Beschreibung |
|---------|-------------|
| [**revoscalepy**](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Unterstützt Datenquellen Objekte sowie das Durchsuchen, manipulieren, Transformieren und Visualisieren von Daten. Es unterstützt die Erstellung von remotecomputekontexten sowie verschiedene skalierbare Machine Learning-Modelle, wie z. **b. rxlinmod**. Weitere Informationen finden Sie unter [revoscalepy-Modul mit SQL Server](../python/ref-py-revoscalepy.md).  |
| [**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Enthält Machine Learning-Algorithmen, die für Geschwindigkeit und Genauigkeit optimiert wurden, sowie Inline Transformationen zum Arbeiten mit Text und Bildern. Weitere Informationen finden Sie unter [microsoftml-Modul mit SQL Server](../python/ref-py-microsoftml.md). |

Microsoftml und revoscalepy sind eng gekoppelt. Datenquellen, die in microsoftml verwendet werden, werden als revoscalepy-Objekte definiert. Rechen Kontext Einschränkungen bei der revoscalepy-Übertragung auf microsoftml. Alle Funktionen sind für lokale Vorgänge verfügbar, aber für den Wechsel zu einem remotecomputekontext ist rxinsqlserver erforderlich.

## <a name="using-python-in-sql-server"></a>Verwenden von python in SQL Server

Sie importieren das **revoscalepy** -Modul in ihren Python-Code und rufen dann wie alle anderen python-Funktionen Funktionen aus dem Modul auf.

Zu den unterstützten Datenquellen gehören ODBC-Datenbanken, SQL Server und das Xdf-Dateiformat zum Austauschen von Daten mit anderen Quellen oder R-Lösungen. Eingabedaten für python müssen tabellarisch sein. Alle python-Ergebnisse müssen in Form eines **Pandas** -Daten Rahmens zurückgegeben werden.

Unterstützte computekontexte sind lokale oder Remote SQL Server computekontext. Ein remotecomputekontext bezieht sich auf die Codeausführung, die auf einem Computer (z. b. einer Arbeitsstation) gestartet wird, die Skriptausführung jedoch auf einen Remote Computer schaltet. Zum Wechseln des computekontexts muss beide Systeme dieselbe revoscalepy-Bibliothek aufweisen.

Der lokale computekontext umfasst erwartungsgemäß die Ausführung von Python-Code auf demselben Server wie die Datenbank-Engine-Instanz, mit Code in T-SQL oder eingebettet in eine gespeicherte Prozedur. Sie können den Code auch aus einer lokalen python-IDE ausführen und das Skript auf dem SQL Server Computer ausführen lassen, indem Sie einen remotecomputekontext definieren.

## <a name="execution-architecture"></a>Ausführungs Architektur

Die folgenden Diagramme stellen die Interaktion von SQL Server-Komponenten mit der python-Laufzeit in jedem der unterstützten Szenarien dar: Ausführen von Skripts in der Datenbank und Remote Ausführung von einem python-Terminal aus mithilfe eines SQL Server computekontexts.

### <a name="python-scripts-executed-in-database"></a>In der Datenbank ausgeführte python-Skripts

Wenn Sie die python-SQL Server "innerhalb" ausführen, müssen Sie das Python-Skript in einer speziellen gespeicherten Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)Kapseln.

Nachdem das Skript in die gespeicherte Prozedur eingebettet wurde, kann jede Anwendung, die einen gespeicherten Prozedur Aufrufvorgang ausführen kann, die Ausführung des python-Codes initiieren.  Danach verwaltet SQL Server die Codeausführung, wie in der folgenden Abbildung zusammengefasst.

![script-in-db-python](../../advanced-analytics/python/media/script-in-db-python2.png)

1. Eine Anforderung für die python-Laufzeit wird durch den Parameter `@language='Python'` angegeben, der an die gespeicherte Prozedur übergeben wird. SQL Server sendet diese Anforderung an den Launchpad-Dienst.
2. Der Launchpad-Dienst startet das entsprechende Start Programm. in diesem Fall pythonlauncher.
3. Pythonlauncher startet den externen Python35-Prozess.
4. Bxlserver koordiniert mit der python-Laufzeit, um den Austausch von Daten zu verwalten und Arbeitsergebnisse zu speichern.
5. Der SQL-Satellit verwaltet die Kommunikation über verwandte Aufgaben und Prozesse mit SQL Server.
6. Bxlserver verwendet den SQL-Satelliten, um den Status und die Ergebnisse SQL Server zu übermitteln.
7. SQL Server ruft Ergebnisse ab und schließt Verwandte Aufgaben und Prozesse.

### <a name="python-scripts-executed-from-a-remote-client"></a>Von einem Remote Client ausgeführte python-Skripts

Sie können python-Skripts von einem Remote Computer aus ausführen, z. b. einem Laptop, und im Kontext des SQL Server-Computers ausgeführt werden, wenn die folgenden Bedingungen erfüllt sind:

+ Entwerfen Sie die Skripts entsprechend.
+ Der Remote Computer hat die Erweiterbarkeits Bibliotheken installiert, die von Machine Learning Services verwendet werden. Das [revoscalepy](../python/ref-py-revoscalepy.md) -Paket ist erforderlich, um remotecomputekontexte zu verwenden.

Im folgenden Diagramm wird der gesamte Workflow zusammengefasst, wenn Skripts von einem Remote Computer gesendet werden.

![remote-sqlcc-from-python](../../advanced-analytics/python/media/remote-sqlcc-from-python3.png)

1. Für Funktionen, die von **revoscalepy**unterstützt werden, ruft die python-Laufzeit eine Verknüpfungs Funktion auf, die wiederum bxlserver aufruft.
2. Bxlserver ist in Machine Learning Services (in-Database) enthalten und wird in einem separaten Prozess von der python-Laufzeit ausgeführt.
3. Bxlserver bestimmt das Verbindungs Ziel und initiiert eine Verbindung mithilfe von ODBC und übergibt Anmelde Informationen, die als Teil der Verbindungs Zeichenfolge im Python-Skript bereitgestellt werden.
4. Bxlserver öffnet eine Verbindung mit der SQL Server Instanz.
5. Wenn eine externe Skript Laufzeit aufgerufen wird, wird der Launchpad-Dienst aufgerufen, der wiederum das entsprechende Start Programm startet: in diesem Fall "pythonlauncher. dll". Anschließend wird die Verarbeitung von Python-Code in einem Workflow behandelt, der der Art entspricht, in der Python-Code von einer gespeicherten Prozedur in T-SQL aufgerufen wird.
6. Pythonlauncher führt einen Rückruf für die python-Instanz aus, die auf dem SQL Server Computer installiert ist.
7. Ergebnisse werden an BxlServer zurückgegeben.
8. Der SQL-Satellit verwaltet die Kommunikation mit SQL Server und Bereinigung verwandter Auftrags Objekte.
9. SQL Server übergibt die Ergebnisse an den Client zurück.

## <a name="next-steps"></a>Nächste Schritte

+ [revoscalepy-Modul in SQL Server](../python/ref-py-revoscalepy.md)
+ [revoscalepy-Funktionsreferenz](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
+ [Erweiterbarkeits Framework in SQL Server](extensibility-framework.md)
+ [R-und Machine Learning-Erweiterungen in SQL Server](extension-r.md)
+ [Informationen zum Python-Paket erhalten](../package-management/python-package-information.md)
+ [Installieren von Python-Paketen mit sqlmlutils](../package-management/install-additional-python-packages-on-sql-server.md)
