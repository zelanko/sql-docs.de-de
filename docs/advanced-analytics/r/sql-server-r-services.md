---
title: R Services in SQL Server 2016
description: R in SQL Server für integrierte R-Aufgaben für relationale Daten, einschließlich Data Science und statistischen Modellierung, Predictive Analytics, Datenvisualisierung und mehr.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/10/2018
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: e849140125ba39c7c1d8601c5ef32880a9d633ac
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344836"
---
# <a name="r-services-in-sql-server-2016"></a>R Services in SQL Server 2016
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R Services ist ein Add-on für eine SQL Server 2016-Datenbank-Engine-Instanz, die zum Ausführen von R-Code und Funktionen auf SQL Server verwendet wird. Der Code wird in einem Erweiterbarkeits Framework ausgeführt, das von Kern Modul Prozessen isoliert ist, aber vollständig für relationale Daten als gespeicherte Prozeduren, als T-SQL-Skript mit r-Anweisungen oder als R-Code mit t-SQL verfügbar ist. 

R Services beinhaltet eine grundlegende Verteilung von r, überlagert mit Enterprise R-Paketen von Microsoft, sodass Sie große Datenmengen auf mehreren Kernen laden und verarbeiten und die Ergebnisse in einer einzigen konsolidierten Ausgabe aggregieren können. Die R-Funktionen und-Algorithmen von Microsoft sind sowohl für die Skalierung als auch das Hilfsprogramm konzipiert: Bereitstellung von Predictive Analytics, statistischen Modellierung, Datenvisualisierungen und führenden Machine Learning-Algorithmen in einem kommerziellen Server Produkt, das entwickelt wurde und von Microsoft unterstützt. 

R-Bibliotheken enthalten [**revoscaler**](ref-r-revoscaler.md), [**microsoftml (r)** ](ref-r-microsoftml.md)und andere. Da R Services in die Datenbank-Engine integriert ist, können Sie Analysen in der Nähe der Daten aufbewahren und die Kosten und Sicherheitsrisiken, die mit der Daten Verschiebung verbunden sind, vermeiden.

> [!Note]
> R Services wurde in SQL Server 2017 und höher umbenannt, um [Machine Learning Services SQL Server](../what-is-sql-server-machine-learning.md), was das Hinzufügen von python widerspiegelt.

## <a name="components"></a>Komponenten

SQL Server 2016 ist nur R. In der folgenden Tabelle werden die Features in SQL Server 2016 beschrieben.

