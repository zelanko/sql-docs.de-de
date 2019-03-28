---
title: SQL Server-Machine Learning-Dienste - Neuigkeiten | Microsoft-Dokumentation
description: Ankündigungen neuer Merkmale für jede Version von SQL Server 2016 R Services, R Server, SQL Server 2017-Machine Learning Services.
ms.date: 03/27/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: a41844fb7cd9c7e638d42fe9edbbb05ef0b81be1
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509827"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Neuerungen in SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Machine Learning-Funktionen werden mit SQL Server in jedem Release hinzugefügt, während weiter erweitern, erweitern und vertiefen, die Integration zwischen der Datenplattform, erweiterte Analyse und Data Science. 

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2019-preview"></a>Neues in SQL Server-2019 preview

Diese Version bietet die am häufigsten gewünschten Features für R- und Python-Machine-Learning-Vorgänge in SQL Server. Weitere Informationen über alle Funktionen in dieser Version finden Sie unter [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md) und [Versionshinweise für SQL Server-2019](../sql-server/sql-server-ver15-release-notes.md).

| Release | Featureupdate |
|---------|----------------|
| CTP 2.4 | Linux-Unterstützung für [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) für R, Python und Java. |
| | Die Umgebungsvariable aus, der angibt, den Speicherort der Java-Interpreter geändert hat `JAVA_HOME` zu `JRE_HOME`. |
| CTP 2.3 | Neuen unterstützten [Java-Datentypen](java/java-sql-datatypes.md). |
| | Auf Windows nur Java-Code erfolgen kann in eine externe Bibliothek mit den [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) Anweisung. Entsprechende Funktionalität wird unter Linux in einer zukünftigen CTP verfügbar sein. Weitere Informationen: [Gewusst wie: Aufrufen von Java aus SQL Server](java/howto-call-java-from-sql.md). |
| | Python-Code kann auf Windows nur in eine externe Bibliothek mit zugegriffen werden die [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) Anweisung. Entsprechende Funktionalität wird unter Linux in einer zukünftigen CTP verfügbar sein. |
| CTP 2.2 | Keine Änderungen. |
| CTP 2.1 | Keine Änderungen. |
| CTP 2.0 | Linux-Unterstützung für R und Python-Machine-Learning-Plattform. Erste Schritte mit [Installieren von SQL Server Machine Learning Services unter Linux](../linux/sql-server-linux-setup-machine-learning.md). |
|   | [Java-spracherweiterung](java/extension-java.md) ist neu in SQL Server-2019 Preview unter Windows und Linux. Sie können kompilierte Java-code zu SQL Server zur Verfügung durch Zuweisen von Berechtigungen und Festlegen des Pfads. Client-apps mit Zugriff auf SQL Server können Sie Daten und Ausführen des Codes durch den Aufruf [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), den gleichen Schritten für die Integration von R und Python in SQL Server. | 
|  | Die [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) führt zwei neue Parameter, mit denen Sie problemlos mehrere Modelle von partitionierten Daten generieren können. Weitere Informationen in diesem Tutorial [Partition basierenden Modellen in R erstellen](tutorials/r-tutorial-create-models-per-partition.md). |
|   | Failover-Clusterunterstützung wird jetzt unterstützt, unter Windows und Linux, vorausgesetzt, dass SQL Server Launchpad-Dienst auf allen Knoten gestartet wurde. Weitere Informationen finden Sie unter [SQL Server-Failoverclusterinstallation](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md). |

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2017"></a>Neues in SQLServer 2017

Diese Version bietet [Python-Unterstützung und branchenweit führende Machine learning-Algorithmen](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/). Den neuen Bereich entsprechend umbenannt, SQL Server 2017 markiert die Einführung von [SQL Server Machine Learning Services (Datenbankintern)](what-is-sql-server-machine-learning.md), mit sprachunterstützung für Python und R. 

Feature Ankündigungen allumfassende, finden Sie unter [Neuigkeiten in SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

### <a name="r-enhancements"></a>R-Erweiterungen

Die R-Komponente des SQL Server 2017-Machine Learning Services ist die nächste Generation von SQL Server 2016 R Services durch aktualisierte Versionen der Basis-R RevoScaler und andere Pakete.

Die neuen Funktionen für R umfassen [ **paketverwaltung**](r/install-additional-r-packages-on-sql-server.md), mit folgenden Vorteilen: 

+ Datenbankrollen können Datenbankadministratoren-Pakete verwalten und Zuweisen von Berechtigungen für die Paketinstallation an.
+ [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) können DBAs Verwalten von Paketen in der vertrauten T-SQL-Sprache.
+ [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) Funktionen können entfernen und Listen Sie die Pakete im Besitz von Benutzern zu installieren. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden der RevoScaleR-Funktionen zum Suchen oder installieren R-Pakete auf SQL Server](r/use-revoscaler-to-manage-r-packages.md).

