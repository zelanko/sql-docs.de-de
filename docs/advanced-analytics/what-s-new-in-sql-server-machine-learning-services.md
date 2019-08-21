---
title: Neues
description: Neue Funktions Ankündigungen für jede Version von SQL Server 2016 R Services, R Server SQL Server Machine Learning Services.
ms.date: 08/21/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f582088359c2878f5dfd84d4b353b1f9d8c369e5
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652294"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Neues in SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Machine Learning-Funktionen werden SQL Server in jeder Version hinzugefügt, da wir die Integration zwischen der Datenplattform, der erweiterten Analyse und Data Science fortsetzen, erweitern und vertiefen. 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2019-preview"></a>Neu in SQL Server 2019 Preview

In dieser Version werden die oben angeforderten Features für R-und python Machine Learning-Vorgänge in SQL Server hinzugefügt. Weitere Informationen zu allen Features in dieser Version finden Sie unter [What es New in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) und [Release Notes for SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md).

> [!NOTE]
> Die Dokumentation zu den Neuerungen in Java in SQL Server 2019 finden Sie unter [What New in SQL Server Language Extensions?](https://docs.microsoft.com/sql/language-extensions/language-extensions-whats-new)

| Release | Funktions Update |
|---------|----------------|
| RC 1 | [Die Loopback Verbindung mit SQL Server von einem Python-oder R-Skript](connect/loopback-connection.md) wird jetzt sowohl für Windows als auch für Linux unterstützt. |
| CTP 3.2 | Keine Änderungen. |
| CTP 3.1 | Keine Änderungen. |
| CTP 3.0 | Keine Änderungen. |
| CTP 2.5 | Keine Änderungen. |
| CTP 2.4 | Linux-Unterstützung für [Create externe Library (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) für R und python. |
| CTP 2.3 | Nur unter Windows kann auf Python-Code in einer externen Bibliothek mithilfe der [Create externe Library-Anweisung (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) zugegriffen werden. |
| CTP 2.2 | Keine Änderungen. |
| CTP 2.1 | Keine Änderungen. |
| CTP 2.0 | Linux-Platt Form Unterstützung für R und python Machine Learning. Beginnen Sie mit [der Installation SQL Server Machine Learning Services unter Linux](../linux/sql-server-linux-setup-machine-learning.md). |
|  | [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) führt zwei neue Parameter ein, mit denen Sie problemlos mehrere Modelle aus partitionierten Daten generieren können. Weitere Informationen finden Sie in diesem Tutorial unter [Erstellen von Partitions basierten Modellen in R](tutorials/r-tutorial-create-models-per-partition.md). |
|   | Die Unterstützung von Failoverclustern wird jetzt unter Windows und Linux unterstützt, vorausgesetzt, SQL Server-Launchpad-Dienst auf allen Knoten gestartet wird. Weitere Informationen finden Sie unter [SQL Server](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)-Failoverclusterinstallation. |

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2017"></a>Neu in SQL Server 2017

Diese Version bietet [python-Unterstützung und branchenführende Machine Learning-Algorithmen](https://cloudblogs.microsoft.com/sqlserver/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/). In SQL Server 2017 wird die Einführung von [SQL Server Machine Learning Services (in-Database)](what-is-sql-server-machine-learning.md)mit Sprachunterstützung für python und R umbenannt, um den neuen Bereich widerzuspiegeln. 

Weitere Informationen zu featureankündigungen finden Sie unter [What es New in SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

### <a name="r-enhancements"></a>R-Erweiterungen

Bei der r-Komponente von SQL Server Machine Learning Services handelt es sich um die nächste Generation von SQL Server 2016 R Services mit aktualisierten Versionen von Base R, revoscaler und anderen Paketen.

Zu den neuen Funktionen von R zählen die [**Paketverwaltung**](r/install-additional-r-packages-on-sql-server.md)mit den folgenden Highlights: 

+ Daten bankrollen helfen DBAs bei der Verwaltung von Paketen und Zuweisen von Berechtigungen für die Paketinstallation.
+ [Create externe Library](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) unterstützt DBAs bei der Verwaltung von Paketen in der vertrauten T-SQL-Sprache.
+ Mithilfe von [revoscaler](r/use-revoscaler-to-manage-r-packages.md) -Funktionen können Sie Pakete installieren, entfernen oder auflisten, die Benutzer besitzen. Weitere Informationen [finden Sie unter Verwenden von revoscaler-Funktionen zum Suchen oder Installieren von R-Paketen auf SQL Server](r/use-revoscaler-to-manage-r-packages.md).

### <a name="r-libraries"></a>R-Bibliotheken

| Package | Beschreibung |
|---------|-------------|
| [**MicrosoftML**](r/ref-r-microsoftml.md) | In dieser Version ist microsoftml in eine Standard-r-Installation integriert, sodass der upgradeschritt entfällt, der in den vorherigen SQL Server 2016 R-Diensten erforderlich ist. Microsoftml bietet moderne Machine Learning-Algorithmen und Daten Transformationen, die in remotecomputekontexten skaliert oder ausgeführt werden können. Algorithmen umfassen anpassbare Deep Neural Networks, schnelle Entscheidungsstrukturen und Entscheidungs Gesamtstrukturen, lineare Regression und logistische Regression.  |

### <a name="python-integration-for-in-database-analytics"></a>Python-Integration für Daten bankübergreifende Analysen

Python ist eine Sprache, die für eine Vielzahl von Machine Learning-Aufgaben eine hohe Flexibilität und Leistungsfähigkeit bietet. Open-Source-Bibliotheken für python umfassen verschiedene Plattformen für anpassbare neuronale Netzwerke sowie beliebte Bibliotheken für die Verarbeitung natürlicher Sprache. 

Da python in die Datenbank-Engine integriert ist, können Sie Analysen in der Nähe der Daten aufbewahren und die Kosten und Sicherheitsrisiken, die mit der Daten Verschiebung verbunden sind, vermeiden. Sie können Machine Learning-Lösungen basierend auf python mithilfe von Tools wie Visual Studio bereitstellen. Ihre Produktionsanwendungen können mit SQL Server Datenzugriffs Methoden Vorhersagen, Modelle oder visuelle Elemente aus der Python 3,5-Laufzeit abrufen.

Die T-SQL-und python-Integration wird durch die gespeicherte System Prozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) unterstützt. Mit dieser gespeicherten Prozedur können Sie beliebigen Python-Code abrufen. Der Code wird in einer sicheren, dualen Architektur ausgeführt, die die Bereitstellung von python-Modellen und-Skripts auf Unternehmens Niveau ermöglicht und von einer Anwendung mithilfe einer einfachen gespeicherten Prozedur aufgerufen werden kann. Zusätzliche Leistungssteigerungen werden erzielt, indem Daten von SQL an python-Prozesse und MPI-Ring Parallelisierung gestreamt werden.

Sie können die T-SQL- [Vorhersage](../t-sql/queries/predict-transact-sql.md) Funktion verwenden, um eine [native Bewertung](sql-native-scoring.md) für ein vorab trainiertes Modell auszuführen, das zuvor im erforderlichen Binärformat gespeichert wurde.

### <a name="python-libraries"></a>Python-Bibliotheken

| Package | Beschreibung |
|---------|-------------|
|[**revoscalepy**](python/ref-py-revoscalepy.md)| Python-Äquivalent von revoscaler. Sie können python-Modelle für lineare und logistische Regressionen, Entscheidungsstrukturen, verstärkte Strukturen und zufällige Gesamtstrukturen erstellen, die alle parallelisierbar sind und in remotecomputekontexten ausgeführt werden können. Dieses Paket unterstützt die Verwendung mehrerer Datenquellen und remotecomputekontexte. Der Daten Analyst oder Entwickler kann Python-Code auf einem Remote SQL Server ausführen, um Daten zu durchsuchen oder Modelle zu erstellen, ohne Daten zu verschieben. |
|[**microsoftml**](python/ref-py-microsoftml.md) |Python-Entsprechung des microsoftml-R-Pakets. |

### <a name="pre-trained-models"></a>Vortrainierte Modelle

[**Vorab trainierte Modelle**](install/sql-pretrained-models-install.md) sind sowohl für python als auch für R verfügbar. verwenden Sie diese Modelle für die Bild Erkennung und positive negative Stimmungs Analyse, um Vorhersagen für Ihre eigenen Daten zu generieren. 

### <a name="standalone-server-as-a-shared-feature-in-sql-server-setup"></a>Eigenständiger Server als frei gegebenes Feature in SQL Server-Setup

Diese Version bietet auch [SQL Server Machine Learning Server (eigenständig)](r/r-server-standalone.md), einen vollständig unabhängigen Data Science Server, der statistische und Predictive Analytics in R und python unterstützt. Wie bei R Services ist dieser Server die nächste Version von SQL Server 2016 R Server (eigenständig). Mit dem eigenständigen Server können Sie R-oder python-Lösungen ohne Abhängigkeiten von SQL Server verteilen und skalieren.
::: moniker-end

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2016"></a>Neu in SQL Server 2016

In dieser Version wurden Machine Learning-Funktionen in SQL Server über **SQL Server 2016 R Services**eingeführt, eine Datenbankanalyse-Engine für die Verarbeitung von R-Skripts in Residenten Daten innerhalb einer Datenbank-Engine-Instanz.

Außerdem wurde **SQL Server 2016 R Server (eigenständig)** als Möglichkeit zur Installation von R Server auf einem Windows-Server freigegeben. Anfänglich hat SQL Server-Setup die einzige Möglichkeit bereitgestellt, R Server für Windows zu installieren. In späteren Versionen konnten Entwickler und Datenanalysten, die R Server unter Windows wollten, ein anderes eigenständiges Installationsprogramm verwenden, um das gleiche Ziel zu erreichen. Der eigenständige Server in SQL Server ist funktional äquivalent zum eigenständigen Server Produkt, [Microsoft R Server für Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Weitere Informationen zu featureankündigungen finden Sie unter [What es New in SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md).

| Release |Funktions Update |
|---------|----------------|
| Cu-Ergänzungen | Die [**Echtzeitbewertung**](real-time-scoring.md) basiert auf nativen C++ Bibliotheken, um ein in einem optimierten Binärformat gespeichertes Modell zu lesen und dann Vorhersagen zu generieren, ohne die R-Laufzeit aufrufen zu müssen. Dadurch werden Bewertungs Vorgänge erheblich beschleunigt. Mit der Echtzeitbewertung können Sie eine gespeicherte Prozedur ausführen oder die Echtzeitbewertung aus R-Code durchführen. Die Echtzeitbewertung ist auch für SQL Server 2016 verfügbar, wenn für die Instanz ein Upgrade auf die neueste Version [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]von durchgeführt wurde. |
| Erste Veröffentlichung | [**R-Integration für in-Database-Analysen**](r/sql-server-r-services.md). <br/><br/> R-Pakete zum Aufrufen von r-Funktionen in T-SQL und umgekehrt. Mithilfe von revoscaler-Funktionen können R-Analysen skaliert werden, indem Daten in Komponenten Teile aufgeteilt werden, verteilte Verarbeitung koordiniert und verwaltet wird und Ergebnisse aggregierte werden. In SQL Server 2016 R Services (in-Database) ist die revoscaler-Engine in eine Instanz der Datenbank-Engine integriert, sodass Daten und Analysen im gleichen Verarbeitungs Kontext zusammengefasst werden. <br/><br/>T-SQL-und R-Integration über [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Mit dieser gespeicherten Prozedur können Sie jeden beliebigen R-Code abrufen. Diese sichere Infrastruktur ermöglicht die Bereitstellung von RN-Modellen und-Skripts auf Unternehmens Niveau, die mithilfe einer einfachen gespeicherten Prozedur von einer Anwendung aufgerufen werden können. Zusätzliche Leistungssteigerungen werden erzielt, indem Daten von SQL zu R-Prozessen und MPI-Ring Parallelisierung gestreamt werden. <br/><br/>Sie können die T-SQL- [Vorhersage](../t-sql/queries/predict-transact-sql.md) Funktion verwenden, um eine [native Bewertung](sql-native-scoring.md) für ein vorab trainiertes Modell auszuführen, das zuvor im erforderlichen Binärformat gespeichert wurde.|

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="linux-support"></a>Linux-Unterstützung

SQL Server 2019 fügt die Linux-Unterstützung für R und python hinzu, wenn Sie die Machine Learning-Pakete mit einer Datenbank-Engine-Instanz installieren. Weitere Informationen finden Sie unter [Installieren von SQL Server Machine Learning Services unter Linux](../linux/sql-server-linux-setup-machine-learning.md).

Unter Linux verfügt SQL Server 2017 nicht über R-oder python-Integration, Sie können jedoch die [native Bewertung](sql-native-scoring.md) unter Linux verwenden, da diese Funktionalität über die T-SQL- [Vorhersage](../t-sql/queries/predict-transact-sql.md)verfügbar ist, die unter Linux ausgeführt wird. Die native Bewertung ermöglicht eine Bewertung mit hoher Leistung aus einem vorab trainierten Modell, ohne dass aufgerufen wird oder eine R-Laufzeit benötigt wird.
::: moniker-end

<a name="azure-sql-database-roadmap"></a>

## <a name="machine-learning-services-in-azure-sql-database"></a>Machine Learning Services in Azure SQL-Datenbank

Machine Learning Services in Azure SQL-Datenbank befindet sich in der öffentlichen Vorschau Phase. Weitere Informationen finden Sie unter [Azure SQL-Datenbank-Machine Learning Services (Vorschau)](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview).

## <a name="next-steps"></a>Nächste Schritte

+ [Installieren von SQL Server Machine Learning Services (Daten bankeigen)](install/sql-machine-learning-services-windows-install.md)
+ [Tutorials und Beispiele für Machine Learning](tutorials/machine-learning-services-tutorials.md)
