---
title: Standard-R-und Python-Paket Bibliotheken
description: R-und Python-Pakete, die von SQL Server für r Services, R Server, Machine Learning Services (in-Database) und Machine Learning Server (eigenständig) installiert werden
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 2a149b4a98ec6c3a1d35cb499dcd391d87216752
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470264"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Standard-R-und Python-Pakete in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die R-und Python-Pakete aufgelistet, die mit SQL Server installiert wurden und wo die paketbibliothek zu finden ist.  

## <a name="r-package-list-for-sql-server"></a>Liste der R-Pakete für SQL Server

R-Pakete werden mit [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) und [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) installiert, wenn Sie die r-Funktion während des Setups auswählen. 

|Pakete         | 2016 | 2017 | Beschreibung |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9,2 | Wird für remotecomputekontexte, Streaming, parallele Ausführung von RX-Funktionen für Datenimport und-Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9,2 |Wird zum Einschließen von R-Skripts in gespeicherte Prozeduren verwendet |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| Niederländische Antillen | 9,2 | Fügt Machine Learning-Algorithmen in R hinzu. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | Niederländische Antillen  | 9,2 | Wird zum Schreiben von MDX-Anweisungen in R verwendet. |

Microsoftml und olapr sind standardmäßig in SQL Server 2017 Machine Learning Services verfügbar. In einer SQL Server 2016 R Services-Instanz können Sie diese Pakete über ein [Komponenten Upgrade](../install/upgrade-r-and-python.md)hinzufügen. Ein Komponenten Upgrade erhält auch neuere Versionen von Paketen (z. b. neuere Versionen von revoscaler enthalten Funktionen für die Paketverwaltung auf SQL Server).

## <a name="python-package-list-for-sql-server"></a>Python-Paketliste für SQL Server

Python-Pakete sind nur in SQL Server 2017 verfügbar, wenn Sie [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) installieren, und wählen Sie die python-Funktion aus.

| Pakete         | 2017    |  Beschreibung |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9,2 | Wird für remotecomputekontexte, Streaming, parallele Ausführung von RX-Funktionen für Datenimport und-Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9,2 | Fügt Machine Learning-Algorithmen in python hinzu. |

## <a name="open-source-r-in-your-installation"></a>Open-Source-R in Ihrer Installation

Die R-Unterstützung umfasst Open Source-Funktionen, sodass Sie grundlegende R-Funktionen aufzurufen und zusätzliche Open Source-und Drittanbieter Pakete installieren können. Die Unterstützung von R-Sprachen umfasst Kernfunktionen wie **Base**, **Stats**, **utils**und andere. Eine Basisinstallation von r umfasst auch zahlreiche Beispiel Datasets und r-Standard Tools, wie z. **b. rgui** (ein schlanker interaktiver Editor) und **RTERM** (eine R-Eingabeaufforderung). 

