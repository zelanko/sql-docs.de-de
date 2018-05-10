---
title: Standardbibliotheken R und Python-Paket in SQL Server R und SQL Server-Machine Learning | Microsoft Docs
description: R und Python-Pakete, die Installation von SQLServer für R-Services, R-Server, Machine Learning Services (Datenbankintern) und Machine Learning-Server (eigenständig)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ee2c8124cf3487ca300c0b08ea113c8e66b114f4
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Standard-R und Python-Paketen in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel behandelt die Paket-Bibliotheken, den Speicherort und Versionen der R und Python-Pakete, die mit SQL Server installiert. 

## <a name="using-the-default-instance-library"></a>Mithilfe der Standard-Instanz-Bibliothek

Bei der Installation von Machine Learning mit SQL Server wird eine einzelnes Paket-Bibliothek auf Instanzebene für jede Sprache erstellt, die Sie installieren. 

Alle Skripts oder Codeabschnitts, führt in-auf SQL Server-Datenbank muss Funktionen aus der Instanz-Bibliothek geladen werden. SQL Server kann nicht mit anderen Bibliotheken installierte Pakete zugreifen. Dies betrifft auch Remoteclients. Beim Herstellen einer Verbindung mit dem Server von einem Remoteclient, können alle R oder Python-Code, der in der Server-computekontext ausgeführt werden soll nur Pakete, die in der Bibliothek für die Instanz installiert.

Um Serverressourcen zu schützen, wird die Standardbibliothek Instanz einem gesicherten Ordner installiert, die mit SQL Server registriert ist, und kann nur von einem Computeradministrator geändert werden. Wenn Sie nicht der Besitzer des Computers sind, müssen Sie möglicherweise Berechtigung durch einen Administrator für das Installieren der Pakete in dieser Bibliothek zu erhalten. 

Auch wenn Sie den Computer besitzen, sollten Sie die Nützlichkeit der jedes bestimmten R oder Python-Paket in einer serverumgebung, vor dem Hinzufügen des Pakets auf die Instanz-Bibliothek. Betrachten Sie Faktoren wie z. B. die Größe der Paketdateien und Anforderungen für mehrere Versionen sowie, ob das Paket Netzwerk oder über das Internet erfordert Zugriff.

### <a name="in-database-engine-instance-file-paths"></a>Im Datenbankmodul-Instanz Dateipfade

Die folgende Tabelle zeigt den Speicherort von R und Python für Version und Datenbank Kombinationen der Datenbankmodul-Instanz. 

|Version | Instanzname|Standardpfad|
|--------|--------------|------------|
| SQL Server 2016 |Standardinstanz| C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQL Server 2016 |Benannte Instanz | C:\Programme\Microsoft SQL Server\MSSQL13. < Instanzname > \R_SERVICES\library|
| SQLServer 2017 mit R|Standardinstanz | C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQLServer 2017 mit R|Benannte Instanz| C:\Program Files\Microsoft SQL Server\MSSQL14. MyNamedInstance\R_SERVICES\library |
| SQLServer 2017 mit Python |Standardinstanz | C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\library |
| SQLServer 2017 mit Python|Benannte Instanz| C:\Programme\Microsoft SQL Server\MSSQL14. < Instanzname > \PYTHON_SERVICES\library |

### <a name="standalone-server-file-paths"></a>Eigenständige Server Dateipfade 

Die folgende Tabelle enthält die Standardpfade der Binärdateien aus, wenn SQL Server 2016 R Server (eigenständig) oder SQL Server 2017 Machine Learning-Server (eigenständig) Server installiert ist. 