### <a name="r-libraries"></a>R-Bibliotheken

| Package | Description |
|---------|-------------|
| [**MicrosoftML**](r/ref-r-microsoftml.md) | In dieser Version ist MicrosoftML in einer Standardinstallation von R enthalten beseitigen den Schritt zum Upgrade in der vorherigen SQL Server 2016 R Services erforderlich. MicrosoftML bietet die neuesten Machine learning-Algorithmen und Transformieren von Daten, die skaliert werden können oder die in remotecomputekontexten ausgeführt werden kann. Algorithmen sind anpassbare tiefgreifende neuronale Netzwerke, schnelle Entscheidungsstrukturen und entscheidungswälder, lineare Regression und logistische Regression.  |

### <a name="python-integration-for-in-database-analytics"></a>Integration von Python für in-Database-Analyse

Python ist eine Sprache, die mehr Flexibilität und Leistungsfähigkeit für eine Vielzahl von Machine learning-Aufgaben bietet. Open Source-Bibliotheken für Python enthalten mehrere Plattformen für anpassbare neuronale Netzwerke sowie in beliebte Bibliotheken für die Verarbeitung natürlicher Sprache. Jetzt wird diese häufig verwendete Sprache in SQL Server 2017-Machine Learning unterstützt.

Python in der Datenbank-Engine integriert ist, können Sie Analysen in der Nähe der Daten und beseitigen, die Kosten und Sicherheitsrisiken bei der datenverschiebung. Sie können Machine Learning-Lösungen, die basierend auf Python mithilfe von Tools wie Visual Studio bereitstellen. Ihre Produktionsanwendungen können Abrufen von Vorhersagen, Modelle, oder visuelle Elemente aus der Python 3.5-Laufzeit, die mithilfe von SQL Server-Daten auf die Methoden zugreifen.

Integration von T-SQL und Python wird unterstützt, über die [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) gespeicherten Systemprozedur. Sie können eine beliebige Python-Code, der mit dieser gespeicherten Prozedur aufrufen. Code in einer sicheren, dual-Architektur, die es ermöglicht Unternehmen-Bereitstellung von Python-Modelle und Skripts, die von einer Anwendung mit einer einfachen gespeicherten Prozedur ausgeführt wird. Zusätzliche Leistungsgewinne werden durch Streamen von Daten aus SQL in Python-Prozesse und MPI-ringparallelisierung erreicht.

Können Sie das T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) Funktion ausführen [nativen Bewertung](sql-native-scoring.md) auf ein vortrainiertes Modell, das zuvor in das erforderliche Binärformat gespeichert wurde.

### <a name="python-libraries"></a>Python-Bibliotheken

| Package | Description |
|---------|-------------|
|[**revoscalepy**](python/ref-py-revoscalepy.md)| Python-Entsprechung zu RevoScaleR. Sie können Python-Modelle für lineare und logistische Regressionen, Entscheidungsstrukturen, verstärkte Strukturen und zufällige Gesamtstrukturen, die alle parallelisiert werden kann und mit in remotecomputekontexten ausgeführt wird, erstellen. Dieses Paket unterstützt die Verwendung von mehreren Datenquellen und remote Compute-Kontexte. Der Data Scientist oder Entwickler kann Python-Code auf einem remote-SQL-Server, zum Durchsuchen von Daten oder erstellen Sie Modelle ohne Verschieben von Daten ausführen. |
|[**microsoftml**](python/ref-py-microsoftml.md) |Python-Darstellung des MicrosoftML-R-Pakets. |

### <a name="pre-trained-models"></a>Vortrainierte Modelle

[**Vortrainierte Modelle** ](install/sql-pretrained-models-install.md) stehen für Python und R. diese Modelle für die bilderkennung und positiv Negative stimmungsanalyse, mit der Vorhersagen mit Ihren eigenen Daten generiert. 

### <a name="standalone-server-as-a-shared-feature-in-sql-server-setup"></a>Eigenständiger Server als freigegebene Funktion in SQL Server-Setup

Diese Version auch bietet [SQL Server Machine Learning Server (eigenständig)](r/r-server-standalone.md), eine vollständig unabhängige Data Science-Servers, statistische und predictive Analytics in R und Python unterstützt. Wie mit R Services ist dieser Server der nächsten Version von SQL Server 2016 R Server (eigenständig). Mit dem eigenständigen Server können Sie die Verteilung und skalieren R- oder Python-Lösungen ohne Abhängigkeiten auf SQL Server.
::: moniker-end

## <a name="new-in-sql-server-2016"></a>Neues in SQLServer 2016

