---
title: Was&#39;Neues in SQL Server Machine Learning Services | Microsoft-Dokumentation
description: Ankündigungen neuer Merkmale für jede Version von SQL Server 2016 R Services, R Server, SQL Server 2017-Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8d3dc4c730ea9c7c9ba0126a50ed4bb8129efc9c
ms.sourcegitcommit: fb269accc3786715c78f8b6e2ec38783a6eb63e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43152580"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Neuerungen in SQL Server Machine Learning Services 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Machine Learning-Funktionen werden mit SQL Server in jeder Version hinzugefügt, während weiter erweitern, erweitern und die Integration zwischen der Datenplattform und der Data Science, Analysen, zu vertiefen und beaufsichtigtes lernen, die Sie für Ihre Daten implementieren möchten. 

## <a name="new-in-sql-server-2017"></a>Neues in SQLServer 2017

Diese Version bietet [Python-Unterstützung und branchenweit führende Machine learning-Algorithmen](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/). Den neuen Bereich entsprechend umbenannt, SQL Server 2017 markiert die Einführung von [SQL Server Machine Learning Services (Datenbankintern)](what-is-sql-server-machine-learning.md), mit sprachunterstützung für Python und R. 

Diese Version auch [SQL Server Machine Learning Server (eigenständig)](r/r-server-standalone.md)vollständig unabhängig von SQL Server für R und Python-Workloads, die auf einem dedizierten System ausgeführt werden soll. Mit dem eigenständigen Server können Sie zu verteilen und Skalieren von R- oder Python-Lösungen ohne Verwendung von SQL Server.

### <a name="python-integration-for-in-database-analytics"></a>Integration von Python für in-Database-Analyse

Integration von T-SQL und Python wird jetzt unterstützt, über die [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) gespeicherten Systemprozedur. Sie können eine beliebige Python-Code, der mit dieser gespeicherten Prozedur aufrufen. Code in einer sicheren, dual-Architektur, die es ermöglicht Unternehmen-Bereitstellung von Python-Modelle und Skripts, die von einer Anwendung mit einer einfachen gespeicherten Prozedur ausgeführt wird. Zusätzliche Leistungsgewinne werden durch Streamen von Daten aus SQL in Python-Prozesse und MPI-ringparallelisierung erreicht.

Können Sie das T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) Funktion ausführen [nativen Bewertung](sql-native-scoring.md) auf ein vortrainiertes Modell, das zuvor in das erforderliche Binärformat gespeichert wurde.

### <a name="python-libraries"></a>Python-Bibliotheken

| Paket | Description |
|---------|-------------|
[**die revoscalepy**](python/what-is-revoscalepy.md)| Python-Entsprechung zu RevoScaleR. Sie können Python-Modelle für lineare und logistische Regressionen, Entscheidungsstrukturen, verstärkte Strukturen und zufällige Gesamtstrukturen, die alle parallelisiert werden kann und mit in remotecomputekontexten ausgeführt wird, erstellen. Dieses Paket unterstützt die Verwendung von mehreren Datenquellen und remote Compute-Kontexte. Der Data Scientist oder Entwickler kann Python-Code auf einem remote-SQL-Server, zum Durchsuchen von Daten oder erstellen Sie Modelle ohne Verschieben von Daten ausführen. |
|[**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) |Python-Darstellung des MicrosoftML-R-Pakets. |

### <a name="r-libraries"></a>R-Bibliotheken

| Paket | Description |
|---------|-------------|
| [**MicrosoftML (R)**](using-the-microsoftml-package.md) | Computekontexte für die modernen Machine Learning-Algorithmen und Transformation von Daten, die horizontal oder Ausführung in Remote sein können. Algorithmen sind anpassbare tiefgreifende neuronale Netzwerke, schnelle Entscheidungsstrukturen und entscheidungswälder, lineare Regression und logistische Regression.  |
| [**R-paketverwaltung**](r/install-additional-r-packages-on-sql-server.md) | In dieser Version, mit folgenden Vorteilen verbessert: Datenbankrollen können den DBA-Pakete verwalten und Zuweisen von Berechtigungen zum Installieren von Paketen, [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) -Anweisung im T-SQL-DBAs, die Verwaltung von Paketen, ohne zu helfen müssen wissen, R und einen umfangreichen Satz von R-Funktionen in [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) installieren, entfernen und Listen Sie die Pakete können im Besitz von Benutzern. |

### <a name="pre-trained-models"></a>Vortrainierte Modelle

[**Vortrainierte Modelle** ](install/sql-pretrained-models-install.md) stehen für Python und R. diese Modelle für die bilderkennung und positiv Negative stimmungsanalyse, mit der Vorhersagen mit Ihren eigenen Daten generiert. 


