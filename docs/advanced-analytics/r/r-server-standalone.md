---
title: Standalone R Server oder Machine Learning Server-Installation – SQL Server Machine Learning Services
description: Übersicht über die Einführung in eigenständigen R Servers und Machine Learning-Server in SQL Server-Setup
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: overview
author: dphansen
ms.author: davidph
ms.openlocfilehash: 407a4c87101b2d422afbb982c7a07d92e84d26f1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962510"
---
# <a name="r-server-standalone-and-machine-learning-server-standalone-in-sql-server"></a>R Server (eigenständig) "und" Machine Learning Server (eigenständig) in SQLServer
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server bietet Unterstützung der Installation für einen eigenständigen R-Server oder Machine Learning-Server, die unabhängig von SQL Server ausgeführt wird. Abhängig von Ihrer SQL Server-Version weist ein eigenständigen Server eine Grundlage für Open-Source-Sprache R und eventuell auch Python, zusammen mit hoher Leistung-Bibliotheken von Microsoft, die statistische und predictive Analytics zur Skalierung hinzufügen. Bibliotheken ermöglichen außerdem die Machine Learning-Tasks, die in die Skripterstellung in R oder Python. 

In SQL Server 2016 kann dieses Feature heißt **R Server (eigenständig)** und ist nur für R. In SQL Server 2017 heißt es **Machine Learning Server (eigenständig)** sowie R und Python.  

> [!Note]
> Wie von SQL Server-Setup installiert, ist ein eigenständiger Server funktionell gleichwertig mit der nicht-SQL-Versionen unter dem Markennamen [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), unterstützen die gleichen Benutzerszenarien, einschließlich der Remoteausführung, operationalisierung und Webdienste, und die vollständige Auflistung von R und Python-Bibliotheken.

## <a name="components"></a>Komponenten

R wird nur von SQL Server 2016 ist. SQL Server-2017 unterstützt R und Python. Die folgende Tabelle beschreibt die Funktionen in der jeweiligen Version.

