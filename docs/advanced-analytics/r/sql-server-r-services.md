---
title: R Services in SQLServer 2016 | Microsoft-Dokumentation
description: R in SQL Server für integrierte R-Aufgaben auf relationalen Daten, einschließlich Data Science- und statistische Modellierung, predictive Analytics, Visualisierung von Daten und mehr.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/10/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 17d0aa51d43ad9592a075ae91be88c857035b15f
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51659929"
---
# <a name="r-services-in-sql-server-2016"></a>R Services in SQLServer 2016
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R Services ist ein Add-on in eine SQL Server 2016-Datenbank-Engine-Instanz, für die Ausführung von R-Code und Funktionen in SQL Server verwendet. Code wird in einem Erweiterbarkeitsframework,, ausgeführt, von der Kern-Engine-Prozesse isoliert, jedoch vollständig auf relationale Daten als gespeicherte Prozeduren, wie T-SQL-Skript, die R-Anweisungen enthält oder als R-Code mit T-SQL verfügbar. 

R Services umfasst eine basisverteilung von R, zusammen mit Enterprise-R-Pakete von Microsoft, damit Sie laden und große Mengen von Daten auf mehreren Kernen verarbeiten und der Ergebnisse in eine einzelne, konsolidierte Ausgabe aggregieren können. Von Microsoft R-Funktionen und Algorithmen werden für sowohl Skalierung als auch Hilfsprogramm entwickelt: Bereitstellung von predictive Analytics, statistische Modellierung, datenvisualisierungen und fortschrittliche-Machine learning-Algorithmen in einer kommerziellen Serverprodukt konzipiert und von Microsoft unterstützt. 

R-Bibliotheken enthalten RevoScaleR, MicrosoftML und andere. Da R Services in der Datenbank-Engine integriert ist, können Sie Analysen in der Nähe der Daten und beseitigen, die Kosten und Sicherheitsrisiken bei der datenverschiebung.

> [!Note]
> R Services wurde umbenannt in SQL Server 2017 an [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md), das Hinzufügen von Python zu reflektieren.

## <a name="components"></a>Components

R wird nur von SQL Server 2016 ist. Die folgende Tabelle beschreibt die Funktionen in SQL Server 2016.

| Komponente | Description |
|-----------|-------------|
| SQL Server Launchpad-Dienst | Ein Dienst, der Kommunikation zwischen der externen R-Laufzeiten und SQL Server-Instanz verwaltet. |
| R-Pakete | [**RevoScaleR** ](revoscaler-overview.md) ist die primäre Bibliothek für skalierbare r-Funktionen in dieser Bibliothek auf die am häufigsten verwendeten sind. Datentransformationen und Manipulation, statistische Zusammenfassung, Visualisierung und viele Formen der Modellierung und Analysen werden in diesen Bibliotheken gefunden. Darüber hinaus verteilen Funktionen in diesen Bibliotheken automatisch Workloads auf verfügbaren Kerne für die parallele Verarbeitung, mit der Möglichkeit, die für Segmente der Daten zu arbeiten, die koordiniert und verwaltet werden, indem die berechnungs-Engine.  <br/>[**MicrosoftML (R)** ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen. <br/>[**SqlRUtils** ](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md) Stellt Hilfsfunktionen für das Einfügen von R-Skripts in einer gespeicherten T-SQL-Prozedur, eine gespeicherte Prozedur mit einer Datenbank registrieren und Ausführen der gespeicherten Prozedur aus einer R-Entwicklungsumgebung.<br/>[**OlapR** ](how-to-create-mdx-queries-using-olapr.md) dient zum Angeben von MDX-Abfragen in r|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open) ist die Open-Source-Distribution von R. Das Paket und ein Interpreter sind enthalten. Verwenden Sie immer die Version der MRO, die von Setup installiert. |
| R-tools | R-Konsole Windows und eingabeaufforderungen werden zu einer Verteilung von R-Standardtools.  |
| R-Beispiele und Skripts |  Open-Source-R und RevoScaleR-Pakete enthalten integrierte Datasets aus, sodass Sie erstellen und Ausführen von Skripts mit vorinstallierten Daten können |
| Vortrainierte Modelle in R | Vortrainierte Modelle sind für spezielle Anwendungsfälle von erstellt und verwaltet die Data Science engineering-Team bei Microsoft. Können Sie die vorab trainierte Modelle wie-besteht darin, eine Bewertung positiv Negative Stimmung im Text-Format oder Erkennen von Funktionen in Images können neue Dateneingaben, die Sie bereitstellen. Die Modelle in R Services ausgeführt, aber nicht über SQL Server-Setup installiert werden. Weitere Informationen finden Sie unter [installieren vorab trainierten Machine learning-Modelle in SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-r-services"></a>Verwenden von R Services

Entwickler und Wirtschaftsanalytiker verfügen häufig über Code, die auf einer lokalen SQL Server-Instanz ausgeführt wird. Hinzufügen von Machine Learning-Dienste aus, und Aktivieren der externen skriptausführung, erhalten Sie die Möglichkeit zum Ausführen von R-Code in SQL Server-Modalitäten: Umschließen von Skripts in gespeicherten Prozeduren, Speichern von Modellen in einer SQL Server-Tabelle oder Kombinieren von T-SQL und R-Funktionen in Abfragen.

Die am häufigsten verwendete Ansatz für in-Database-Analyse ist die Verwendung [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), R-Skript als Eingabeparameter übergeben.

Klassischen Client / Server-Interaktionen sind ein weiterer Ansatz. Von einer beliebigen Clientarbeitsstation, die über eine IDE verfügt, können Sie installieren [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client), und klicken Sie dann Code schreiben, der Ausführung überträgt (genannt eine *remotecomputekontext*) auf Daten und Vorgänge mit einer remote-SQL Server. 

Schließlich bei Verwendung einer [eigenständiger Server](r-server-standalone.md) und Developer Edition können Sie Lösungen auf einer Clientarbeitsstation, die mit demselben Interpreter und Bibliotheken erstellen und anschließend bereitstellen Produktionscode in SQL Server Machine Learning Dienste (Datenbankintern). 

## <a name="how-to-get-started"></a>Erste Schritte

Mit dem Setup starten Sie, fügen Sie die Binärdateien an Ihrem bevorzugten Entwicklungstool und Schreiben Sie das erste Skript.

**Schritt 1:** installieren und konfigurieren Sie die Software. 

+ [Installieren von SQL Server 2016 R Services (Datenbankintern)](../install/sql-r-services-windows-install.md)

**Schritt 2:** erhalten Sie praktische Erfahrungen mit einem der folgenden Tutorials:

+ [Tutorial: Erfahren Sie mehr in-Database-Analyse, die mithilfe von R](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Tutorial: End-to-End Walkthrough mit R](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

**Schritt 3:** Ihrer bevorzugten R-Pakete hinzufügen und verwenden Sie diese zusammen mit Paketen, die von Microsoft bereitgestellt werden

+ [R-paketverwaltung für SQL Server](install-additional-r-packages-on-sql-server.md)


## <a name="see-also"></a>Siehe auch

 [Installieren von SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
