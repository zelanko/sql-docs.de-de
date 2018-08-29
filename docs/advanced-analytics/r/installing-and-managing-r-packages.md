---
title: Standardbibliotheken R- und Python-Paket in SQL Server R und SQL Server-Machine Learning | Microsoft-Dokumentation
description: R und Python-Pakete, die von SQLServer für R Services, R Server, Machine Learning Services (Datenbankintern) und Machine Learning Server (eigenständig) installiert
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7f5c51e9b93aca5d52858417667865633a0c4151
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118308"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Standard-R und Python-Paketen in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt, die R- und Python-Pakete, die mit SQL Server und, wo Sie finden die Paket-Bibliothek installiert wird.  

## <a name="r-package-list-for-sql-server"></a>Liste der R-Pakete für SQL Server

R-Pakete installiert und die [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) und [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) Wenn Sie die R-Funktion während des Setups auswählen. 

Pakete         | 2016 | 2017 | Description |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9.2 | Für remotecomputekontexte, streaming, parallele Ausführung über Rx-Funktionen für Datenimport und -Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9.2 |Zum Einschließen von R-Skripts in gespeicherten Prozeduren verwendet. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| Niederländische Antillen | 9.2 | Fügt der Algorithmen für maschinelles lernen in r | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | Niederländische Antillen  | 9.2 | Zum Schreiben von MDX-Anweisungen in r verwendet |

