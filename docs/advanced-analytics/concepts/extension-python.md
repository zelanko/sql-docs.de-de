---
title: Python-Programmiersprachenerweiterung
description: Erfahren Sie mehr über die Ausführung von Python-Code und integrierte Python-Bibliotheken in SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/04/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0445fb83a1ee4c4e2a991df8e698f24988454d19
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727676"
---
# <a name="python-language-extension-in-sql-server"></a>Python-Spracherweiterung in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die Python-Erweiterung ist Teil des SQL Server Machine Learning Services-Add-Ons für die relationale Datenbank-Engine. Es werden eine Python-Ausführungsumgebung, eine Anaconda-Distribution mit Python-Runtime und Python-Interpreter Version 3.5, Standardbibliotheken und -tools sowie die Microsoft-Produktbibliotheken für Python hinzugefügt: [revoscalepy](../python/ref-py-revoscalepy.md) für skalierte Analysen und [microsoftml](../python/ref-py-microsoftml.md) für Algorithmen für maschinelles Lernen. 

Die Python-Integration wird als [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) installiert.

Die Installation von Python-Runtime und -Interpreter Version 3.5 gewährleistet eine nahezu vollständige Kompatibilität mit Python-Standardlösungen. Python wird in einem separaten Prozess von SQL Server ausgeführt, um sicherzustellen, dass die Datenbankvorgänge nicht beeinträchtigt werden.

## <a name="python-components"></a>Python-Komponenten

SQL Server enthält sowohl Open Source- als auch proprietäre Pakete. Die von Setup installierte Python-Runtime ist Anaconda 4.2 mit Python 3.5. Python-Runtime wird unabhängig von SQL-Tools installiert und außerhalb der Kernprozesse der Engine im Erweiterbarkeitsframework ausgeführt. Im Rahmen der Installation von Machine Learning Services mit Python müssen Sie den Bedingungen der öffentlichen GNU-Lizenz zustimmen. 

