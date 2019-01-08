---
title: Python-Erweiterung "Sprache" SQL Server-Machine Learning-Programmierung
description: Informationen Sie zur Ausführung von Python-Code und integrierten Python-Bibliotheken in SQL Server 2017-Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6bbce3d58f016b26618413ef0647995d0914a237
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432323"
---
# <a name="python-language-extension-in-sql-server"></a>Erweiterung der Sprache Python in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die Python-Erweiterung ist Teil der SQL Server Machine Learning Services-Add-On der relationalen Datenbank-Engine. Fügt eine Python-Umgebung Anaconda-Distribution mit der Python 3.5-Runtime-Interpreter, standard-Bibliotheken und Tools und die Microsoft-Produkt-Bibliotheken für Python: [Revoscalepy](../python/ref-py-revoscalepy.md) für die Analyse mit Skalierung und [Microsoftml](../python/ref-py-microsoftml.md) für Machine learning-Algorithmen. 

Integration von Python installiert ist, als [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md).

Installation der Python 3.5-Laufzeit und der Interpreter gewährleistet nahezu vollständige Kompatibilität mit der standardmäßigen Python-Lösungen. Python wird in einem separaten Prozess ausgeführt, von SQL Server, um sicherzustellen, dass die Datenbankvorgänge nicht gefährdet sind.

## <a name="python-components"></a>Python-Komponenten

SQL Server umfasst sowohl Open Source- und proprietären Pakete. Die Python-Laufzeit, die von Setup installiert ist, Anaconda 4.2 in Python 3.5. Die Python-Laufzeit unabhängig von der SQL-Tools installiert ist, und außerhalb der Kern-Engine-Prozesse, in dem Extensibility Framework ausgeführt wird. Im Rahmen der Installation von Machine Learning-Dienste mit Python müssen Sie den Bedingungen der GNU Public License zustimmen. 

