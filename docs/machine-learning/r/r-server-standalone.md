---
title: Was ist eine eigenständige Machine Learning Server- oder R Server-Instanz?
description: Lernen Sie die Unterschiede zwischen einem eigenständigen R Server und Machine Learning Server im SQL Server-Setup kennen.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 08/13/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 342c9bd2f83fed2b74cbce1f5ea7b7d942e9fd63
ms.sourcegitcommit: afb02c275b7c79fbd90fac4bfcfd92b00a399019
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91956911"
---
# <a name="what-are-standalone-machine-learning-server-or-r-server-in-sql-server"></a>Was ist eine eigenständige Machine Learning Server- oder R Server-Instanz in SQL Server?
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

SQL Server ermöglicht die Installation von eigenständigen R Server- bzw. Machine Learning Server-Instanzen, die unabhängig von SQL Server ausgeführt werden. Abhängig von Ihrer SQL Server-Version verfügt ein eigenständiger Server über die grundlegende Open-Source-Programmiersprache R und möglicherweise auch Python, die von leistungsstarken Microsoft-Bibliotheken überlagert werden, die Funktionen für Statistik- und Vorhersageanalysen in großem Umfang hinzufügen. Darüber hinaus ist es durch die Bibliotheken möglich, Machine Learning-Tasks in R oder Python auszuführen. 

In SQL Server 2016 heißt dieses Feature **R Server (Standalone)** und schließt nur R ein. In SQL Server 2017 wird dieses Feature **Machine Learning Server (eigenständig)** genannt und es umfasst R und Python.  

> [!Note]
> Der beim SQL Server-Setup installierte, eigenständige Server entspricht funktional den Nicht-SQL-Versionen von [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server), die dieselben Benutzerszenarios, wie Remoteausführung, Operationalisierung und Webdienste, sowie die komplette Sammlung von R- und Python-Bibliotheken unterstützen.

## <a name="components"></a>Komponenten

SQL Server 2016 unterstützt nur R. SQL Server-2017 unterstützt R und Python. In der folgenden Tabelle sind die in den einzelnen Versionen enthaltenen Features beschrieben.