|Version| Installation|Standardpfad|
|------|------|------|
| SQL Server 2016|R-Server (eigenständig)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning-Server mit R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning-Server mit Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Wenn Sie andere Ordner mit ähnlichen Unterordnernamen und Dateien feststellen, haben Sie wahrscheinlich eine eigenständige Installation von Microsoft R Server oder [Machine Learning-Server](https://docs.microsoft.com/machine-learning-server/). Diese Serverprodukte haben unterschiedliche Installationsprogramme und Pfade (nämlich c:\Programme\Microsoft Files\Microsoft\R Server\R_SERVER oder c:\Programme\Microsoft Files\Microsoft\ML SERVER\R_SERVER). Weitere Informationen finden Sie unter [Machine Learning-Server für Windows installieren](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) oder [Installieren von R Server 9.1 für Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="what-is-included-in-a-default-installation"></a>Was ist in einer Standardinstallation enthalten.

Dieser Abschnitt fasst die R und Python Features in einer Standardinstallation zusammen.

### <a name="r-components"></a>R-Komponenten

Komponenten umfassen Microsofts Verteilung der Open-Source-R als [Microsoft R Open](https://mran.microsoft.com/open). Base R-Pakete enthalten grundlegende Funktionen, z. B. **Stats** und **Utils**. Sie können ausführen `installed.packages(priority = "base")` um eine Liste der Pakete zurück. Eine Basisinstallation von R hinaus zahlreiche beispieldatasets und R-Standardtools wie "rgui.exe" (eine einfache interaktive-Editor) und RTerm (ein R-Eingabeaufforderung).

Microsoft-Pakete enthalten ["revoscaler"](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) für remote rechenkontexte, streaming, Rx-Funktionen für den Datenimport und die Transformation für die Ausführung paralleler, Modellierung und Visualisierung und Analyse. [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package) fügt Machine Learning in r Modellierung Zu den Paketen gehören [OlapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) zum Schreiben von MDX-Anweisungen in R und [Sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) zum Einschließen von R-Skripts in gespeicherten Prozeduren.


|Release             | R-version       | Microsoft-Pakete    |
|--------------------|-----------------|-----------------------|
| SQL Server 2016 R Services | 3.2.2   | "Revoscaler", sqlrutil  |
| SQL Server 2017-Machine Learning-Dienste| 3.4.3 | "Revoscaler", MicrosoftML, OlapR, sqlrutil|

Sie können Pakete und vorinstallierte Modelle mit SQL Server 2016 R Services durch die Supportrichtlinie für moderne Lifecycle Bindung hinzufügen. Bindung ändert das Dienstmodell. Standardmäßig werden R-Pakete nach der ersten Installation über Servicepacks und kumulativen Updates aktualisiert. Zusätzliche Pakete und vollständige Versionsupgrade für R-Kernkomponenten sind nur möglich, über Produktupgrades (von SQL Server 2016, SQL Server-2017) oder durch das Binden von R mit Microsoft Machine Learning-Server unterstützen. Weitere Informationen finden Sie unter [R aktualisieren und Python-Komponenten in SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="python-components"></a>Python-Komponenten

SQL Server-2017 werden Python-Serverkomponenten hinzufügt. Wenn Sie die Python-Language-Option auswählen, wird eine Anaconda-Verteilung installiert. Zusätzlich zu den Python-Code-Bibliotheken enthält die Standardinstallation Beispieldaten, Komponententests und Beispielskripts. 

Microsoft-Pakete enthalten [Revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) als die Python-Entsprechung von "revoscaler", Streaming, parallele Ausführung von Rx-Funktionen für Datenimport und Transformation, Modellierung, Visualisierung und Analyse. Ein anderes Python-Paket ist [Microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) für Training und Transformationen, Bewertung, Text und Image-Analyse und merkmalsextraktion für Werte von vorhandenen Daten ableiten.

SQL Server 2017 Machine Learning ist die erste Version R und Python-Unterstützung verfügen.

|Release             | Anaconda-version| Microsoft-Pakete    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017-Machine Learning-Dienste  | 4.2 über Python 3.5 | Revoscalepy microsoftml |

Nach der anfänglichen Installation Python-Pakete werden über Servicepacks und kumulativen Updates aktualisiert, aber vollständige Versionsupgrade sind nur möglich, indem Unterstützung der Python an Microsoft Machine Learning-Server binden. Weitere Informationen finden Sie unter [R aktualisieren und Python-Komponenten in SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="administrative-permissions-for-package-installation"></a>Administratorberechtigungen für die Paketinstallation

Die erforderlichen Berechtigungen für die Paketinstallation wurden zwischen SQL Server 2016 und SQL Server-2017 geändert.

+ In SQL Server 2016 ist Administratorzugriff erforderlich ist, für die Installation der neuen R-Pakete.
+ In SQL Server-2017 können Sie weiterhin Pakete als Administrator für R und Python zu installieren, und dies ist wahrscheinlich die einfachste Methode. 

    Die DDL-Anweisung, externe Bibliothek erstellen kann den Datenbankadministrator, um Pakete zu installieren, ohne Verwendung von R-Tools. 

    Wenn Sie die Paket-Verwaltungsfunktion für Machine Learning-Server verwenden, können Sie "revoscaler" verwenden, Installieren von R-Pakete auf Datenbankebene. Der Datenbankadministrator muss das Feature aktivieren, und gewähren Sie Benutzern die Möglichkeit, ihre eigenen Pakete auf jede Datenbank separat zu installieren. Weitere Informationen finden Sie unter [aktivieren paketverwaltung mit DDLs](r-package-how-to-enable-or-disable.md).

### <a name="user-libraries-are-not-supported"></a>Benutzerbibliotheken werden nicht unterstützt.

Benutzer, die ein Paket nicht häufig an einem sicheren Speicherort installieren können, installieren ein Paket in einer Benutzerbibliothek verwenden. Allerdings ist dies nicht möglich, in der SQL Server-Umgebung. Dateisystemzugriff ist in der Regel auf dem Server beschränkt und auch wenn Sie in einen Benutzer Dokumentordner auf dem Server Administratorrechte sowie über Zugriff verfügt, nicht externes Skript-Laufzeit, die in SQL Server ausgeführt wird Pakete außerhalb der Standardinstanz installiert verfügbar Bibliothek. Problemumgehungen sind allerdings möglich. Tipps zum Beheben von Problemen im Zusammenhang mit benutzerbibliotheken, finden Sie unter [Problemumgehungen für R-benutzerbibliotheken](packages-installed-in-user-libraries.md).

## <a name="next-steps"></a>Nächste Schritte

+ [Abrufen von Paketinformationen](determine-which-packages-are-installed-on-sql-server.md)
+ [Installieren Sie neue R-Pakete](install-additional-r-packages-on-sql-server.md)
+ [Installieren neuer Python-Pakete](../python/install-additional-python-packages-on-sql-server.md)
+ [Aktivieren der Remoteverwaltung der R-Paket](r-package-how-to-enable-or-disable.md)
+ [RevoScaleR-Funktionen für die Verwaltung der R-Paket](use-revoscaler-to-manage-r-packages.md)
+ [Synchronisierung der R-Paket](package-install-uninstall-and-sync.md)
+ [MiniCRAN für das Repository von R-Paket](create-a-local-package-repository-using-minicran.md)