SQL Server ändert sich nicht auf die ausführbaren Python-Dateien, aber Sie müssen die Version von Python, die von Setup installiert werden, da diese Version der ist, dass der proprietären Pakete erstellt und getestet verwenden. Eine Liste der Pakete, die durch die Anaconda-Distribution unterstützt finden Sie unter der Continuum Analytics-Website: [Die Liste der Pakete Anaconda](https://docs.continuum.io/anaconda/packages/pkg-docs).

Die Anaconda-Distribution, die eine bestimmte Datenbank-Engine-Instanz zugeordneten finden Sie in den Ordner mit der Instanz verknüpft ist. Z. B. Wenn Sie SQL Server 2017-Datenbank-Engine mit Machine Learning-Dienste und Python auf der Standardinstanz installiert haben, suchen Sie unter `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`.

Python-Pakete, die von Microsoft für parallelen und verteilten Workloads hinzugefügt enthalten die folgenden Bibliotheken.

| Bibliothek | Description |
|---------|-------------|
| [**die revoscalepy**](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Unterstützt von Datenquellenobjekten und Durchsuchen von Daten, Manipulation, Transformation und Visualisierung. Es unterstützt die Erstellung von remotecomputekontexte sowie verschiedene skalierbare Machine Learning-Modellen wie z. B. **RxLinMod**. Weitere Informationen finden Sie unter [Revoscalepy-Modul mit SQL Server](../python/ref-py-revoscalepy.md).  |
| [**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Enthält die Machine Learning-Algorithmen, die wurden optimiert Geschwindigkeit und Genauigkeit als auch Inline-Transformationen für die Arbeit mit Text und Bilder. Weitere Informationen finden Sie unter [Microsoftml-Modul mit SQL Server](../python/ref-py-microsoftml.md). |

Microsoftml "und" Revoscalepy sind eng verknüpft; in Microsoftml verwendete Datenquellen werden als Revoscalepy-Objekte definiert. Kontext-Einschränkungen in Revoscalepy-Übertragung in Microsoftml zu berechnen. Nämlich alle Funktionen sind für lokale Vorgänge verfügbar, aber das Wechseln zu einem remotecomputekontext erfordert RxInSqlServer.

## <a name="using-python-in-sql-server"></a>Verwenden von Python in SQLServer

Sie importieren die **Revoscalepy** Module in Ihre Python-Code, und rufen die Funktionen des Moduls, wie alle anderen Python-Funktionen.

Unterstützte Datenquellen umfassen die ODBC-Datenbanken, SQL Server und einer XDF-Datei-Format zum Austauschen von Daten mit anderen Datenquellen oder mit R-Lösungen. Eingabedaten für Python müssen tabellarische sein. Alle Python-Ergebnisse zurückgegeben werden müssen, in Form einer **Pandas** Datenrahmen.

Unterstützte computekontexte umfassen lokal oder remote SQL Server-computekontext. Ein remotecomputekontext bezieht sich auf die Ausführung von Code, der auf einem Computer, z. B. eine Arbeitsstation beginnt, aber dann Switches der skriptausführung auf einem Remotecomputer befindet. Wechseln den computekontext erfordert, dass beide Systeme dieselbe Revoscalepy-Bibliothek.

Lokalen computekontext zu erwarten, umfasst die Ausführung von Python-Code auf dem gleichen Server wie die Datenbank-Engine-Instanz, mit Code in T-SQL oder in einer gespeicherten Prozedur eingebettet. Sie können auch führen Sie den Code von einer lokalen Python-IDE und das Skript auf dem SQL Server-Computer ausgeführt werden, durch die Definition einer Remote-computekontext.

## <a name="execution-architecture"></a>Ausführung-Architektur

Die folgenden Diagramme stellen die Interaktion des SQL Server-Komponenten mit der Python-Laufzeit in jeder der unterstützten Szenarien: Ausführung des Skripts in der Datenbank und remote über das Terminal Python, verwenden einen SQL Server-computekontext ausgeführt.

### <a name="python-scripts-executed-in-database"></a>Python-Skripts ausgeführt, in der Datenbank

Wenn Sie Python "in" SQL Server ausführen, muss das Python-Skript in einer speziellen gespeicherten Prozedur gekapselt [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Nachdem das Skript in der gespeicherten Prozedur eingebettet wurde, kann jede Anwendung, die eine gespeicherte Prozedur aufrufen können Ausführung von Python-Code initiieren.  SQL Server verwaltet danach Ausführung von Code wie im folgenden Diagramm zusammengefasst.

![Skript-in-Db-python](../../advanced-analytics/python/media/script-in-db-python2.png)

1. Eine Anforderung für die Python-Laufzeit wird angegeben, durch den Parameter `@language='Python'` an die gespeicherte Prozedur übergeben. SQL-Server sendet diese Anforderung an den Launchpad-Dienst.
2. Der Launchpad-Dienst startet das entsprechende Startprogramm; In diesem Fall PythonLauncher.
3. PythonLauncher startet den externen Prozess von Python35.
4. BxlServer koordiniert mit der Python-Laufzeit, um Austauschvorgänge von Daten und Speicherung von Arbeitsergebnissen zu verwalten.
5. SQL-Satellit verwaltet die Kommunikation über verwandte Aufgaben und Prozesse mit SQL Server.
6. BxlServer verwendet SQL-Satellit zum Status und Ergebnisse an SQL Server zu kommunizieren.
7. SQL Server ruft die Ergebnisse ab und schließt Verwandte Aufgaben und Prozesse.

### <a name="python-scripts-executed-from-a-remote-client"></a>Python-Skripts, die von einem Remoteclient ausgeführt werden.

Sie können Python-Skripts von einem Remotecomputer, z. B. einem Laptop ausgeführt und haben diese im Kontext von der SQl Server-Computer ausgeführt werden, wenn diese Bedingungen erfüllt sind:

+ Sie entwerfen die Skripts ordnungsgemäß
+ Der Remotecomputer hat die Erweiterbarkeit Bibliotheken installiert, die von Machine Learning-Dienste verwendet werden. Die [Revoscalepy](../python/ref-py-revoscalepy.md) Paket ist erforderlich, um remoterechenkontexte zu verwenden.

Das folgende Diagramm fasst den gesamten Workflow aus, wenn Skripts von einem Remotecomputer gesendet werden.

![Remote-Sqlcc-aus-python](../../advanced-analytics/python/media/remote-sqlcc-from-python3.png)

1. Für Funktionen, die in Microsoft Intune **Revoscalepy**, die Python-Laufzeit ruft eine Verknüpfungsfunktion auf, die wiederum BxlServer aufruft.
2. BxlServer ist im Lieferumfang von Machine Learning Services (Datenbankintern) und in einem separaten Prozess ausgeführt wird, aus der Python-Laufzeit.
3. BxlServer bestimmt das Verbindungsziel und initiiert eine Verbindung mithilfe von ODBC, übergeben von Anmeldeinformationen, die als Teil der Verbindungszeichenfolge im Python-Skript angegeben.
4. BxlServer öffnet eine Verbindung mit SQL Server-Instanz.
5. Wenn eine externes Skript-Runtime aufgerufen wird, der Launchpad-Dienst wird aufgerufen, die wiederum startet, des entsprechenden Startprogramms: in diesem Fall PythonLauncher.dll. Danach wird die Verarbeitung von Python-Code in einem Workflow ähnelt behandelt, wenn Python-Code aus einer gespeicherten Prozedur in T-SQL aufgerufen wird.
6. PythonLauncher wird einen Aufruf an die Instanz von Python, die auf dem SQL Server-Computer installiert ist.
7. Ergebnisse werden an BxlServer zurückgegeben.
8. SQL-Satellit verwaltet die Kommunikation mit SQL Server und die Bereinigung verwandter Auftragsobjekte.
9. SQL Server übergibt die Ergebnisse an den Client zurück.

## <a name="see-also"></a>Siehe auch

+ [die Revoscalepy-Modul in SQL Server](../python/ref-py-revoscalepy.md)
+ [die Revoscalepy-Funktionsreferenz](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
+ [Extensibility Framework im SQL Server](extensibility-framework.md)
+ [R und SQL Server-Erweiterungen für maschinelles lernen](extension-r.md)