| Komponente | BESCHREIBUNG |
|-----------|-------------|
| R-Pakete | [**RevoScaleR**](ref-r-revoscaler.md) ist die Hauptbibliothek für skalierbare R-Skripts mit Funktionen zur Datenmanipulation, -transformation, -visualisierung und -analyse.  <br/>[**MicrosoftML**](ref-r-microsoftml.md) stellt Machine Learning-Algorithmen zur Erstellung von benutzerdefinierten Modellen für die Text-, Bild- und Stimmungsanalyse bereit. <br/>[**sqlRUtils**](ref-r-sqlrutils.md) bietet Hilfsfunktionen zum Einfügen von R-Skripts in eine gespeicherte T-SQL-Prozedur, Registrieren dieser gespeicherten Prozedur bei einer Datenbank und Ausführen der gespeicherten Prozedur aus einer R-Entwicklungsumgebung.<br/>[**olapR**](ref-r-olapr.md) dient der Angabe von MDX-Abfragen in R.|
| Microsoft R Open (MRO) | [**MRO**](https://mran.microsoft.com/open) ist die Open-Source-Distribution für R von Microsoft. Das Paket und der Interpreter sind enthalten. Verwenden Sie immer die im Setup enthaltene Version von MRO. |
| R-Tools | Das R-Konsolenfenster und die Eingabeaufforderungen sind Standardtools in einer R-Distribution. Diese finden Sie unter \Programme\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| Beispiele und Skripts zu R |  R- und RevoScaleR-Open-Source-Pakete sind integrierte Datasets, sodass Sie Skripts mit vorinstallierten Daten erstellen und ausführen können. Suchen Sie unter \Programme\Microsoft SQL Server\140\R_SERVER\library\datasets and \library\RevoScaleR. |
| Python-Pakete | [**revoscalepy**](../python/ref-py-revoscalepy.md) ist die Hauptbibliothek für skalierbare Python-Skripts mit Funktionen zur Datenmanipulation, -transformation, -visualisierung und -analyse. <br/>[**microsoftml**](../python/ref-py-microsoftml.md) stellt Machine Learning-Algorithmen zur Erstellung von benutzerdefinierten Modellen für die Text-, Bild- und Stimmungsanalyse bereit.  |
| Python-Tools | Das integrierte Befehlszeilentool von Python ist für Ad-hoc-Tests und -Tasks sehr hilfreich. Sie finden das Tool unter \Programme\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda ist eine Open Source-Distribution von Python- und grundlegenden Paketen. |
| Beispiele und Skripts zu Python | Wie auch R umfasst Python integrierte Datasets und Skripts. Die revoscalepy-Daten finden Sie unter \Programme\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample-data. |
| Vorab trainierte Modelle in R und Python | Vorab trainierte Modelle werden für bestimmte Anwendungsfälle erstellt und vom Data Science-Entwicklungsteam bei Microsoft verwaltet. Mit den vorab trainierten Modellen können Sie mithilfe der von Ihnen bereitgestellten neuen Dateneingaben positive und negative Stimmungen im Text erfassen oder Merkmale in Bildern erkennen. Vorab trainierte Modelle werden unterstützt und können auf einem eigenständigen Server verwendet werden. Sie können Sie jedoch nicht über das SQL Server-Setup installieren. Weitere Informationen finden Sie unter [Install pretrained machine learning models on SQL Server (Installieren von vorab trainierten Machine Learning-Modellen in SQL Server)](../install/sql-pretrained-models-install.md). |

## <a name="using-a-standalone-server"></a>Verwenden eines eigenständigen Servers

R- und Python-Entwickler entscheiden sich in der Regel für einen eigenständigen Server, um die Speicher- und Verarbeitungsbeschränkungen der Open-Source-Produkte R und Python zu umgehen. R- und Python-Bibliotheken, die auf einem eigenständigen Server ausgeführt werden, können große Datenmengen in mehreren Kernen laden und verarbeiten und die Ergebnisse zu einer einzigen konsolidierten Ausgabe zusammenfassen. Die Hochleistungsfunktionen sind sowohl für Skalierbarkeit als auch für einen besseren Nutzen konzipiert: Sie liefern Vorhersageanalysen, statistische Modellierung, Datenvisualisierungen und modernste Machine Learning-Algorithmen in einem kommerziellen Serverprodukt, das von Microsoft entwickelt und unterstützt wird.

Da es sich um einen von SQL Server getrennten unabhängigen Server handelt, erfolgen Konfiguration, Sicherung und Zugriff auf R- und Python-Umgebungen mithilfe des zugrunde liegenden Betriebssystems und der Standardtools des eigenständigen Servers und nicht mit SQL Server. Es gibt keine integrierte Unterstützung für relationale SQL Server-Daten. Wenn Sie SQL Server-Daten verwenden möchten, können Sie Datenquellenobjekte und -verbindungen genauso wie von jedem anderen Client aus erstellen.

Als Ergänzung zu SQL Server ist ein eigenständiger Server auch als leistungsstarke Entwicklungsumgebung nützlich, wenn Sie sowohl lokales als auch Remotecomputing benötigen. Die R- und Python-Pakete auf einem eigenständigen Server entsprechen denen, die mit der Installation einer Datenbank-Engine bereitgestellt werden, wodurch Codeportabilität und [Computekontextwechsel](/machine-learning-server/r/concept-what-is-compute-context) ermöglicht werden.

## <a name="how-to-get-started"></a>Einstieg

Beginnen Sie mit dem Setup, fügen Sie die Binärdateien zu Ihrem bevorzugten Entwicklungstool hinzu, und schreiben Sie Ihr erstes Skript.

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der Software

Installieren Sie eine der folgenden Versionen:

+ [SQL Server 2017 Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (Standalone) – nur R](../install/sql-machine-learning-standalone-windows-install.md?view=sql-server-2016)

### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren eines Entwicklungstools

Auf einem eigenständigen Server ist es üblich, lokal mit einer auf dem gleichen Computer installierten Entwicklungsumgebung zu arbeiten.

+ [Einrichten von R-Tools](set-up-a-data-science-client.md)
+ [Einrichten von Python-Tools](../python/setup-python-client-tools-sql.md)

### <a name="step-3-write-your-first-script"></a>Schritt 3: Schreiben Ihres ersten Skripts

Schreiben Sie mithilfe von Funktionen aus revoscaler bzw. revoscalepy und den Machine Learning-Algorithmen ein R- oder Python-Skript.
  
  + [Erkunden von R und RevoScaleR in 25 Funktionen](/machine-learning-server/r/tutorial-r-to-revoscaler): Beginnen Sie mit grundlegenden R-Befehlen und wechseln Sie dann zu den verteilbaren Analysefunktionen von RevoScaleR, die eine hohe Leistung und Skalierung für R-Lösungen bereitstellen. Enthält parallelisierbare Versionen von vielen der beliebtesten R-Modellierpakete wie K-Means-Clustering, Entscheidungsstrukturen, Entscheidungswälder und Tools für die Datenbearbeitung.

  + [Schnellstart: An example of binary classification with the microsoftml Python package (Ein Beispiel für die binäre Klassifizierung mit dem microsoftml-Python-Paket)](/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): Erstellen Sie ein binäres Klassifizierungsmodell mit den Funktionen von microsoftml und dem bekannten Dataset für Brustkrebs.

Wählen Sie die für diese Aufgabe am besten geeignete Sprache aus. R ist für schwer mit SQL implementierbare statistische Berechnungen besser geeignet. Für satzbasierte Vorgänge zu Daten nutzen Sie die Leistungsfähigkeit von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], um die bestmöglichen Ergebnisse zu erzielen. Verwenden Sie die In-Memory-Database-Engine für sehr schnelle Berechnungen von Spalten.