SQL Server ändert die ausführbaren Python-Dateien nicht. Sie müssen jedoch die Version von Python verwenden, die von Setup installiert wird, da auf dieser Version die proprietären Pakete erstellt und getestet werden. Eine Liste der von der Anaconda-Distribution unterstützten Pakete finden Sie auf der Website „Anaconda Documentation“: [Anaconda-Paketliste](https://docs.continuum.io/anaconda/packages/pkg-docs).

Die Anaconda-Distribution, die mit einer bestimmten Datenbank-Engine verknüpft ist, finden Sie in dem Ordner, der mit der Instanz verknüpft ist. Wenn Sie beispielsweise die SQL Server 2017-Datenbank-Engine mit Machine Learning Services und Python auf der Standardinstanz installiert haben, suchen Sie unter `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`.

Python-Pakete, die von Microsoft für parallele und verteilte Workloads hinzugefügt wurden, umfassen die folgenden Bibliotheken.

| Bibliothek | Beschreibung |
|---------|-------------|
| [**revoscalepy**](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Unterstützt Datenquellenobjekte sowie die Exploration, Manipulation, Transformation und Visualisierung von Daten. Unterstützt die Erstellung von Remotecomputekontexten sowie verschiedene skalierbare Machine Learning-Modelle wie **rxLinMod**. Weitere Informationen finden Sie unter [revoscalepy (Python-Modul in SQL Server)](../python/ref-py-revoscalepy.md).  |
| [**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Enthält Algorithmen für das maschinelle Lernen, die hinsichtlich Geschwindigkeit und Genauigkeit optimiert wurden, sowie Inline-Transformationen für die Arbeit mit Text und Bildern. Weitere Informationen finden Sie unter [microsoftml (Python-Modul in SQL Server)](../python/ref-py-microsoftml.md). |

microsoftml und revoscalepy sind eng miteinander verbunden; in microsoftsoftml verwendete Datenquellen sind als revoscalepy-Objekte definiert. Berechnen Sie Kontextbeschränkungen bei der revoscalepy-Übertragung nach microsoftml. Die gesamte Funktionalität für lokale Vorgänge ist zwar verfügbar, aber der Wechsel zu einem Remotecomputekontext erfordert RxInSqlServer.

## <a name="using-python-in-sql-server"></a>Verwenden von Python in SQL Server

Sie importieren das Modul **revoscalepy** in Ihren Python-Code und rufen dann Funktionen aus dem Modul auf, wie bei allen anderen Python-Funktionen.

Unterstützte Datenquellen sind ODBC-Datenbanken, SQL Server und das XDF-Dateiformat, um Daten mit anderen Quellen oder mit R-Lösungen auszutauschen. Die Eingabedaten für Python müssen tabellarisch sein. Alle Python-Ergebnisse müssen in Form eines **Pandas**-Datenrahmens zurückgegeben werden.

Unterstützte Computekontexte sind lokale oder SQL Server-Remotecomputekontexte. Ein Remotecomputekontext bezieht sich auf die Codeausführung, die auf einem Computer (beispielsweise einer Arbeitsstation) beginnt, aber dann die Skriptausführung auf einen Remotecomputer schaltet. Zum Wechseln des Computekontexts müssen beide Systeme dieselbe revoscalepy-Bibliothek aufweisen.

Ein lokaler Computekontext umfasst naturgemäß die Ausführung von Python-Code auf demselben Server wie die Instanz der Datenbank-Engine, wobei sich der Code in T-SQL befindet oder in eine gespeicherte Prozedur eingebettet ist. Sie können den Code auch aus einer lokalen Python-IDE ausführen und das Skript auf dem SQL Server-Computer ausführen lassen, indem Sie einen Remotecomputekontext definieren.

## <a name="execution-architecture"></a>Ausführungsarchitektur

Die folgenden Diagramme zeigen die Interaktion von SQL Server-Komponenten mit Python-Runtime in jedem der unterstützten Szenarios: datenbankinternes Ausführen von Skripts und Remoteausführung von einer Python-Befehlszeile aus, indem ein SQL Server-Computekontext verwendet wird.

### <a name="python-scripts-executed-in-database"></a>Datenbankinternes Ausführen von Python-Skripts

Wenn Sie Python „innerhalb“ von SQL Server ausführen, müssen Sie das Python-Skript in einer speziellen gespeicherten Prozedur kapseln, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Nachdem das Skript in die gespeicherte Prozedur eingebettet wurde, kann jede Anwendung, die einen Aufruf der gespeicherten Prozedur ausführen kann, die Ausführung von Python-Code einleiten.  Anschließend verwaltet SQL Server die Ausführung des Codes. Dies wird im folgenden Diagramm gezeigt.

![script-in-db-python](../../advanced-analytics/python/media/script-in-db-python2.png)

1. Eine Anforderung für Python-Runtime wird vom Parameter `@language='Python'` angegeben, der an die gespeicherte Prozedur weitergegeben wird. SQL Server sendet diese Anforderung an den Launchpad-Dienst.
Unter Linux verwendet SQL einen **launchpadd**-Dienst, um mit einem separaten Launchpad-Prozess für jeden Benutzer zu kommunizieren. Ausführliche Informationen finden Sie im [Diagramm zur Erweiterbarkeitsarchitektur](extensibility-framework.md#architecture-diagram).
2. Der Launchpad-Dienst startet das entsprechende Startprogramm; in diesem Fall „PythonLauncher“.
3. PythonLauncher startet den externen Python35-Prozess.
4. BxlServer koordiniert mit Python-Runtime, um die Austauschvorgänge von Daten und der Speicherung von Arbeitsergebnissen zu verwalten.
5. SQL Satellite verwaltet die Kommunikation über zugehörige Aufgaben und Prozesse mit SQL Server.
6. BxlServer verwendet SQL Satellite, um Status und Ergebnisse an SQL Server zu übermitteln.
7. SQL Server ruft die Ergebnisse ab und schließt zugehörige Aufgaben und Prozesse.

### <a name="python-scripts-executed-from-a-remote-client"></a>Von einem Remoteclient ausgeführte Python-Skripts

Sie können Python-Skripts von einem Remotecomputer, z. B. einem Laptop, ausführen und im Kontext des SQL Server-Computers ausführen lassen, wenn diese Bedingungen erfüllt sind:

+ Sie entwerfen die Skripts entsprechend.
+ Der Remotecomputer hat die Erweiterbarkeitsbibliotheken installiert, die von Machine Learning Services verwendet werden. Das [revoscalepy](../python/ref-py-revoscalepy.md)-Paket ist zur Verwendung von Remotecomputekontexten erforderlich.

Das folgende Diagramm stellt den gesamten Workflow dar, wenn Skripts von einem Remotecomputer gesendet werden.

![remote-sqlcc-from-python](../../advanced-analytics/python/media/remote-sqlcc-from-python3.png)

1. Python-Runtime ruft für in **revoscalepy** unterstützte Funktionen eine Verknüpfungsfunktion auf, die wiederum Bxlserver aufruft.
2. BxlServer ist in Machine Learning Services (datenbankintern) enthalten und läuft in einem separaten Prozess von Python-Runtime.
3. BxlServer bestimmt das Verbindungsziel und initiiert eine Verbindung mithilfe von ODBC, wobei Anmeldeinformationen, die als Teil der Verbindungszeichenfolge im Python-Skript bereitgestellt werden, übergeben werden.
4. BxlServer öffnet eine Verbindung mit der SQL Server-Instanz.
5. Beim Aufruf einer externen Skriptruntime wird der Launchpad-Dienst aufgerufen, der wiederum das entsprechenden Startprogramm startet: in diesem Fall PythonLauncher.dll. Danach wird die Verarbeitung von Python-Code in einem Workflow ähnlich behandelt wie beim Aufruf von Python-Code aus einer gespeicherten Prozedur in T-SQL.
6. PythonLauncher ruft die Python-Instanz ab, die auf dem SQL Server-Computer installiert ist.
7. Ergebnisse werden an BxlServer zurückgegeben.
8. SQL Satellite verwaltet die Kommunikation mit SQL Server sowie die Bereinigung zugehöriger Auftragsobjekte.
9. SQL Server gibt die Ergebnisse an den Client zurück.

## <a name="next-steps"></a>Nächste Schritte

+ [revoscalepy (Python-Modul in SQL Server)](../python/ref-py-revoscalepy.md)
+ [revoscalepy-Funktionsreferenz](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
+ [Erweiterbarkeitsframework in SQL Server](extensibility-framework.md)
+ [R- und Machine Learning-Erweiterungen in SQL Server](extension-r.md)
+ [Abrufen von Paketinformationen für Python](../package-management/python-package-information.md)
+ [Installieren von Python-Paketen mit sqlmlutils](../package-management/install-additional-python-packages-on-sql-server.md)
