---
title: Standalone R Server oder Machine Learning Server-Installation in SQL Server | Microsoft-Dokumentation
description: Übersicht über die Einführung in eigenständigen R Servers und Machine Learning-Server in SQL Server-Setup
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/01/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9cb0cecaef28d512cf36e694344e62b01df88ebf
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657499"
---
# <a name="r-server-standalone-and-machine-learning-server-standalone-in-sql-server"></a>R Server (eigenständig) "und" Machine Learning Server (eigenständig) in SQLServer
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server bietet Unterstützung der Installation für einen eigenständigen R-Server oder Machine Learning-Server, die unabhängig von SQL Server ausgeführt wird. Abhängig von Ihrer SQL Server-Version weist ein eigenständigen Server eine Grundlage für Open-Source-Sprache R und eventuell auch Python, zusammen mit hoher Leistung-Bibliotheken von Microsoft, die statistische und predictive Analytics zur Skalierung hinzufügen. Bibliotheken ermöglichen außerdem die Machine Learning-Tasks, die in die Skripterstellung in R oder Python. 

In SQL Server 2016 kann dieses Feature heißt **R Server (eigenständig)** und ist nur für R. In SQL Server 2017 heißt es **Machine Learning Server (eigenständig)** sowie R und Python.  

> [!Note]
> Wie von SQL Server-Setup installiert, ist ein eigenständiger Server funktionell gleichwertig mit der nicht-SQL-Versionen unter dem Markennamen [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), unterstützen die gleichen Benutzerszenarien, einschließlich der Remoteausführung, operationalisierung und Webdienste, und die vollständige Auflistung von R und Python-Bibliotheken.

## <a name="components"></a>Components

R wird nur von SQL Server 2016 ist. SQL Server-2017 unterstützt R und Python. Die folgende Tabelle beschreibt die Funktionen in der jeweiligen Version.