MicrosoftML und OlapR sind standardmäßig in SQL Server 2017-Machine Learning Services verfügbar. In einer SQL Server 2016 R Services-Instanz, Sie können diese Pakete durch Hinzufügen einer [Upgrade von Integrationskomponenten](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Ein Komponentenupgrade erhält Sie auch neuere Versionen der Pakete (beispielsweise die neuere Versionen der RevoScaleR-Funktionen für die Verwaltung von Paketen auf SQL Server enthalten).

## <a name="python-package-list-for-sql-server"></a>Liste der Python-Pakete für SQL Server

Python-Pakete sind nur in SQL Server 2017 verfügbar, bei der Installation [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) , und wählen Sie die Python-Funktion.

| Pakete         | 2017    |  Description |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | Für remotecomputekontexte, streaming, parallele Ausführung über Rx-Funktionen für Datenimport und -Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Machine Learning-Algorithmen hinzugefügt in Python. |

## <a name="open-source-r-in-your-installation"></a>Open-Source-Sprache R in Ihrer installation

Unterstützung für R enthält Open Source sind, damit Sie grundlegende R-Funktionen aufrufen und zusätzliche Open Source- und Drittanbieter-Pakete installieren können. Unterstützung der Sprache R beinhaltet Kernfunktionalität, z. B. **Basis**, **Statistiken**, **"utils"**, und andere. Eine Basisinstallation von R enthält außerdem zahlreiche Beispiel-Datasets und R-Standardtools wie z. B. **RGui** (einen einfachen interaktiven Editor) und **RTerm** (ein R-Eingabeaufforderung). 

Die Verteilung der Open-Source-R, die in Ihrer Installation enthalten ist [Microsoft R öffnen (MRO)](https://mran.microsoft.com/open). MRO kommt base R von einschließlich zusätzlicher Open-Source-Pakete, wie z. B. die [Intel Math Kernel Library](https://en.wikipedia.org/wiki/Math_Kernel_Library).

Die folgende Tabelle enthält die Versionen von R von MRO mit SQL Server-Setup bereitgestellt werden.

|Release             | R-version       |
|--------------------|-----------------|
| [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [SQL Server 2017-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

Sie sollten die Version von R, die von SQL Server-Setup installiert werden, durch neuere Versionen im Internet niemals manuell überschreiben. Microsoft R-Paketen basieren auf bestimmte Versionen von r ändern kann die Installation destabilisieren sie.

## <a name="open-source-python-in-your-installation"></a>Open-Source-Python in Ihrer installation

SQL Server 2017 fügt Python-Komponenten. Wenn Sie die Python-Language-Option auswählen, wird die 4.2 der Anaconda-Distribution installiert. Zusätzlich zu den Bibliotheken für Python-Code enthält die Standardinstallation Beispieldaten, Komponententests und Beispielskripts. 

SQL Server 2017-Machine Learning ist die erste Version, um R und Python-Unterstützung zu erhalten.

|Release             | Anaconda version| Microsoft-Pakete    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017-Machine Learning-Dienste  | 4.2 über Python 3.5 | die Revoscalepy, microsoftml |

Sie sollten die Version von Python, die von SQL Server-Setup installiert werden, durch neuere Versionen im Internet niemals manuell überschreiben. Microsoft Python-Paketen basieren auf bestimmte Versionen von Anaconda. Ändern die Installation kann es destabilisieren.

## <a name="component-upgrades"></a>Upgrades der Komponenten

Nach der ursprünglichen Installation, R und Python-Paketen durch Servicepacks und kumulativen Updates aktualisiert werden, aber vollständige Versionsupgrades sind nur durch *Bindung* , der Modern Lifecycle-Richtlinie. Bindung ändert sich das Dienstmodell. Standardmäßig werden R-Pakete nach der ersten Installation über die Servicepacks und kumulativen Updates aktualisiert. Zusätzliche Pakete und vollständige Versionsupgrade für grundlegende R-Komponenten sind nur möglich, über die Produkt-Upgrades (von SQL Server 2016 auf SQL Server 2017) oder durch die Bindung von R, Microsoft Machine Learning Server zu unterstützen. Weitere Informationen finden Sie unter [ein Upgrade von R und Python-Komponenten in SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="package-library-location"></a>Speicherort des Pakets-Bibliothek

Wenn Sie Machine Learning mit SQL Server installieren, wird eine einzelnes Paket-Bibliothek auf Instanzebene für jede Sprache erstellt, die Sie installieren. Auf Windows ist die Instanz-Bibliothek einem gesicherten Ordner, die in SQL Server registriert.

Alle Skripts oder Code, führt in in SQL Server der Datenbank muss die Funktionen aus der Bibliothek für die Instanz laden. SQL Server kann nicht mit anderen Bibliotheken installierte Pakete zugreifen. Dies gilt für RAS-Clients. Wenn von einem Remoteclient eine Verbindung mit dem Server herstellen, kann jeder R oder Python-Code, der im Server-rechenkontext ausgeführt werden soll nur in der Bibliothek der Instanz installierten Pakete verwenden.

Um Serverressourcen zu schützen, kann die Standardbibliothek für die Instanz nur von einem Computeradministrator geändert werden. Wenn Sie nicht der Besitzer des Computers sind, müssen Sie die Berechtigung von einem Administrator zum Installieren von Paketen zu dieser Bibliothek zu erhalten. 

#### <a name="file-path-for-in-database-engine-instances"></a>Der Pfad für die In der Datenbank-Engine-Instanzen

Die folgende Tabelle zeigt den Speicherort der Datei R- und Python-Version und Datenbank-Engine-Instanz Kombinationen. MSSQL13 gibt SQL Server 2016 und wird nur R. MSSQL14 gibt SQL Server 2017 und verfügt über R und Python-Ordner. 

Pfade umfassen auch die Instanznamen. SQL Server installiert [Datenbank-Engine-Instanzen](../../database-engine/configure-windows/database-engine-instances-sql-server.md) als Standardinstanz (MSSQLSERVER) oder als eine benutzerdefinierte benannte Instanz. Wenn SQL Server als benannte Instanz installiert ist, wird Ihnen diese Namen, und fügen wie folgt: `MSSQL13.<instance_name>`.

|Version und Sprache  | Standardpfad|
|----------------------|------------|
| SQL Server 2016 |C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQLServer 2017 mit R|C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQLServer 2017 mit Python |C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site-Pakete |


#### <a name="file-path-for-standalone-server-installations"></a>Dateipfad für die eigenständige Installation

Die folgende Tabelle enthält die Standardpfade der Binärdateien auf, wenn SQL Server 2016 R Server (eigenständig) oder SQL Server 2017-Machine Learning Server (eigenständig)-Server installiert ist. 

|Version| Installation|Standardpfad|
|-------|-------------|------------|
| SQL Server 2016|R-Server (eigenständig)| C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning-Server mit R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning-Server mit Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Wenn Sie andere Ordner mit ähnlichen Unterordnernamen und Dateien finden, haben Sie wahrscheinlich eine eigenständige Installation von Microsoft R Server oder [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/). Diese Serverprodukte verfügen über unterschiedliche Installationsprogramme und Pfade (d. h., c:\Programme\Microsoft Files\Microsoft\R Server\R_SERVER oder c:\programme\microsoft\ml SERVER\R_SERVER). Weitere Informationen finden Sie unter [installieren Machine Learning Server für Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) oder [Installieren von R Server 9.1 für Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="next-steps"></a>Nächste Schritte

+ [Paketinformationen abrufen](determine-which-packages-are-installed-on-sql-server.md)
+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Remoteverwaltung für R-Pakete aktivieren](r-package-how-to-enable-or-disable.md)
+ [RevoScaleR-Funktionen für die Verwaltung von R-Paketen](use-revoscaler-to-manage-r-packages.md)
+ [R-Paketsynchronisierung](package-install-uninstall-and-sync.md)
+ [miniCRAN für das lokale R-Paketrepository](create-a-local-package-repository-using-minicran.md)