Die Verteilung von Open Source-R in Ihrer Installation ist [Microsoft R Open (MRO)](https://mran.microsoft.com/open). MRO fügt der Basis-R einen Wert hinzu, indem weitere Open Source-Pakete wie die [Intel Math Kernel Library](https://en.wikipedia.org/wiki/Math_Kernel_Library)eingeschlossen werden.

In der folgenden Tabelle werden die Versionen von R zusammengefasst, die von MRO mithilfe SQL Server-Setup bereitgestellt werden

|Release             | R-Version       |
|--------------------|-----------------|
| [SQL Server 2016 R-Dienste](../install/sql-r-services-windows-install.md) | geforderten   | 
| [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

Sie sollten die installierte Version von R nie manuell überschreiben, indem Sie SQL Server-Setup mit neueren Versionen im Web. Microsoft r-Pakete basieren auf bestimmten Versionen von R. durch eine Änderung Ihrer Installation kann die Anwendung destabilisiert werden.

## <a name="open-source-python-in-your-installation"></a>Open-Source-python in Ihrer Installation

SQL Server 2017 fügt python-Komponenten hinzu. Wenn Sie die python-Sprachoption auswählen, ist Anaconda 4,2 Distribution installiert. Zusätzlich zu den python-Codebibliotheken umfasst die Standardinstallation Beispiel Daten, Komponententests und Beispiel Skripts. 

SQL Server 2017 Machine Learning ist die erste Version, die sowohl R als auch python unterstützt.

|Release             | Anaconda-Version| Microsoft-Pakete    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017-Machine Learning-Dienste  | 4,2 über python 3,5 | revoscalepy, microsoftml |

Sie sollten die von installierte Python-Version niemals manuell überschreiben, indem Sie SQL Server-Setup mit neueren Versionen im Web installieren. Microsoft Python-Pakete basieren auf bestimmten Versionen von Anaconda. Wenn Sie Ihre Installation ändern, könnte dies destabilisiert werden.

## <a name="component-upgrades"></a>Komponenten Upgrades

Nach der erstmaligen Installation werden R-und Python-Pakete mithilfe von Service Packs und kumulativen Updates aktualisiert, vollständige Versions Upgrades sind jedoch nur durch *binden* an die Support Richtlinie des modernen Lebenszyklus möglich. Die Bindung ändert das Wartungs Modell. Nach der Erstinstallation werden R-Pakete standardmäßig durch Service Packs und kumulative Updates aktualisiert. Zusätzliche Pakete und vollständige Versions Upgrades von Kern-R-Komponenten sind nur durch Produkt Upgrades (von SQL Server 2016 bis SQL Server 2017) oder durch die Bindung von R-Unterstützung an Microsoft Machine Learning Server möglich. Weitere Informationen finden Sie unter [Aktualisieren von R-und python-Komponenten in SQL Server](../install/upgrade-r-and-python.md).

## <a name="package-library-location"></a>Speicherort der paketbibliothek

Wenn Sie Machine Learning mit SQL Server installieren, wird eine einzelne paketbibliothek auf Instanzebene für jede von Ihnen installierte Sprache erstellt. Unter Windows ist die instanzbibliothek ein sicherer Ordner, der bei SQL Server registriert ist.

Alle Skripts oder Code, die in-Database auf SQL Server ausgeführt werden, müssen Funktionen aus der instanzbibliothek laden. SQL Server kann nicht auf Pakete zugreifen, die in anderen Bibliotheken installiert sind. Dies gilt auch für Remote Clients. Wenn Sie von einem Remote Client aus eine Verbindung mit dem Server herstellen, können alle R-oder python-Codes, die Sie im computekontext des Servers ausführen möchten, nur Pakete verwenden, die in der instanzbibliothek installiert sind.

Die standardinstanzbibliothek kann nur von einem Computer Administrator geändert werden, um Server Objekte zu schützen. Wenn Sie nicht der Besitzer des Computers sind, müssen Sie möglicherweise die Berechtigung von einem Administrator erhalten, um Pakete in dieser Bibliothek zu installieren. 

#### <a name="file-path-for-in-database-engine-instances"></a>Dateipfad für in-Database-Engine-Instanzen

In der folgenden Tabelle werden der Speicherort von R und python für die Kombinationen von Versions-und Datenbank-Engine-Instanzen angezeigt. MSSQL13 gibt an, dass SQL Server 2016 und R-only ist. MSSQL14 gibt SQL Server 2017 und enthält R-und python-Ordner. 

Dateipfade enthalten auch Instanznamen. SQL Server installiert [Datenbank-Engine-Instanzen](../../database-engine/configure-windows/database-engine-instances-sql-server.md) als Standard Instanz (MSSQLSERVER) oder als benutzerdefinierte benannte Instanz. Wenn SQL Server als benannte Instanz installiert ist, sehen Sie, dass der Name wie folgt angehängt wird `MSSQL13.<instance_name>`:.

|Version und Sprache  | Standardpfad|
|----------------------|------------|
| SQL Server 2016 |C:\Programme\Microsoft SQL server\mssql13. MSSQLSERVER\R_SERVICES\library|
| SQL Server 2017 mit R|C:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\R_SERVICES\library |
| SQL Server 2017 mit python |C:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages |


#### <a name="file-path-for-standalone-server-installations"></a>Dateipfad für eigenständige Serverinstallationen

In der folgenden Tabelle sind die Standard Pfade der Binärdateien aufgeführt, wenn SQL Server 2016 R Server (eigenständig) oder SQL Server 2017 Machine Learning Server (Standalone)-Server installiert ist. 

|Version| Installation|Standardpfad|
|-------|-------------|------------|
| SQL Server 2016|R-Server (eigenständig)| C:\Programme\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning Server mit R |C:\Programme\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Server mit python |C:\Programme\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Wenn Sie andere Ordner mit ähnlichen Unterordner Namen und-Dateien finden, verfügen Sie wahrscheinlich über eine eigenständige Installation von Microsoft R Server oder [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/). Diese Server Produkte verfügen über verschiedene Installationsprogramme und Pfade (c:\programme\microsoft\r Server\R_SERVER oder c:\programme\microsoft\ml Server\R_SERVER). Weitere Informationen finden Sie unter [install Machine Learning Server for Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) oder [install R Server 9,1 for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="next-steps"></a>Nächste Schritte

+ [Paketinformationen abrufen](installed-package-information.md)
+ [Neue R-Pakete installieren](../r/install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Remoteverwaltung für R-Pakete aktivieren](../r/r-package-how-to-enable-or-disable.md)
+ [RevoScaleR-Funktionen für die Verwaltung von R-Paketen](../r/use-revoscaler-to-manage-r-packages.md)
+ [R-Paketsynchronisierung](../r/package-install-uninstall-and-sync.md)
+ [miniCRAN für das lokale R-Paketrepository](../r/create-a-local-package-repository-using-minicran.md)