| Komponente | Description |
|-----------|-------------|
| R-Pakete | [**RevoScaleR** ](revoscaler-overview.md) ist die primäre Bibliothek für skalierbare R mit Funktionen zur datenbearbeitung, Transformation, Visualisierung und Analyse.  <br/>[**MicrosoftML** ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen. <br/>[**SqlRUtils** ](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md) Stellt Hilfsfunktionen für das Einfügen von R-Skripts in einer gespeicherten T-SQL-Prozedur, eine gespeicherte Prozedur mit einer Datenbank registrieren und Ausführen der gespeicherten Prozedur aus einer R-Entwicklungsumgebung.<br/>[**Mrsdeploy** ](operationalization-with-mrsdeploy.md) bietet web-Service-Bereitstellung (in nur SQL Server 2017). <br/>[**OlapR** ](how-to-create-mdx-queries-using-olapr.md) dient zum Angeben von MDX-Abfragen in r|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open) ist die Open-Source-Distribution von R. Das Paket und ein Interpreter sind enthalten. Verwenden Sie immer die Version der MRO Setup gebündelt. |
| R-tools | R-Konsole Windows und eingabeaufforderungen werden zu einer Verteilung von R-Standardtools. Finden sie unter \Programme\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| R-Beispiele und Skripts |  Open-Source-R und RevoScaleR-Pakete enthalten die integrierten Datasets, damit Sie erstellen und Ausführen von Skripts mit vorinstallierten Daten können. Suchen Sie unter \Programme\Microsoft SQL Server\140\R_SERVER\library\datasets und \library\RevoScaleR. |
| Python-Pakete | [**die Revoscalepy** ](../python/what-is-revoscalepy.md) ist die primäre Bibliothek für skalierbare Python mit Funktionen zur datenbearbeitung, Transformation, Visualisierung und Analyse. <br/>[**Microsoftml** ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen.  |
| Python-tools | Das integrierte Tool der Python-Befehlszeile eignet sich für ad-hoc-Tests und Aufgaben. Suchen Sie das Tool im Verzeichnis \Programme\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda ist ein Open-Source-Distribution von Python und essential-Pakete. |
| Python-Beispiele und Skripts | Enthält wie bei R, Python, integrierten Datasets und Skripts. Suchen Sie die Revoscalepy-Daten unter \Programme\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-Packages\revoscalepy\data\sample-Daten. |
| Vortrainierte Modelle in R und Python | Vortrainierte Modelle sind für spezielle Anwendungsfälle von erstellt und verwaltet die Data Science engineering-Team bei Microsoft. Können Sie die vorab trainierte Modelle wie-besteht darin, eine Bewertung positiv Negative Stimmung im Text-Format oder Erkennen von Funktionen in Images können neue Dateneingaben, die Sie bereitstellen. Vortrainierte Modelle werden unterstützt und auf einem eigenständigen Server verwendet werden, aber sie kann nicht über SQL Server-Setup installiert werden. Weitere Informationen finden Sie unter [Installation vorab Machine Learning-Modelle in SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-a-standalone-server"></a>Verwenden einen eigenständigen server

R und Python-Entwickler wählen Sie in der Regel auf einen eigenständigen Server über den Arbeitsspeicher und verarbeitungsleistung Einschränkungen von Open-Source-Sprache R und Python zu verschieben. R und Python-Bibliotheken, die auf einem eigenständigen Server ausführen können zu laden und verarbeiten große Mengen von Daten auf mehreren Kernen und Aggregieren der Ergebnisse in eine einzelne, konsolidierte Ausgabe. Hochleistungs-Funktionen werden für sowohl Skalierung als auch Hilfsprogramm entwickelt: Bereitstellung von predictive Analytics, statistische Modellierung, datenvisualisierungen und fortschrittliche-Machine learning-Algorithmen in einer kommerziellen Serverprodukt konzipiert und unterstützt von Von Microsoft.

Als unabhängige-Server von SQL Server entkoppelt ist die R- und Python-Umgebung, gesicherte und zugegriffen, mit dem zugrunde liegenden Betriebssystem und den standard in der eigenständige Server, nicht auf SQL Server bereitgestellten Tools konfiguriert. Es gibt keine integrierte Unterstützung für relationale SQL Server-Daten. Wenn Sie SQL Server-Daten verwenden möchten, können Sie von Datenquellenobjekten und Verbindungen erstellen, wie Sie von jedem Client aus.

Als Ergänzung zum SQL Server ist ein eigenständiger Server auch als eine leistungsstarke Entwicklungsumgebung nützlich, bei Bedarf sowohl lokale als auch remote computing. Die R und Python-Pakete auf einem eigenständigen Server entsprechen denen, die mit einer Datenbank-Engine-Installation ermöglicht Codeportabilität und [Compute-Kontextwechsel](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

## <a name="how-to-get-started"></a>Erste Schritte

Mit dem Setup starten Sie, fügen Sie die Binärdateien an Ihrem bevorzugten Entwicklungstool und Schreiben Sie das erste Skript.

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der Softwareupdates

Installieren Sie entweder eine dieser Versionen:

+ [SQL Server 2017-Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016-R-Server (eigenständig) – nur R](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren Sie ein Entwicklungstool

Auf einem eigenständigen Server ist es üblich, arbeiten lokal mit einer Entwicklung auf dem gleichen Computer installiert.

+ [Einrichten von R-Tools](set-up-a-data-science-client.md)
+ [Einrichten von Python-Tools](../python/setup-python-client-tools-sql.md)

### <a name="step-3-write-your-first-script"></a>Schritt 3: Schreiben Sie das erste Skript.

Schreiben Sie R- oder Python-Skript, die mithilfe der Funktionen von RevoScaleR, Revoscalepy und Machine learning-Algorithmen.
  
  + [Erkunden von R und RevoScaleR in 25 Funktionen](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): beginnen Sie mit der grundlegende R-Befehle und dann auf wird ausgeführt, um die RevoScaleR verteilbaren analytischen Funktionen, die hohe Leistung bieten und Skalierung für R-Lösungen. Enthält parallelisierbare Versionen von vielen der beliebtesten R-Modellierpakete wie K-Means-Clustering, Entscheidungsstrukturen, Entscheidungswälder und Tools für die Datenbearbeitung.

  + [Schnellstart: Ein Beispiel für binäre Klassifizierung mit dem Python-Paket Microsoftml](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): ein binäres klassifizierungsmodell mithilfe der Funktionen von Microsoftml und das bekannte Breast Cancer Dataset zu erstellen.

Wählen Sie die beste Sprache für den Task. R ist am besten für statistische Berechnungen, die mit SQL schwierig sind. Nutzen Sie für setbasierte Vorgänge für Daten, die die Leistungsfähigkeit des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um maximale Leistung zu erzielen. Verwenden Sie die in-Memory-Datenbank-Engine für sehr schnelle Berechnungen über Spalten hinweg.

### <a name="step-4-operationalize-your-solution"></a>Schritt 4: Operationalisieren Sie Ihrer Lösung

Eigenständige Server können die [operationalisierung](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) Funktionalität von der SQL-markenfreien [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Sie können konfigurieren, einen eigenständigen Server für die operationalisierung, wodurch Sie die folgenden Vorteile: Bereitstellen und hosten Sie Ihren Code ein, wie Webdienste, führen Sie Diagnosen, Web-Servicekapazität testen.

## <a name="see-also"></a>Siehe auch

 [Installieren von R Server (eigenständig) oder Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md)