| Komponente | Beschreibung |
|-----------|-------------|
| R-Pakete | [**RevoScaleR** ](ref-r-revoscaler.md) ist die primäre Bibliothek für skalierbare R mit Funktionen zur datenbearbeitung, Transformation, Visualisierung und Analyse.  <br/>[**MicrosoftML** ](ref-r-microsoftml.md) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen. <br/>[**SqlRUtils** ](ref-r-sqlrutils.md) Stellt Hilfsfunktionen für das Einfügen von R-Skripts in einer gespeicherten T-SQL-Prozedur, eine gespeicherte Prozedur mit einer Datenbank registrieren und Ausführen der gespeicherten Prozedur aus einer R-Entwicklungsumgebung.<br/>[**Mrsdeploy** ](operationalization-with-mrsdeploy.md) bietet web-Service-Bereitstellung (in nur SQL Server 2017). <br/>[**OlapR** ](ref-r-olapr.md) dient zum Angeben von MDX-Abfragen in r|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open) ist die Open-Source-Distribution von R. Das Paket und ein Interpreter sind enthalten. Verwenden Sie immer die Version der MRO Setup gebündelt. |
| R-tools | R-Konsole Windows und eingabeaufforderungen werden zu einer Verteilung von R-Standardtools. Finden sie unter \Programme\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| R-Beispiele und Skripts |  Open-Source-R und RevoScaleR-Pakete enthalten die integrierten Datasets, damit Sie erstellen und Ausführen von Skripts mit vorinstallierten Daten können. Suchen Sie unter \Programme\Microsoft SQL Server\140\R_SERVER\library\datasets und \library\RevoScaleR. |
| Python-Pakete | [**die Revoscalepy** ](../python/ref-py-revoscalepy.md) ist die primäre Bibliothek für skalierbare Python mit Funktionen zur datenbearbeitung, Transformation, Visualisierung und Analyse. <br/>[**Microsoftml** ](../python/ref-py-microsoftml.md) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen.  |
| Python-tools | Die integrierten Python-Befehlszeilentool eignet sich für ad-hoc-Tests und Aufgaben. Suchen Sie das Tool im Verzeichnis \Programme\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda ist ein Open-Source-Distribution von Python und essential-Pakete. |
| Python-Beispiele und Skripts | Enthält wie bei R, Python, integrierten Datasets und Skripts. Suchen Sie die Revoscalepy-Daten unter \Programme\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-Packages\revoscalepy\data\sample-Daten. |
| Vortrainierte Modelle in R und Python | Vortrainierte Modelle sind für spezielle Anwendungsfälle von erstellt und verwaltet die Data Science engineering-Team bei Microsoft. Können Sie die vorab trainierte Modelle wie-besteht darin, eine Bewertung positiv Negative Stimmung im Text-Format oder Erkennen von Funktionen in Images können neue Dateneingaben, die Sie bereitstellen. Vortrainierte Modelle werden unterstützt und auf einem eigenständigen Server verwendet werden, aber sie kann nicht über SQL Server-Setup installiert werden. Weitere Informationen finden Sie unter [Installation vorab Machine Learning-Modelle in SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-a-standalone-server"></a>Verwenden einen eigenständigen server

R und Python-Entwickler wählen Sie in der Regel auf einen eigenständigen Server über den Arbeitsspeicher und verarbeitungsleistung Einschränkungen von Open-Source-Sprache R und Python zu verschieben. R und Python-Bibliotheken, die auf einem eigenständigen Server ausführen können zu laden und verarbeiten große Mengen von Daten auf mehreren Kernen und Aggregieren der Ergebnisse in eine einzelne, konsolidierte Ausgabe. Hochleistungs-Funktionen werden für sowohl Skalierung als auch Hilfsprogramm entwickelt: Bereitstellung von predictive Analytics, statistische Modellierung, datenvisualisierungen und fortschrittliche-Machine learning-Algorithmen in einer kommerziellen Serverprodukt konzipiert und unterstützt von Von Microsoft.

Als unabhängige-Server von SQL Server entkoppelt ist die R- und Python-Umgebung, gesicherte und zugegriffen, mit dem zugrunde liegenden Betriebssystem und den standard in der eigenständige Server, nicht auf SQL Server bereitgestellten Tools konfiguriert. Es gibt keine integrierte Unterstützung für relationale SQL Server-Daten. Wenn Sie SQL Server-Daten verwenden möchten, können Sie von Datenquellenobjekten und Verbindungen erstellen, wie Sie von jedem Client aus.

Als Ergänzung zum SQL Server ist ein eigenständiger Server auch als eine leistungsstarke Entwicklungsumgebung nützlich, bei Bedarf sowohl lokale als auch remote computing. Die R und Python-Pakete auf einem eigenständigen Server entsprechen denen, die mit einer Datenbank-Engine-Installation ermöglicht Codeportabilität und [Compute-Kontextwechsel](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

## <a name="how-to-get-started"></a>Erste Schritte

Mit dem Setup starten Sie, fügen Sie die Binärdateien an Ihrem bevorzugten Entwicklungstool und Schreiben Sie das erste Skript.

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der software

Installieren Sie entweder eine dieser Versionen:

+ [SQL Server 2017-Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016-R-Server (eigenständig) – nur R](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren Sie ein Entwicklungstool

Auf einem eigenständigen Server ist es üblich, arbeiten lokal mit einer Entwicklung auf dem gleichen Computer installiert.

+ [Einrichten von R-Tools](set-up-a-data-science-client.md)
+ [Einrichten von Python-Tools](../python/setup-python-client-tools-sql.md)

### <a name="step-3-write-your-first-script"></a>Schritt 3: Das erste Skript schreiben

Schreiben Sie R- oder Python-Skript, die mithilfe der Funktionen von RevoScaleR, Revoscalepy und Machine learning-Algorithmen.
  
  + [Erkunden von R und RevoScaleR in 25 Funktionen](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): Beginnen Sie mit einfachen R-Befehlen und arbeiten Sie sich dann um die RevoScaleR verteilbaren analytischen Funktionen, die hohe Leistung und Skalierung für R-Lösungen bereitstellen. Enthält parallelisierbare Versionen von vielen der beliebtesten R-Modellierpakete wie K-Means-Clustering, Entscheidungsstrukturen, Entscheidungswälder und Tools für die Datenbearbeitung.

  + [Schnellstart: Ein Beispiel für binäre Klassifizierung mit dem Python-Paket Microsoftml](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): Ein binäres klassifizierungsmodell mithilfe der Funktionen von Microsoftml und das bekannte Breast Cancer Dataset zu erstellen.

Wählen Sie die beste Sprache für den Task. R ist am besten für statistische Berechnungen, die mit SQL schwierig sind. Nutzen Sie für setbasierte Vorgänge für Daten, die die Leistungsfähigkeit des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um maximale Leistung zu erzielen. Verwenden Sie die in-Memory-Datenbank-Engine für sehr schnelle Berechnungen über Spalten hinweg.

### <a name="step-4-operationalize-your-solution"></a>Schritt 4: Operationalisieren Sie Ihre Lösung

Eigenständige Server können die [operationalisierung](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) Funktionalität von der SQL-markenfreien [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Sie können konfigurieren, einen eigenständigen Server für die operationalisierung, wodurch Sie die folgenden Vorteile: Bereitstellen und hosten Sie Ihren Code ein, wie Webdienste, führen Sie Diagnosen, Web-Servicekapazität testen.

### <a name="step-5-maintain-your-server"></a>Schritt 5: Verwalten Sie Ihrer server

SQL Server-Versionen kumulativen Updates in regelmäßigen Abständen. Anwenden von kumulativen Updates hinzugefügt Sicherheits- und funktionale Verbesserungen einer vorhandenen Installation. 

Beschreibung der neuen oder geänderten Funktionen finden Sie in der [CAB-Downloads](../install/sql-ml-cab-downloads.md) Artikel und auf den Webseiten für [kumulativen Updates für SQL Server 2016](https://support.microsoft.com/help/3177312/sql-server-2016-build-versions) und [kumulativen Updates für SQL Server 2017 ](https://support.microsoft.com/help/4047329). 

Weitere Informationen zum Anwenden von Updates zu einer vorhandenen Instanz finden Sie unter [Anwenden von Updates](../install/sql-machine-learning-standalone-windows-install.md#apply-cu) in den installationsanweisungen.

## <a name="see-also"></a>Siehe auch

 [Installieren von R Server (eigenständig) oder Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md)

