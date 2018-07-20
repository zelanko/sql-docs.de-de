---
title: SQL Server Machine Learning Server (eigenständig) und R Server (eigenständig) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a8cdceabc26c55b6eade57712fa610d3e84808f5
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174787"
---
# <a name="sql-server-machine-learning-server-standalone-and-r-server-standalone"></a>SQL Server Machine Learning Server (eigenständig) und R Server (eigenständig)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Ein eigenständigen Server ist eine Installation von Machine Learning-Komponenten gegliedert, wie R und Python-Funktionen, die unabhängig von der SQL Server-Datenbank-Engine-Instanzen ausgeführt werden. Sie können einen eigenständigen Server, mit der keine Abhängigkeiten von SQL Server installieren. Da ein eigenständiger Server unabhängig von der SQL Server, Konfiguration und Verwaltung von Aufgaben und Tools auf eine nicht-SQL-Version von Machine Learning Server, auf dem Sie sich vertraut können sind, in machen ähnlicher [in diesem Artikel](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server).

Das Ziel eines eigenständigen Machine Learning-Servers ist eine umfassende Entwicklungsumgebung, mit der verteilte und parallele Verarbeitung von R und Python-Workloads für kleine bis große Datasets, die mithilfe der proprietären Pakete und berechnungsmodulen bereitstellen mit dem Server installiert. Die R und Python-Pakete auf einem eigenständigen Server sind identisch mit denen in einer SQL Server (Datenbankintern)-Installation, sodass Codeportabilität bereitgestellt und [Compute-Kontextwechsel](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

Der Hauptgrund für den Entwickler wählen, dass es sich bei ein eigenständigen Machine Learning-Server wird über den Arbeitsspeicher und verarbeitungsleistung Einschränkungen von Open-Source-R und Python zu verschieben. Eigenständige Server können zu laden und verarbeiten große Mengen von Daten auf mehreren Kernen und Aggregieren der Ergebnisse in eine einzelne, konsolidierte Ausgabe. Die Funktionen und Algorithmen werden für sowohl Skalierung als auch Hilfsprogramm entwickelt: Bereitstellung von predictive Analytics, statistische Modellierung, datenvisualisierungen und fortschrittliche-Machine learning-Algorithmen in einer kommerziellen Serverprodukt konzipiert und unterstützt von Von Microsoft.

Im Allgemeinen empfohlen, Sie behandeln (eigenständig) und (In-Database) Installationen als sich gegenseitig exklusiv zur Vermeidung von Ressourcenkonflikten, aber wenn Sie über ausreichende Ressourcen, besteht keine Verbot für beide auf demselben physischen Computer installieren.

Sie können nur ein eigenständiger Server verwenden, auf dem Computer: entweder [Machine Learning Server (eigenständig) für SQL Server 2017](../install/sql-machine-learning-standalone-windows-install.md) oder [SQL Server 2016 R Server (eigenständig)](../install/sql-r-standalone-windows-install.md). Sie müssen manuell eine Version vor der Installation einer anderen Version deinstallieren.

## <a name="components-of-a-standalone-server"></a>Komponenten eines eigenständigen Servers

R wird nur von SQL Server 2016 ist. SQL Server-2017 unterstützt R und Python. Die folgende Tabelle beschreibt die Funktionen in der jeweiligen Version.

| Komponente | Description |
|-----------|-------------|
| R-Pakete | [RevoScaleR](revoscaler-overview.md) ist die primäre Bibliothek für skalierbare R mit Funktionen zur datenbearbeitung, Transformation, Visualzation und Analyse.  <br/>[MicrosoftML (R)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen. <br/>[Mrsdeploy](operationalization-with-mrsdeploy.md) bietet web-Service-Bereitstellung (in nur SQL Server 2017). <br/>[OlapR](how-to-create-mdx-queries-using-olapr.md) dient zum Angeben von MDX-Abfragen in r|
| Microsoft R Open (MRO) | [MRO](https://mran.microsoft.com/open) ist die Open-Source-Distribution von R. Das Paket und ein Interpreter sind enthalten. Verwenden Sie immer die Version der MRO Setup gebündelt. |
| R-tools | R-Konsole Windows und eingabeaufforderungen werden zu einer Verteilung von R-Standardtools. Finden sie unter \Programme\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| R-Beispiele und Skripts |  Open-Source-R und RevoScaleR-Pakete enthalten die integrierten Datasets, damit Sie erstellen und Ausführen von Skripts mit vorinstallierten Daten können. Suchen Sie unter \Programme\Microsoft SQL Server\140\R_SERVER\library\datasets und \library\RevoScaleR. |
| Python-Pakete | [die Revoscalepy](../python/what-is-revoscalepy.md) ist die primäre Bibliothek für skalierbare Python mit Funktionen zur datenbearbeitung, Transformation, Visualzation und Analyse. <br/>[Microsoftml (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) fügt Machine Learning-Algorithmen, um benutzerdefinierte Modelle für die Textanalyse, Bildanalyse und stimmungsanalysen zu erstellen.  |
| Python-tools | Das integrierte Tool der Python-Befehlszeile eignet sich für ad-hoc-Tests und Aufgaben. Suchen Sie das Tool im Verzeichnis \Programme\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda ist ein Open-Source-Distribution von Python und essential-Pakete. |
| Python-Beispiele und Skripts | Enthält wie bei R, Python, integrierten Datasets und Skripts. Suchen Sie die Revoscalepy-Daten unter \Programme\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-Packages\revoscalepy\data\sample-Daten. |
| Vortrainierte Modelle in R und Python | Vortrainierte Modelle werden unterstützt und auf einem eigenständigen Server verwendet werden, aber sie kann nicht über SQL Server-Setup installiert werden. Das Setupprogramm für die Microsoft Machine Learning Server stellt die Modellen, die Sie installieren können kostenlos. Weitere Informationen finden Sie unter [Installation vorab Machine Learning-Modelle in SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="get-started-step-by-step"></a>Beginnen Sie Schritt für Schritt

Mit dem Setup starten Sie, fügen Sie die Binärdateien an Ihrem bevorzugten Entwicklungstool und Schreiben Sie das erste Skript.

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der Softwareupdates

Installieren Sie entweder eine dieser Versionen:

+ [SQL Server 2017-Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016-R-Server (eigenständig) – nur R](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren Sie ein Entwicklungstool

Konfigurieren Sie Ihre Entwicklungstools, um die Machine Learning Server-Binärdateien zu verwenden. Weitere Informationen zu Python finden Sie unter [Link-Python-Binärdateien](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Anweisungen zur Verwendung in R Studio eine Verbindung herstellen, finden Sie unter [mit verschiedenen Versionen von R](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) , und zeigen Sie das Tool zu C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64. Sie können auch ausprobieren [R-Tools für Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation). 

### <a name="step-3-write-your-first-script"></a>Schritt 3: Schreiben Sie das erste Skript.

Schreiben Sie R- oder Python-Skript, die mithilfe der Funktionen von RevoScaleR, Revoscalepy und Machine learning-Algorithmen.
  
  + [Erkunden von R und RevoScaleR in 25 Funktionen](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): beginnen Sie mit der grundlegende R-Befehle und dann auf wird ausgeführt, um die RevoScaleR verteilbaren analytischen Funktionen, die hohe Leistung bieten und Skalierung für R-Lösungen. Enthält parallelisierbare Versionen von vielen der beliebtesten R-Modellierpakete wie K-Means-Clustering, Entscheidungsstrukturen, Entscheidungswälder und Tools für die Datenbearbeitung.

  + [Schnellstart: Ein Beispiel für binäre Klassifizierung mit dem Python-Paket Microsoftml](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): ein binäres klassifizierungsmodell mithilfe der Funktionen von Microsoftml und das bekannte Breast Cancer Dataset zu erstellen.

Wählen Sie die beste Sprache für den Task. R ist am besten für statistische Berechnungen, die mit SQL schwierig sind. Nutzen Sie für setbasierte Vorgänge für Daten, die die Leistungsfähigkeit des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um maximale Leistung zu erzielen. Verwenden Sie die in-Memory-Datenbank-Engine für sehr schnelle Berechnungen über Spalten hinweg.

### <a name="step-4-operationalize-your-solution"></a>Schritt 4: Operationalisieren Sie Ihrer Lösung

Eigenständige Server können die [operationalisierung](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) Funktionalität von der SQL-markenfreien [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Sie können konfigurieren, einen eigenständigen Server für die operationalisierung, wodurch Sie die folgenden Vorteile: Bereitstellen und hosten Sie Ihren Code ein, wie Webdienste, führen Sie Diagnosen, Web-Servicekapazität testen.

## <a name="see-also"></a>Siehe auch

 [SQL Server Machine Learning-Dienste (Datenbankintern)](sql-server-r-services.md)