### <a name="step-4-operationalize-your-solution"></a>Schritt 4: Operationalisieren der Lösung

Eigenständige Server können die Funktionalität zur [Operationalisierung](//machine-learning-server/what-is-operationalization) der Nicht-SQL-Instanz [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server) nutzen. Es ist möglich, einen eigenständigen Server für die Operationalisierung zu konfigurieren, wodurch Sie folgende Vorteile erhalten: Bereitstellung und Hosting Ihres Codes als Webdienst, Ausführung von Diagnosen und Testen der Webdienstleistung.

### <a name="step-5-maintain-your-server"></a>Schritt 5: Warten des Servers

Für SQL Server sind regelmäßig kumulative Updates verfügbar. Durch das Anwenden der kumulativen Updates auf eine vorhandene Installation werden daran zusätzliche Sicherheits- und Funktionserweiterungen vorgenommen. 

Beschreibungen neuer oder geänderter Funktionen finden Sie im Artikel [CAB-Downloads](../install/sql-ml-cab-downloads.md) und auf den Webseiten für [kumulative Updates für SQL Server 2016](https://support.microsoft.com/help/3177312/sql-server-2016-build-versions) und [kumulative Updates für SQL Server 2017](https://support.microsoft.com/help/4047329). 

Weitere Informationen zum Anwenden von Updates auf eine vorhandene Instanz finden Sie in der Installationsanleitung unter [Anwenden von Updates](../install/sql-machine-learning-standalone-windows-install.md#apply-cu).

## <a name="see-also"></a>Weitere Informationen

 [Installieren von Machine Learning Server (eigenständig) oder R Server (Standalone)](../install/sql-machine-learning-standalone-windows-install.md)