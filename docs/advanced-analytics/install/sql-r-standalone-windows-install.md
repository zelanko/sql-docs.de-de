---
title: Installieren von SQL Server 2016 R Server (eigenständig) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e5457698120536247ad1823b842bb1b8e52b484d
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979282"
---
# <a name="install-sql-server-2016-r-server-standalone"></a>Installieren von SQL Server 2016 R Server (eigenständig)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird beschrieben, wie Sie mit SQL Server 2016-Setup zum Installieren der eigenständigen Version von **SQL Server 2016 R Services**.

## <a name="bkmk_prereqs"> </a> Checkliste für die vor der Installation

SQL Server 2016 ist erforderlich. Wenn Sie SQL Server 2017 haben, installieren Sie [Machine Learning Server (eigenständig) für SQL Server 2017](sql-machine-learning-standalone-windows-install.md) stattdessen.

Wenn Sie alle früheren Versionen von Revolution Analytics-Tools bzw. die Pakete installiert haben, müssen Sie diese zunächst deinstallieren. 

## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Installieren einer Patchanforderung 

Microsoft hat ein Problem bei der speziellen Version von Microsoft VC++ 2013 Runtime-Binärdateien erkannt, die von SQL Server als vorausgesetzte Komponenten installiert werden. Wenn dieses Update an den VC++ Runtime-Binärdateien nicht installiert wird, können bei SQL Server in bestimmten Szenarios Stabilitätsprobleme auftreten. Bevor Sie SQL Server installieren, sollten Sie entsprechend den Anweisungen unter [Versionsanmerkungen zu SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) vorgehen, um festzustellen, ob Ihr Computer einen Patch für die VC-Runtime-Binärdateien benötigt.  

## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Setup-Assistenten für SQL Server 2016. Es wird empfohlen, dass Sie Servicepack 1 oder höher installieren.

2. Auf der **Installation** auf **neue R Server (Standalone) Installation**.
    
     ![Starten Sie das Setup von R Server (eigenständig)](media/2016-setup-installation-rsvr.png "starten Sie das Setup von R Server (eigenständig)")
    
3.  Auf der Seite **Feature selection** (Funktionsauswahl) sollte die folgende Option bereits aktiviert sein:
    
    **R Server (eigenständig)**  
    
    ![Die Funktionsauswahl für R Server (eigenständig)](media/2016setup-rserver-features.png "Funktionsauswahl für R Server (eigenständig)")
    
    Alle anderen Optionen können ignoriert werden. 
    
    > [!NOTE]
    > Vermeiden Sie die Installation der **gemeinsam genutzte Funktionen** Wenn Sie Setup auf einem Computer ausführen, bei der es dem R Services bereits für SQL Server in-Database-Analyse installiert wurde. Dadurch wird die doppelte Bibliotheken erstellt.
    > 
    > Während der R-Skripts in SQL Server von SQL Server nicht in Konflikt mit von anderen Datenbank-Engine-Dienste verwendete Arbeitsspeicher verwaltet werden, wird der eigenständigen R Servers verfügt über keine solche Einschränkungen, und bei anderen Datenbankvorgängen beeinträchtigen kann.
    > 
    > Wir empfehlen im allgemeinen Installation von R Server (eigenständig) auf einem separaten Computer von SQL Server R Services (Datenbankintern).

4.  Akzeptieren Sie die Lizenzbedingungen für das Herunterladen und Installieren von Microsoft R Open. Wenn die Schaltfläche **Annehmen** deaktiviert wird, können Sie auf **Weiter**klicken.
    
    Installation dieser Komponenten und alle erforderlichen Komponenten, die sie benötigen könnte, die kann eine Weile dauern.
    
5.  Überprüfen Sie Ihre Auswahl auf der Seite **Installationsbereit** , und klicken Sie anschließend auf **Installieren**.

## <a name="default-installation-folders"></a>Standard-Installationsordner

Bei der Installation von R-Server mit SQL Server-Setup werden die R-Bibliotheken installiert, in einem Ordner mit dem zugeordneten SQL Server-Version, die Sie bei der Installation verwendet wird. In diesem Ordner finden Sie auch Beispieldaten, die Dokumentation für die R-Basispakete und Dokumentation der R-Tools und der Common Language Runtime.

Allerdings werden bei Installation von Microsoft R Server mit dem separate Windows Installer (nicht SQL-Setup), oder führen Sie ein upgrade des separaten Windows Installers, die R-Bibliotheken in einem anderen Ordner installiert.

Obwohl dagegen empfohlen, wenn Sie eine Instanz von SQL Server R Services (Datenbankintern) auch auf dem gleichen Computer installiert, wird eine zweite Kopie von R-Bibliotheken und Tools in einem anderen Ordner installiert.

Die folgende Tabelle enthält die Pfade für jede Installation.

|Version| Installationsmethode | Standardordner|
|----|----|----|
|R-Server (eigenständig) |SQL Server 2016-Setup-Assistenten|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R-Server (eigenständig) |Eigenständiger Installer für Windows|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Machine Learning-Server (eigenständig) |  SQL Server 2017-Setup-Assistenten, mit der Option "R-Sprache" |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Machine Learning-Server (eigenständig) |  SQL Server 2017-Setup-Assistenten, mit der Option für Python-Sprache |`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Machine Learning-Server (eigenständig) |  Eigenständiger Installer für Windows |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|R Services (In-Database) |SQL Server 2016-Setup-Assistenten|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Machine Learning-Dienste (datenbankintern) |SQL Server 2017-Setup-Assistenten, mit der Option "R-Sprache"|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  |
|Machine Learning-Dienste (datenbankintern) |SQL Server 2017-Setup-Assistenten, mit der Option für Python-Sprache| `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |

## <a name="development-tools"></a>Entwicklungstools

Eine integrierte Entwicklungsumgebung ist nicht als Teil des Setups installiert. Zusätzliche Tools sind nicht erforderlich, da alle standardmäßigen Tools eingeschlossen werden würde, die mit einer Verteilung von R oder Python bereitgestellt werden.

Es wird empfohlen, dass Sie, die neue Version von versuchen [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] oder [Python für Visual Studio](https://docs.microsoft.com/visualstudio/python/installing-python-support-in-visual-studio). Visual Studio unterstützt sowohl R und Python, sowie Tools zur Datenbankentwicklung, Verbindungen mit SQL Server und BI-Tools. Sie können jedoch bevorzugten Entwicklungsumgebung nutzen, einschließlich der RStudio.
  
## <a name="get-help"></a>Hilfe

Benötigen Sie Hilfe bei der Installation oder Aktualisierung? Finden Sie Antworten auf häufig gestellte Fragen und bekannte Probleme finden Sie im folgenden Artikel:

* [Upgrade und Installation – häufig gestellte Fragen – Machine Learning-Dienste](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Versuchen Sie diese benutzerdefinierten Berichte, um den Installationsstatus der Instanz zu überprüfen und Behandeln häufig auftretender Probleme.

* [Benutzerdefinierte Berichte für SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen beginnen, und die Grundlagen der Funktionsweise von R mit SQL Server. Der nächste Schritt ist finden Sie in den folgenden Links:

+ [Tutorial: Ausführen von R in T-SQL-](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Beispiele für Machine Learning, die auf realen Szenarien basieren, finden Sie unter [Machine learning-Tutorials](../tutorials/machine-learning-services-tutorials.md).

