---
title: Eigenständige R Server oder Machine Learning Server Installation
description: Übersicht über die Einführung in eigenständige R Server und Machine Learning Server in SQL Server Setup
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: overview
author: dphansen
ms.author: davidph
ms.openlocfilehash: 84ef5d684e767016491baa6e47e37d1402fc6879
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470050"
---
# <a name="r-server-standalone-and-machine-learning-server-standalone-in-sql-server"></a>R Server (eigenständig) und Machine Learning Server (eigenständig) in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server bietet Installationsunterstützung für eine eigenständige R Server oder Machine Learning Server, die unabhängig von SQL Server ausgeführt wird. Abhängig von Ihrer SQL Server Version verfügt ein eigenständiger Server über eine Grundlage von Open Source-R und möglicherweise python, überlagert mit Hochleistungs Bibliotheken von Microsoft, die statistische und Predictive Analytics skaliert hinzufügen. Bibliotheken aktivieren auch Machine Learning-Aufgaben in skriskripten in R oder python. 

In SQL Server 2016 heißt diese Funktion **R Server (eigenständig)** und ist R-only. In SQL Server 2017 heißt es **Machine Learning Server (eigenständig)** und umfasst sowohl R als auch Python.  

> [!Note]
> Wie von SQL Server-Setup installiert, ist ein eigenständiger Server funktionell gleichwertig mit den nicht-SQL-Branding-Versionen von [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)und unterstützt dieselben Benutzer Szenarien, einschließlich Remote Ausführung, Operationalisierung und Web. Dienste und die gesamte Sammlung von R-und python-Bibliotheken.

## <a name="components"></a>Komponenten

SQL Server 2016 ist nur R. SQL Server-2017 unterstützt R und Python. In der folgenden Tabelle werden die Features in den einzelnen Versionen beschrieben.

