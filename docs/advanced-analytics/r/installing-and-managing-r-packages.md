---
title: Standardbibliotheken R und Python-Paket in SQL Server R und SQL Server-Machine Learning | Microsoft Docs
description: R und Python-Pakete, die Installation von SQLServer für R-Services, R-Server, Machine Learning Services (Datenbankintern) und Machine Learning-Server (eigenständig)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9362d6e9dc98f80beabc301f43e755b205b40a10
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707288"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Standard-R und Python-Paketen in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel führt die R und Python-Pakete, die mit SQL Server sowie Orten zum Suchen von der Bibliothek des Pakets installiert.  

## <a name="r-package-list-for-sql-server"></a>Liste der R-Pakete für SQL Server

R-Pakete installiert und die [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) und [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) bei Auswahl die R-Funktion während des Setups. 

Pakete         | 2016 | 2017 | Description |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9.2 | Für remote rechenkontexte, streaming, parallele Ausführung von Rx-Funktionen für Datenimport und Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9.2 |Zum Einschließen von R-Skripts in gespeicherten Prozeduren verwendet. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| entfällt | 9.2 | Fügt der Machine Learning-Algorithmen in R. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | entfällt  | 9.2 | Zum Schreiben von MDX-Anweisungen in r verwendet |

MicrosoftML und OlapR sind standardmäßig in SQL Server 2017 Machine Learning Services verfügbar. In einer SQL Server 2016-R-Services-Instanz, Sie können diese Pakete durch Hinzufügen einer [Komponentenupdate](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Ein Upgrade von Integrationskomponenten auch ruft Sie neuere Versionen der Pakete (neuere Versionen von "revoscaler" zählen beispielsweise Funktionen zum Verwalten von Paketen in SQL Server).

## <a name="python-package-list-for-sql-server"></a>Liste der Python-Pakete für SQL Server

Python-Pakete nur in SQL Server-2017 verfügbar sind, bei der Installation [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) , und wählen Sie die Python-Funktion.

| Pakete         | 2017    |  Description |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | Für remote rechenkontexte, streaming, parallele Ausführung von Rx-Funktionen für Datenimport und Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Fügt den Machine Learning-Algorithmen in Python hinzu. |

## <a name="open-source-r-in-your-installation"></a>Open-Source-R in Ihrer installation

R-Unterstützung umfasst, Open Source-, sodass Sie Basis R-Funktionen aufrufen und zusätzliche Open Source- und Drittanbieter-Pakete installieren können. Sprachunterstützung für R enthält grundlegende Funktionen, wie z. B. **Basis**, **Stats**, **Utils**, und andere. Eine Basisinstallation von R enthält außerdem zahlreiche beispieldatasets und R-Standardtools wie z. B. **"rgui.exe"** (eine einfache interaktive-Editor) und **RTerm** (ein R-Eingabeaufforderung). 

Die Verteilung der Open-Source-R, die in Ihrer Installation enthalten ist [Microsoft R öffnen (MRO)](https://mran.microsoft.com/open). MRO fügt Wert Basis R von einschließlich zusätzliche Open-Source-Pakete, wie z. B. die [mathematische Kernenbibliothek von Intel](https://en.wikipedia.org/wiki/Math_Kernel_Library).

In der folgenden Tabelle sind die Versionen von R mit SQL Server-Setup MRO zusammengefasst.

|Release             | R-version       |
|--------------------|-----------------|
| [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [SQL Server 2017 Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

Sie sollten die Version von R, die von SQL Server-Setup installiert werden, durch neuere Versionen im Web nie manuell überschreiben. Microsoft R-Pakete basieren auf bestimmte Versionen von r ändern kann die Installation destabilisieren es.

## <a name="open-source-python-in-your-installation"></a>Open-Source-Python in Ihrer installation

SQL Server-2017 werden Python-Serverkomponenten hinzufügt. Wenn Sie die Python-Language-Option auswählen, wird die 4.2 Anaconda-Verteilung installiert. Zusätzlich zu den Python-Code-Bibliotheken enthält die Standardinstallation Beispieldaten, Komponententests und Beispielskripts. 

SQL Server 2017 Machine Learning ist die erste Version R und Python-Unterstützung verfügen.

|Release             | Anaconda-version| Microsoft-Pakete    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017-Machine Learning-Dienste  | 4.2 über Python 3.5 | Revoscalepy microsoftml |

Sie sollten die Version von Python mit neueren Versionen im Web von SQL Server-Setup installiert nie manuell überschreiben. Microsoft-Python-Pakete basieren auf bestimmte Versionen des Anaconda. Ändern die Installation kann es destabilisieren.

## <a name="component-upgrades"></a>Upgrades bei den Komponenten

Nach einer Erstinstallation R und Python-Pakete über Servicepacks und kumulativen Updates aktualisiert werden, aber vollständige Versionsupgrade sind nur möglich, indem *Bindung* für die moderne Lifecycle Support-Richtlinie. Bindung ändert das Dienstmodell. Standardmäßig werden R-Pakete nach der ersten Installation über Servicepacks und kumulativen Updates aktualisiert. Zusätzliche Pakete und vollständige Versionsupgrade für R-Kernkomponenten sind nur möglich, über Produktupgrades (von SQL Server 2016, SQL Server-2017) oder durch das Binden von R mit Microsoft Machine Learning-Server unterstützen. Weitere Informationen finden Sie unter [R aktualisieren und Python-Komponenten in SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="package-library-location"></a>Paketspeicherort-Bibliothek

Bei der Installation von Machine Learning mit SQL Server wird eine einzelnes Paket-Bibliothek auf Instanzebene für jede Sprache erstellt, die Sie installieren. Unter Windows ist die Instanz-Bibliothek einem gesicherten Ordner, die mit SQL Server registriert.

Alle Skripts oder Codeabschnitts, führt in-auf SQL Server-Datenbank muss Funktionen aus der Instanz-Bibliothek geladen werden. SQL Server kann nicht mit anderen Bibliotheken installierte Pakete zugreifen. Dies betrifft auch Remoteclients. Beim Herstellen einer Verbindung mit dem Server von einem Remoteclient, können alle R oder Python-Code, der in der Server-computekontext ausgeführt werden soll nur Pakete, die in der Bibliothek für die Instanz installiert.

Um Serverressourcen zu schützen, kann die Standardbibliothek Instanz nur von einem Computeradministrator geändert werden. Wenn Sie nicht der Besitzer des Computers sind, müssen Sie möglicherweise Berechtigung durch einen Administrator für das Installieren der Pakete in dieser Bibliothek zu erhalten. 

#### <a name="file-path-for-in-database-engine-instances"></a>Der Pfad für die Instanzen des Datenbankmoduls In der Datenbank

Die folgende Tabelle zeigt den Speicherort von R und Python für Version und Datenbank Kombinationen der Datenbankmodul-Instanz. MSSQL13 gibt an, SQL Server 2016 und wird nur für R. MSSQL14 gibt SQL Server-2017 an und weist R und Python-Ordner. 

Dateipfade umfassen auch Instanznamen. SQL Server installiert [Datenbank Instanzen des Datenbankmoduls](../../database-engine/configure-windows/database-engine-instances-sql-server.md) als Standardinstanz (MSSQLSERVER) oder als eine benutzerdefinierte benannte Instanz. Wenn SQL Server als benannte Instanz installiert ist, wird dieses Namens angehängt wie folgt angezeigt: `MSSQL13.<instance_name>`.

|Version und Sprache  | Standardpfad|
|----------------------|------------|
| SQL Server 2016 |C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQLServer 2017 mit R|C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQLServer 2017 mit Python |C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site-Pakete |


#### <a name="file-path-for-standalone-server-installations"></a>Dateipfad für eigenständige Serverinstallationen

Die folgende Tabelle enthält die Standardpfade der Binärdateien aus, wenn SQL Server 2016 R Server (eigenständig) oder SQL Server 2017 Machine Learning-Server (eigenständig) Server installiert ist. 

|Version| Installation|Standardpfad|
|-------|-------------|------------|
| SQL Server 2016|R-Server (eigenständig)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning-Server mit R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning-Server mit Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Wenn Sie andere Ordner mit ähnlichen Unterordnernamen und Dateien feststellen, haben Sie wahrscheinlich eine eigenständige Installation von Microsoft R Server oder [Machine Learning-Server](https://docs.microsoft.com/machine-learning-server/). Diese Serverprodukte haben unterschiedliche Installationsprogramme und Pfade (nämlich c:\Programme\Microsoft Files\Microsoft\R Server\R_SERVER oder c:\Programme\Microsoft Files\Microsoft\ML SERVER\R_SERVER). Weitere Informationen finden Sie unter [Machine Learning-Server für Windows installieren](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) oder [Installieren von R Server 9.1 für Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="next-steps"></a>Nächste Schritte

+ [Paketinformationen abrufen](determine-which-packages-are-installed-on-sql-server.md)
+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Remoteverwaltung für R-Pakete aktivieren](r-package-how-to-enable-or-disable.md)
+ [RevoScaleR-Funktionen für die Verwaltung von R-Paketen](use-revoscaler-to-manage-r-packages.md)
+ [R-Paketsynchronisierung](package-install-uninstall-and-sync.md)
+ [miniCRAN für das lokale R-Paketrepository](create-a-local-package-repository-using-minicran.md)