Diese Version eingeführt Machine learning-Funktionen in SQL Server über **SQL Server 2016 R Services**, eine in-Database-Analyse-Engine für die von R-Verarbeitungsskript auf Residente Daten innerhalb einer Datenbank-Engine-Instanz.

Darüber hinaus **SQL Server 2016 R Server (eigenständig)** als eine Möglichkeit zum Installieren von R Server auf einem Windows-Server veröffentlicht wurde. SQL Server-Setup wird zunächst die einzige Möglichkeit zum Installieren von R Server für Windows bereitgestellt. In späteren Versionen können Entwickler und Data Scientists, die R Server unter Windows sollte einen anderen eigenständigen Installer Sie das gleiche Ziel erreichen. Der eigenständige Server in SQL Server ist funktionell gleichwertig mit der eigenständige Server-Produkts [Microsoft R Server für Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Feature Ankündigungen allumfassende, finden Sie unter [Neuigkeiten in SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md).

| Release |Featureupdate |
|---------|----------------|
| CU-Erweiterungen | [**Echtzeitbewertung** ](real-time-scoring.md) basiert auf systemeigene C++-Bibliotheken zum Lesen eines Modells in einem optimierten Binärformat gespeichert und anschließend Vorhersagen generieren, ohne die R-Laufzeit aufrufen zu müssen. Dadurch wird die Bewertung Vorgänge wesentlich schneller. Sie können mit echtzeitbewertung, führen eine gespeicherte Prozedur oder ausführen echtzeitbewertung aus R-Code. Echtzeitbewertung ist auch für SQL Server 2016 verfügbar, wenn die Instanz, auf die neueste Version von aktualisiert wird [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
| Erste Veröffentlichung | [**R-Integration für in-Database-Analyse**](r/sql-server-r-services.md). <br/><br/> R-Pakete für die aufrufende R-Funktionen in T-SQL (und umgekehrt). RevoScaleR-Funktionen geben R-Analysen nach Maß durch Segmentieren der Daten in Komponenten, Koordination und Verwaltung verteilte Verarbeitung und Aggregieren der Ergebnisse. In SQL Server 2016 R Services (Datenbankintern) wird die RevoScaleR-Engine mit einer Datenbank-Engine-Instanz, sind die Daten und Analysen, die zusammen in demselben Verarbeitungskontext integriert. <br/><br/>T-SQL und R-Integration durch [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Sie können eine beliebige R-Code, der mit dieser gespeicherten Prozedur aufrufen. Diese sichere Infrastruktur ermöglicht die Bereitstellung der Unternehmensklasse Rn-Modelle und Skripts, die aus einer Anwendung mit einer einfachen gespeicherten Prozedur aufgerufen werden können. Zusätzliche Leistungsgewinne werden durch Streamen von Daten aus SQL in R-Prozessen und MPI-ringparallelisierung erreicht. <br/><br/>Können Sie das T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) Funktion ausführen [nativen Bewertung](sql-native-scoring.md) auf ein vortrainiertes Modell, das zuvor in das erforderliche Binärformat gespeichert wurde.|

## <a name="linux-support-roadmap"></a>Roadmap für die Linux-Unterstützung

2019 CTP 2.3 von SQL Server fügt Linux-Unterstützung für R, Python und Java, bei der Installation der Machine learning-Pakete mit einer Datenbank-Engine-Instanz. Weitere Informationen finden Sie unter [Installieren von SQL Server Machine Learning Services unter Linux](../linux/sql-server-linux-setup-machine-learning.md).

Unter Linux, SQL Server 2017 verfügt nicht über R oder Python-Integration, aber Sie können [nativen Bewertung](sql-native-scoring.md) unter Linux, da diese Funktion über T-SQL verfügbar ist [PREDICT](../t-sql/queries/predict-transact-sql.md), die unter Linux ausgeführt wird. Nativen Bewertung können leistungsstarke Bewertungen aus einem vorab trainierten Modell ohne aufrufen oder sogar müssen eine R-Laufzeit.

<a name="azure-sql-database-roadmap"></a>

## <a name="machine-learning-services-in-azure-sql-database"></a>Machine Learning-Dienste in Azure SQL-Datenbank

Machine Learning-Dienste (mit R) in Azure SQL-Datenbank ist in der öffentlichen Vorschau. Weitere Informationen finden Sie unter [Schnellstart: Verwenden von Machine Learning Services (mit R) in Azure SQL-Datenbank (Vorschau)](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-r).

## <a name="next-steps"></a>Nächste Schritte

+ [Installieren von SQL Server 2017-Machine Learning-Dienste (Datenbankintern)](install/sql-machine-learning-services-windows-install.md)
+ [Machine Learning-Tutorials und Beispiele](tutorials/machine-learning-services-tutorials.md)
