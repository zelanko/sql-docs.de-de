---
title: Was&#39;Neues in SQL Server Machine Learning Services | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bf56d52823727609d713639d534e277be57caaef
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174807"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Neuerungen in SQL Server Machine Learning Services 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Machine Learning-Funktionen werden mit SQL Server in jeder Version hinzugefügt, während weiter erweitern, erweitern und die Integration zwischen der Datenplattform und der Data Science, Analysen, zu vertiefen und beaufsichtigtes lernen, die Sie für Ihre Daten implementieren möchten. 

## <a name="new-in-sql-server-2017"></a>Neues in SQLServer 2017

Diese Version hinzugefügt, die Python-Unterstützung und branchenweit führende Machine learning-Algorithmen. Den neuen Bereich entsprechend umbenannt, SQL Server 2017 markierte die Einführung von **SQL Server Machine Learning Services (Datenbankintern)**, mit der sprachunterstützung für Python und R. 

Diese Version auch **SQL Server Machine Learning Server (eigenständig)** vollständig unabhängig von SQL Server für R und Python-Workloads, die auf einem dedizierten System ausgeführt werden soll. Mit dem eigenständigen Server können Sie zu verteilen und Skalieren von R- oder Python-Lösungen ohne Verwendung von SQL Server.

| Release | Featureupdate |
|---------|----------------|
| CU 6 | Fehlerbehebungen und Paket aktualisieren, jedoch keine Funktion neue Ankündigungen. Korrekturen umfassen Unterstützung für DateTime-Datentypen in SPEES-Abfrage für Python und verbesserte Fehlermeldungen in Microsoftml, wenn vorab trainierte Modelle fehlen. |
| CU 5 | Fehlerbehebungen und Paket aktualisieren, jedoch keine Funktion neue Ankündigungen. Fehlerbehebungen enthalten Verbesserungen, Funktionen und Variablen in Revoscalepy, korrigieren die lange pfadbezogene Fehler in RxInstallPackages, Beheben von Verbindungsproblemen in einen Loopback für RxExec Rx_exec Funktionen und Änderungen an Warnungen zu transformieren. |
| CU 4 | Fehlerbehebungen und Paket aktualisieren, jedoch keine Funktion neue Ankündigungen. |
| CU 3 | Serialisierung in Revoscalepy, Python-Modell mithilfe der [Rx_serialize_model Funktion](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/><br/>[Native Bewertung](sql-native-scoring.md) sowie Verbesserungen bei der [in Echtzeit bewerten](real-time-scoring.md). In der Datenbank zu bewerten, Durchsatz ist eine Million Zeilen pro Sekunde mithilfe von R-Modelle. In diesem Update wird bieten in Echtzeit zu bewerten und nativen Bewertung eine bessere Leistung in einzelne Zeile und der batchbewertung. Native Bewertung verwendet kann eine T-SQL-Funktion für die schnelle Bewertung, die in jeder Edition von SQL Server, auch unter Linux ausgeführt werden. Die Funktion erfordert keine Installation von R oder zusätzliche Konfiguration. Dies bedeutet, Sie können an anderer Stelle ein Modell trainieren, speichern Sie sie in SQL Server und führen Sie dann die Bewertung, ohne jemals r Weitere Informationen zum Bewerten von Methoden, finden Sie unter [wie scoring in Echtzeit oder nativen Bewertung](r/how-to-do-realtime-scoring.md). |
| CU 2 | Fehlerbehebungen und Paket aktualisieren, jedoch keine Funktion neue Ankündigungen. |
| CU 1 | In Revoscalepy, fügt Rx_create_col_info für die Rückgabe von Schemainformationen aus einer SQL Server-Datenquelle, die ähnlich wie [RxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) für R. <br/><br/>Verbesserungen bei der [Rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) zur Unterstützung der paralleler Szenarien für die Verwendung der `RxLocalParallel` compute Context verwenden.|
| Erste Veröffentlichung |[**Integration von Python für in-Database-Analyse**](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) <br/><br/>Die [Revoscalepy](python/what-is-revoscalepy.md) Paket ist die Python-Entsprechung zu RevoScaleR. Sie können Python-Modelle für lineare und logistische Regressionen, Entscheidungsstrukturen, verstärkte Strukturen und zufällige Gesamtstrukturen, die alle parallelisiert werden kann und mit in remotecomputekontexten ausgeführt wird, erstellen. Dieses Paket unterstützt die Verwendung von mehreren Datenquellen und remote Compute-Kontexte. Der Data Scientist oder Entwickler kann Python-Code auf einem remote-SQL-Server, zum Durchsuchen von Daten oder erstellen Sie Modelle ohne Verschieben von Daten ausführen. <br/><br/>Die [Microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) Paket ist die Python-Darstellung des MicrosoftML-R-Pakets.<br/><br/>Integration von T-SQL und Python durch [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Sie können eine beliebige Python-Code, der mit dieser gespeicherten Prozedur aufrufen. Diese sichere Infrastruktur ermöglicht die Bereitstellung von Enterprise-Grade von Python-Modellen und Skripts, die aus einer Anwendung mit einer einfachen gespeicherten Prozedur aufgerufen werden können. Zusätzliche Leistungsgewinne werden durch Streamen von Daten aus SQL in Python-Prozesse und MPI-ringparallelisierung erreicht. <br/><br/>Können Sie das T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) Funktion ausführen [nativen Bewertung](sql-native-scoring.md) auf ein vortrainiertes Modell, das zuvor in das erforderliche Binärformat gespeichert wurde.|
| Erste Veröffentlichung | [**MicrosoftML (R)** ](using-the-microsoftml-package.md) enthält Stand der Technik-Machine learning-Algorithmen und -Transformation, die horizontal oder Ausführung in remotecomputekontexten sein können. Algorithmen sind anpassbare tiefgreifende neuronale Netzwerke, schnelle Entscheidungsstrukturen und entscheidungswälder, lineare Regression und logistische Regression. |
| Erste Veröffentlichung | [**Vortrainierte Modelle** ](install/sql-pretrained-models-install.md) für die bilderkennung und positiv Negative stimmungsanalyse. Verwenden Sie diese Modelle, um Vorhersagen für Ihre eigenen Daten zu generieren. |
| Erste Veröffentlichung | [**R-paketverwaltung**](r/install-additional-r-packages-on-sql-server.md), einschließlich von folgenden Vorteilen: Datenbankrollen können den DBA-Pakete verwalten und Zuweisen von Berechtigungen zum Installieren von Paketen, [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) -Anweisung im T-SQL Hilfe DBAs Pakete verwalten, ohne zu wissen der R sowie ein umfangreichen Satz von R-Funktionen in [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) installieren, entfernen und Listen Sie die Pakete können im Besitz von Benutzern. |
| Erste Veröffentlichung | [**Operationalisierung über Mrsdeploy** ](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package) für die Bereitstellung und hosting von R-Skript als Webdienst. Gilt für nur R-Skript (keine Python-Entsprechung). Vorgesehen für die Serveroption (eigenständig), um Ressourcen zu mit anderen SQL Server-Vorgängen zu vermeiden. |


## <a name="new-in-sql-server-2016"></a>Neues in SQLServer 2016

Diese Version eingeführt Machine learning-Funktionen in SQL Server über **SQL Server 2016 R Services**, eine in-Database-Analyse-Engine für die von R-Verarbeitungsskript auf Residente Daten innerhalb einer Datenbank-Engine-Instanz.

Darüber hinaus **SQL Server 2016 R Server (eigenständig)** als eine Möglichkeit zum Installieren von R Server auf einem Windows-Server veröffentlicht wurde. SQL Server-Setup wird zunächst die einzige Möglichkeit zum Installieren von R Server für Windows bereitgestellt. In späteren Versionen können Entwickler und Data Scientists, die R Server unter Windows sollte einen anderen eigenständigen Installer Sie das gleiche Ziel erreichen. Der eigenständige Server in SQL Server ist funktionell gleichwertig mit der eigenständige Server-Produkts [Microsoft R Server für Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

| Release |Featureupdate |
|---------|----------------|
| CU-Erweiterungen | [**Bewertung in Echtzeit** ](real-time-scoring.md) basiert auf systemeigene C++-Bibliotheken zum Lesen eines Modells in einem optimierten Binärformat gespeichert und anschließend Vorhersagen generieren, ohne die R-Laufzeit aufrufen zu müssen. Dadurch wird die Bewertung Vorgänge wesentlich schneller. Mit in Echtzeit bewerten möchten, können Sie führen eine gespeicherte Prozedur oder zur echtzeitbewertung aus R-Code ausführen. In Echtzeit bewerten ist auch für SQL Server 2016 zur Verfügung, wenn die Instanz, auf die neueste Version von aktualisiert wird [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
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