## <a name="new-in-sql-server-2016"></a>Neues in SQLServer 2016

Diese Version eingeführt Machine learning-Funktionen in SQL Server über **SQL Server 2016 R Services**, eine in-Database-Analyse-Engine für die von R-Verarbeitungsskript auf Residente Daten innerhalb einer Datenbank-Engine-Instanz.

Darüber hinaus **SQL Server 2016 R Server (eigenständig)** als eine Möglichkeit zum Installieren von R Server auf einem Windows-Server veröffentlicht wurde. SQL Server-Setup wird zunächst die einzige Möglichkeit zum Installieren von R Server für Windows bereitgestellt. In späteren Versionen können Entwickler und Data Scientists, die R Server unter Windows sollte einen anderen eigenständigen Installer Sie das gleiche Ziel erreichen. Der eigenständige Server in SQL Server ist funktionell gleichwertig mit der eigenständige Server-Produkts [Microsoft R Server für Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

| Release |Featureupdate |
|---------|----------------|
| CU-Erweiterungen | [**Echtzeitbewertung** ](real-time-scoring.md) basiert auf systemeigene C++-Bibliotheken zum Lesen eines Modells in einem optimierten Binärformat gespeichert und anschließend Vorhersagen generieren, ohne die R-Laufzeit aufrufen zu müssen. Dadurch wird die Bewertung Vorgänge wesentlich schneller. Sie können mit echtzeitbewertung, führen eine gespeicherte Prozedur oder ausführen echtzeitbewertung aus R-Code. Echtzeitbewertung ist auch für SQL Server 2016 verfügbar, wenn die Instanz, auf die neueste Version von aktualisiert wird [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
| Erste Veröffentlichung | [**R-Integration für in-Database-Analyse**](r/sql-server-r-services.md). <br/><br/> R-Pakete für die aufrufende R-Funktionen in T-SQL (und umgekehrt). RevoScaleR-Funktionen geben R-Analysen nach Maß durch Segmentieren der Daten in Komponenten, Koordination und Verwaltung verteilte Verarbeitung und Aggregieren der Ergebnisse. In SQL Server 2016 R Services (Datenbankintern) wird die RevoScaleR-Engine mit einer Datenbank-Engine-Instanz, sind die Daten und Analysen, die zusammen in demselben Verarbeitungskontext integriert. <br/><br/>T-SQL und R-Integration durch [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Sie können eine beliebige R-Code, der mit dieser gespeicherten Prozedur aufrufen. Diese sichere Infrastruktur ermöglicht die Bereitstellung der Unternehmensklasse Rn-Modelle und Skripts, die aus einer Anwendung mit einer einfachen gespeicherten Prozedur aufgerufen werden können. Zusätzliche Leistungsgewinne werden durch Streamen von Daten aus SQL in R-Prozessen und MPI-ringparallelisierung erreicht. <br/><br/>Können Sie das T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) Funktion ausführen [nativen Bewertung](sql-native-scoring.md) auf ein vortrainiertes Modell, das zuvor in das erforderliche Binärformat gespeichert wurde.|

## <a name="linux-support-roadmap"></a>Roadmap für die Linux-Unterstützung

Machine Learning mit R oder Python in der Datenbank wird in SQL Server unter Linux derzeit nicht unterstützt. Suchen Sie nach Ankündigungen in einer späteren Version.

Allerdings unter Linux durchführen können [nativen Bewertung](sql-native-scoring.md) mit der VORHERSAGE von T-SQL-Funktion. Nativen Bewertung können Sie die von einem vorab trainierten Modell sehr schnell und ohne aufrufen oder sogar müssen eine R-Laufzeit zu bewerten. Dies bedeutet, dass Sie SQL Server unter Linux verwenden können, um sehr schnell und Clientanwendungen dienen Vorhersagen zu generieren.

<a name="azure-sql-database-roadmap"></a>

## <a name="azure-sql-database-roadmap"></a>Roadmap für Azure SQL-Datenbank

Besteht eingeschränkte Unterstützung für R in Azure SQL-Datenbank: verfügbar nur in USA, Mitte, in Diensten, die im Premium-Tarif erstellt. Erweiterten Coverage, einschließlich der Python-Unterstützung, wird wahrscheinlich in einer zukünftigen Version ausführen. Es ist jedoch keine voraussichtliche Veröffentlichungsdatum wird zu diesem Zeitpunkt.  

## <a name="next-steps"></a>Nächste Schritte

+ [Installieren von SQL Server 2017-Machine Learning-Dienste (Datenbankintern)](install/sql-machine-learning-services-windows-install.md)
+ [Machine Learning-Tutorials und Beispiele](tutorials/machine-learning-services-tutorials.md)