| Komponente | Beschreibung |
|-----------|-------------|
| SQL Server-Launchpad-Dienst | Ein Dienst, der die Kommunikation zwischen den externen R-Laufzeiten und der SQL Server Instanz verwaltet. |
| R-Pakete | [**Revoscaler**](ref-r-revoscaler.md) ist die primäre Bibliothek für skalierbare R. Funktionen in dieser Bibliothek gehören zu den am häufigsten verwendeten Funktionen. In diesen Bibliotheken finden Sie Daten Transformationen und-Manipulation, statistische Zusammenfassung, Visualisierung und viele Formen der Modellierung und Analyse. Außerdem verteilen Funktionen in diesen Bibliotheken Workloads automatisch auf verfügbare Kerne für die parallele Verarbeitung, mit der Möglichkeit, an Datenblöcken zu arbeiten, die von der Berechnungs-Engine koordiniert und verwaltet werden.  <br/>[**Microsoftml (R)** ](ref-r-microsoftml.md) fügt Machine Learning-Algorithmen hinzu, um benutzerdefinierte Modelle für die Textanalyse, die Bildanalyse und die Stimmungs Analyse zu erstellen. <br/>[**sqlrutils**](ref-r-sqlrutils.md) stellt Hilfsfunktionen für das Einfügen von R-Skripts in eine gespeicherte T-SQL-Prozedur, das Registrieren einer gespeicherten Prozedur in einer Datenbank und das Ausführen der gespeicherten Prozedur aus einer R-Entwicklungsumgebung bereit.<br/>[**olapr**](ref-r-olapr.md) dient zum Angeben von MDX-Abfragen in R.|
| Microsoft R Open (MRO) | [**MRO**](https://mran.microsoft.com/open) ist die Open Source-Verteilung von R von Microsoft. Das Paket und der Interpreter sind eingeschlossen. Verwenden Sie immer die von Setup installierte MRO-Version. |
| R-Tools | R-Konsolenfenster und Eingabe Aufforderungen sind Standard Tools in einer R-Distribution.  |
| R-Beispiele und-Skripts |  Open-Source-R-und revoscaler-Pakete enthalten integrierte Datasets, damit Sie mithilfe vorinstallierter Daten Skripts erstellen und ausführen können. |
| Vortrainierte Modelle in R | Vorab trainierte Modelle werden für bestimmte Anwendungsfälle erstellt und vom Data Science Engineering-Team bei Microsoft verwaltet. Mit den von Ihnen bereitgestellten neuen Dateneingaben können Sie die vorab trainierten Modelle unverändert verwenden, um positive negative Stimmungen in Text zu bewerten oder Features in Bildern zu erkennen. Die Modelle werden in R Services ausgeführt, können jedoch nicht über SQL Server-Setup installiert werden. Weitere Informationen finden Sie unter [Installieren von vorab trainierten Machine Learning-Modellen auf SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-r-services"></a>Verwenden von R Services

Entwickler und Analysten verfügen häufig über Code, der auf einer lokalen SQL Server-Instanz ausgeführt wird. Indem Sie Machine Learning Services hinzufügen und die Ausführung externer Skripts aktivieren, erhalten Sie die Möglichkeit, R-Code in SQL Server Modalitäten auszuführen: das Umwickeln von Skripts in gespeicherten Prozeduren, das Speichern von Modellen in einer SQL Server Tabelle oder das Kombinieren von T-SQL und R-Funktionen

Der gängigste Ansatz für Daten bankübergreifende Analysen ist die Verwendung von [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)und die Übergabe des R-Skripts als Eingabeparameter.

Klassische Client-Server-Interaktionen sind ein weiterer Ansatz. Auf jeder Client Arbeitsstation mit einer IDE können Sie [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)installieren und dann Code schreiben, der die Ausführung (als remotecomputekontext bezeichnet) auf Daten und Vorgänge an eine Remote SQL Server überträgt. 

Wenn Sie einen [eigenständigen Server](r-server-standalone.md) und die Developer Edition verwenden, können Sie mit denselben Bibliotheken und Interpretern Lösungen auf einer Client Arbeitsstation erstellen und dann Produktionscode auf SQL Server Machine Learning Services (Daten bankeigen) bereitstellen. 

## <a name="how-to-get-started"></a>Vorgehensweise beim Einstieg

Beginnen Sie mit dem Setup, fügen Sie die Binärdateien an Ihr bevorzugtes Entwicklungs Tool an, und schreiben Sie das erste Skript.

**Schritt 1:** Installieren und konfigurieren Sie die Software. 

+ [Installieren von SQL Server 2016 R Services (Daten bankeigen)](../install/sql-r-services-windows-install.md)

**Schritt 2:** Nutzen Sie eines der folgenden Tutorials, um praktische Erfahrungen zu sammeln:

+ [Tutorial: Erlernen von Daten bankbasierten Analysen mit R](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Tutorial: Exemplarische End-to-End-Exemplarische Vorgehensweise mit R](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

**Schritt 3:** Fügen Sie Ihre bevorzugten R-Pakete hinzu, und verwenden Sie Sie mit von Microsoft bereitgestellten Paketen.

+ [R-Paketverwaltung für SQL Server](install-additional-r-packages-on-sql-server.md)


## <a name="see-also"></a>Siehe auch

 [Installieren von SQL Server 2016 R-Diensten](../install/sql-r-services-windows-install.md)