| Komponente | Beschreibung |
|-----------|-------------|
| R-Pakete | [**Revoscaler**](ref-r-revoscaler.md) ist die primäre Bibliothek für skalierbare R mit Funktionen für die Bearbeitung, Transformation, Visualisierung und Analyse von Daten.  <br/>[**Microsoftml**](ref-r-microsoftml.md) fügt Machine Learning-Algorithmen hinzu, um benutzerdefinierte Modelle für die Textanalyse, die Bildanalyse und die Stimmungs Analyse zu erstellen. <br/>[**sqlrutils**](ref-r-sqlrutils.md) stellt Hilfsfunktionen für das Einfügen von R-Skripts in eine gespeicherte T-SQL-Prozedur, das Registrieren einer gespeicherten Prozedur in einer Datenbank und das Ausführen der gespeicherten Prozedur aus einer R-Entwicklungsumgebung bereit.<br/>[**mrsdeployment**](operationalization-with-mrsdeploy.md) bietet eine Webdienst Bereitstellung (nur in SQL Server 2017). <br/>[**olapr**](ref-r-olapr.md) dient zum Angeben von MDX-Abfragen in R.|
| Microsoft R Open (MRO) | [**MRO**](https://mran.microsoft.com/open) ist die Open Source-Verteilung von R von Microsoft. Das Paket und der Interpreter sind eingeschlossen. Verwenden Sie immer die Version von MRO gebündelt in Setup. |
| R-Tools | R-Konsolenfenster und Eingabe Aufforderungen sind Standard Tools in einer R-Distribution. Diese finden Sie unter \Programme\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| R-Beispiele und-Skripts |  Open-Source-R-und revoscaler-Pakete enthalten integrierte Datasets, mit denen Sie Skripts mit vorinstallierten Daten erstellen und ausführen können. Suchen Sie nach dem Verzeichnis \Programme\Microsoft SQL Server\140\R_SERVER\library\datasets und \library\revoscaler. |
| Python-Pakete | [**revoscalepy**](../python/ref-py-revoscalepy.md) ist die primäre Bibliothek für skalierbare python mit Funktionen für die Datenbearbeitung, Transformation, Visualisierung und Analyse. <br/>[**microsoftml**](../python/ref-py-microsoftml.md) fügt Machine Learning-Algorithmen hinzu, um benutzerdefinierte Modelle für die Textanalyse, die Bildanalyse und die Stimmungs Analyse zu erstellen.  |
| Python-Tools | Das integrierte python-Befehlszeilen Tool eignet sich für Ad-hoc-Tests und-Aufgaben. Das Tool finden Sie unter \Programme\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda ist eine Open Source-Verteilung von Python-und Essentials-Paketen. |
| Python-Beispiele und-Skripts | Wie bei R umfasst python auch integrierte Datasets und Skripts. Suchen Sie die revoscalepy-Daten unter "\Programme\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample-Data. |
| Vortrainierte Modelle in R und python | Vorab trainierte Modelle werden für bestimmte Anwendungsfälle erstellt und vom Data Science Engineering-Team bei Microsoft verwaltet. Mit den von Ihnen bereitgestellten neuen Dateneingaben können Sie die vorab trainierten Modelle unverändert verwenden, um positive negative Stimmungen in Text zu bewerten oder Features in Bildern zu erkennen. Vorab trainierte Modelle werden unterstützt und können auf einem eigenständigen Server verwendet werden. Sie können Sie jedoch nicht über SQL Server Setup installieren. Weitere Informationen finden Sie [unter Install pretrainierte Machine Learning Models on SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-a-standalone-server"></a>Verwenden eines eigenständigen Servers

R-und Python-Entwickler wählen in der Regel einen eigenständigen Server aus, um über die Arbeitsspeicher-und Verarbeitungs Einschränkungen von Open Source-r und python hinauszugehen R-und python-Bibliotheken, die auf einem eigenständigen Server ausgeführt werden, können große Datenmengen auf mehreren Kernen laden und verarbeiten und die Ergebnisse in eine einzelne konsolidierte Ausgabe aggregieren. Hochleistungs Funktionen werden sowohl für die Skalierung als auch für das Hilfsprogramm entwickelt: Bereitstellen von Predictive Analytics, statistischen Modellierung, Datenvisualisierungen und führenden Machine Learning-Algorithmen in einem kommerziellen Server Produkt, das von Microsoft.

Als unabhängiger Server, der von SQL Server entkoppelt ist, wird die R-und python-Umgebung konfiguriert, gesichert und der Zugriff erfolgt über das zugrunde liegende Betriebssystem und die Standard Tools, die im eigenständigen Server bereitgestellt werden, nicht SQL Server. Es gibt keine integrierte Unterstützung für SQL Server relationale Daten. Wenn Sie SQL Server Daten verwenden möchten, können Sie Datenquellen Objekte und Verbindungen wie von jedem beliebigen Client erstellen.

Als Ergänzung zu SQL Server ist ein eigenständiger Server auch als leistungsstarke Entwicklungsumgebung nützlich, wenn Sie sowohl lokale als auch Remote Computing benötigen. Die R-und Python-Pakete auf einem eigenständigen Server sind identisch mit denen, die mit einer Datenbank-Engine-Installation bereitgestellt werden, sodass Code Portabilität und [computecontext-Wechsel](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)möglich sind.

## <a name="how-to-get-started"></a>Vorgehensweise beim Einstieg

Beginnen Sie mit dem Setup, fügen Sie die Binärdateien an Ihr bevorzugtes Entwicklungs Tool an, und schreiben Sie das erste Skript.

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der Software

Installieren Sie eine der folgenden Versionen:

+ [SQL Server 2017 Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (eigenständig): nur R](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren eines Entwicklungs Tools

Auf einem eigenständigen Server ist es üblich, lokal über eine auf dem gleichen Computer installierte Entwicklung zu arbeiten.

+ [Einrichten von R-Tools](set-up-a-data-science-client.md)
+ [Einrichten von Python-Tools](../python/setup-python-client-tools-sql.md)

### <a name="step-3-write-your-first-script"></a>Schritt 3: Schreiben Ihres ersten Skripts

Schreiben Sie ein R-oder Python-Skript mithilfe von Funktionen von revoscaler, revoscalepy und den Machine Learning-Algorithmen.
  
  + [Erkunden Sie R und revoscaler in 25 Funktionen](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): Beginnen Sie mit grundlegenden R-Befehlen, und gehen Sie dann zu den analytischen Funktionen von revoscaler verteilbarer, die hohe Leistung und Skalierung für R-Lösungen bieten. Enthält parallelisierbare Versionen von vielen der beliebtesten R-Modellierpakete wie K-Means-Clustering, Entscheidungsstrukturen, Entscheidungswälder und Tools für die Datenbearbeitung.

  + [Schnellstart: Ein Beispiel für die binäre Klassifizierung mit dem microsoftml python](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml)-Paket: Erstellen Sie ein binäres Klassifizierungs Modell mithilfe der Funktionen von microsoftml und des bekannten Breast Cancer-Datasets.

Wählen Sie die beste Sprache für den Task aus. R eignet sich am besten für statistische Berechnungen, die mit SQL schwierig zu implementieren sind. Nutzen Sie die Leistungsfähigkeit von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um eine maximale Leistung zu erzielen. Verwenden Sie die in-Memory-Datenbank-Engine für sehr schnelle Berechnungen über Spalten.

### <a name="step-4-operationalize-your-solution"></a>Schritt 4: Operationalisieren der Lösung

Eigenständige Server können die [operationalisierungsfunktionalität](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) der nicht-SQL-Branding- [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)verwenden. Sie können einen eigenständigen Server für die Operationalisierung konfigurieren, was Ihnen folgende Vorteile bietet: Bereitstellen und Hosten Ihres Codes als Webdienste, Ausführen von Diagnosen und Testen der Webdienst Kapazität.

### <a name="step-5-maintain-your-server"></a>Schritt 5: Warten des Servers

In SQL Server werden kumulative Updates in regelmäßigen Abständen veröffentlicht. Durch das Anwenden der kumulativen Updates werden eine vorhandene Installation von Sicherheits-und Funktions Verbesserungen erweitert. 

Beschreibungen neuer oder geänderter Funktionen finden Sie im Artikel [CAB-Downloads](../install/sql-ml-cab-downloads.md) und auf den Webseiten für [2016 SQL Server kumulative Updates](https://support.microsoft.com/help/3177312/sql-server-2016-build-versions) und [SQL Server 2017 kumulative Updates](https://support.microsoft.com/help/4047329). 

Weitere Informationen zum Anwenden von Updates auf eine vorhandene Instanz finden Sie unter [Anwenden von Updates](../install/sql-machine-learning-standalone-windows-install.md#apply-cu) in den Installationsanweisungen.

## <a name="see-also"></a>Siehe auch

 [Installieren von R Server (eigenständig) oder Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md)

