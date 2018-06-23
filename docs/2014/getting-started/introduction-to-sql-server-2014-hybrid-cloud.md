---
title: Einführung in SQL Server 2014 Hybridcloud | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc42752-1fcd-4ab9-8194-c3001ea342e7
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fc36b9e907a9399a47b2d4f3a743e3f83bfa7a31
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046267"
---
# <a name="introduction-to-sql-server-2014-hybrid-cloud"></a>Einführung in SQL Server 2014 Hybrid Cloud
 Für die meisten Anwendungen gelten eine Reihe zentraler Herausforderungen. Dazu gehören hohe Effizienz, maximaler Geschäftswert, komplexe Hardwarekonfigurationen, Deckung von Bedarfsspitzen und die Einhaltung branchen- und unternehmensspezifischer Auflagen. Angesichts all dieser Faktoren kann sich die Entwicklung einer unternehmensfähigen Technologie sehr schwierig gestalten. Die Microsoft Hybrid Cloud-Strategie wird diesen Anforderungen gerecht, indem sie Unterstützung für herkömmliche, private Clouds, öffentliche Clouds und Hybrid Cloud-Umgebungen bietet. 
 
 Wenn Ihr Unternehmen eine flexible IT-Infrastruktur, die bei Bedarf skaliert werden können benötigt, können Sie eine private Cloud in Ihrem Rechenzentrum oder eine öffentliche Cloud in globaler Daten zwischen Azure-Rechenzentren erstellen. Wenn Sie Ihr Rechenzentrum erweitern, um es mit der öffentlichen Cloud zu kombinieren, sprechen wird von einem Hybrid Cloud-Modell. 
 
 In diesem Thema werden die SQL Server 2014-Funktionen vorgestellt, die die Hybrid Cloud-Szenarien unterstützen. Ausführliche Informationen zur Microsoft Hybrid Cloud-Strategie und SQL Server, finden Sie unter [Hybrid IT für SQL Server](http://www.microsoft.com/sqlserver/solutions-technologies/hybrid-It.aspx) Website. 
 
## <a name="sql-server-azure-and-hybrid-cloud"></a>SQLServer, Azure und Hybridcloud 
 Microsoft-Technologien ermöglichen folgende Arten der Codeausführung: lokal und in der Cloud, cloudbasiert auf der Grundlage lokaler Daten oder vollständig in der Cloud, wobei Ihnen die Kapazitäten mehrerer Rechenzentren zur Verfügung stehen. Sie können Ihre Anwendungen also nach Ihrem eigenen Zeitplan in die Cloud verlagern und den Wert bereits getätigter IT-Investitionen dabei voll ausschöpfen. 
 
 In diesem Artikel konzentrieren wir uns auf Hybrid Cloud-Szenarien, die von einer lokalen SQL Server auf die öffentliche Azure-Cloud-Angebote umfassen: [SQL Server in Azure Virtual Machines](http://msdn.microsoft.com/library/azure/jj823132.aspx) und [Azure-Speicher](http://www.azure.com/documentation/services/storage/). Im Einzelnen erörtern wir die folgenden Szenarien: 
 
-  [Sichern und Wiederherstellen von Datenbanken zu/von Azure-Speicher](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#backup) 
 
-  [Vorhalten von Datenbankreplikaten auf virtuellen Azure-Computern](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#replica) 
 
-  [Speichern von SQL Server-Datendateien in Azure-Speicher](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#store) 
 
-  [Migrieren Sie vorhandene SQL Server-Datenbanken zu Azure Virtual Machines](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#migrate) 
 
### <a name="hybrid-cloud-scenarios-for-sql-server-and-microsoft-azure"></a>Hybrid Cloud-Szenarien für SQLServer und Microsoft Azure 
 
#### <a name="backup"></a> Sichern und Wiederherstellen von Datenbanken zu/von Azure-Speicher 
 Eine der grundlegendsten Administratoraufgaben ist die Sicherung und Wiederherstellung von Datenbanken. Mit SQL Server und Azure können Sie zuverlässige datenbanksicherungen in der Cloud erstellen. 
 
 Verwenden der Sicherung und Wiederherstellung von SQL Server mit Azure-Speicher als Sicherungsziel Hauptvorteile gehören: 
 
-  Unbegrenzter kostengünstiger Speicher 
 
-  Hochverfügbarer Speicher (keine Datenverluste dank geografischer Replikation) 
 
-  Externer Speicher zur Erfüllung der Notfallwiederherstellungs- und Kompatibilitätsanforderungen 
 
-  Vereinfachte Remotesicherung und -wiederherstellung 
 
 Im Folgenden sind die Sicherungs- und Wiederherstellungsfunktionen von SQL Server aufgeführt, die für lokale Szenarien und die Cloud verfügbar sind: 
 
-  Die [SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md) Feature ermöglicht Ihnen, Azure-Speicher sichern, indem Sie URL als Sicherungsziel angeben. Mit dieser Funktion können Sie manuelle Sicherungen ausführen oder eine eigene Sicherungsstrategie konfigurieren. Dabei gehen Sie genauso vor wie bei der lokalen Speicherung oder anderen externen Speicheroptionen. 
 
-  Die [Sicherungsverschlüsselung](../relational-databases/backup-restore/backup-encryption.md) Funktion ermöglicht es Ihnen, zum Verschlüsseln der Daten beim Erstellen einer Sicherung für die Speicherziele: lokale und Azure-Speicher. 
 
-  Die [Sicherungskomprimierung (SQL Server)](../relational-databases/backup-restore/backup-compression-sql-server.md) Feature ermöglicht Ihnen, eine Sicherung erstellen, die kleiner als eine unkomprimierte Sicherung derselben Daten ist. Die Komprimierung einer Sicherung erfordert weniger Geräte-E/A-Vorgänge und steigert deshalb deutlich die Sicherungsleistung. Dies kann besonders dann von Vorteil sein, wenn Sie Sicherungsdateien im Azure-Speicher zu speichern. 
 
-  Die [SQL Server Managed Backup to Azure](https://msdn.microsoft.com/library/dn606152(v=sql.120).aspx) Funktion ermöglicht Ihnen, automatisch backup SQL Server-Datenbanken auf [Azure-Speicher](http://www.azure.com/documentation/services/storage/). Mit dieser Funktion können Sie SQL Server konfigurieren, um die Sicherungsstrategie zu verwalten und Sicherungen für eine einzelne oder mehrere Datenbanken zu planen oder um Standardwerte auf Instanzebene festzulegen. 
 
-  Die [SQL Server Backup to Azure Tool](http://www.microsoft.com/download/details.aspx?id=40740) können Sicherungen im Azure-Blob-Speicher außerdem verschlüsselt und komprimiert Sie SQL Server-Sicherungen lokal oder in der Cloud gespeichert. Dieses Tool unterstützt eine einzelne Cloudsicherungsstrategie für mehrere Versionen von SQL Server wie SQL Server 2005, 2008, 2008 R2 und 2014. 
 
#### <a name="replica"></a> Vorhalten von Datenbankreplikaten auf virtuellen Azure-Computern 
 Ihr Geschäftserfolg hängt maßgeblich davon ab, ob Sie eine zuverlässige Notfallwiederherstellungslösung für Ihre Datenbanken implementiert haben. Die meisten Kunden müssen einen eigenen Standort für die Notfallwiederherstellung einrichten und zusätzliche Hardware für Datenbankreplikate anschaffen. Mit SQL Server und Azure können Sie ein oder mehrere Replikate Ihrer Datenbanken in der Cloud speichern. 
 
 Die wichtigsten Vorzüge von Speicherung sekundärer Replikate in Azure umfassen: 
 
-  Kostengünstige Notfallwiederherstellungslösung 
 
-  Transparentes Anwendungsfailover 
 
-  Verfügbare Replikate zur Auslagerung von Lesearbeitslasten und Sicherungen 
 
 Sie können sekundäre Replikate in Azure mithilfe einer der folgenden Methoden verwalten: 
 
-  Die [Assistent zum Hinzufügen eines Azure-Replikaten](http://msdn.microsoft.com/library/dn463980\(v=sql.120\).aspx) können Sie eine oder mehrere Replikate Ihrer Datenbanken auf einem virtuellen Computer in Azure für die notfallwiederherstellung bereitstellen. 
 
-  AlwaysOn-Verfügbarkeitsgruppen, Datenbankspiegelung und Protokollversand sind die gängigsten Technologien, mit denen Sie die Hochverfügbarkeits- und Notfallwiederherstellungsanforderungen Ihrer Anwendung erfüllen können. Informationen finden Sie unter [hohe Verfügbarkeit und Notfallwiederherstellung für SQL Server in Azure Virtual Machines](http://msdn.microsoft.com/library/azure/jj870962.aspx). 
 
#### <a name="store"></a> Speichern von SQL Server-Datendateien in Azure-Speicher 
 Speichern von lokalen SQL Server-Datendateien in Azure-Speicher bietet eine flexible, zuverlässige und unbegrenzte offsitespeicherung für Ihre Datenbanken. Beginnend mit SQL Server 2014, können Sie [SQL Server-Datendateien in Miceosoft Azure](https://docs.microsoft.com/sql/relational-databases/databases/sql-server-data-files-in-microsoft-azure) zum Speichern von SQL Server-Datenbankdateien im Azure-Speicher. Mit dieser Funktion können Sie Daten verschieben und Protokolldateien aus einer lokalen Datenbank im Azure-Speicher Weiterleitungstopologie dem Computeknoten SQL Server lokal ausgeführt wird. Dieses Feature ermöglicht es Ihnen, unbegrenzte Speicherkapazitäten im Azure-Speicher. 
 
 Die wichtigsten Vorteile des Speicherns von SQL Server-Datendateien Azure-Speicher enthalten: 
 
-  Unbegrenzter kostengünstiger Speicher im Azure-Speicher 
 
-  Optimale Lösung, um Lesezugriffe auf ältere Daten in die Cloud auszulagern und auf diese Weise lokale Berichterstellungsanwendungen zu entlasten. 
 
-  Einfachere Notfallwiederherstellung durch die Trennung von Serverinstanz (eine SQL Server-Instanz) und Daten (SQL Server-Datendateien). Dadurch können Sie problemlos anfügen die Datenbank in eine andere Instanz von SQL Server in einer lokalen Umgebung oder in einem virtuellen Azure-Computer bei einem Notfall. 
 
#### <a name="migrate"></a> Migrieren Sie vorhandene SQL Server-Datenbanken zu Azure Virtual Machines 
 Das Cloud Computing eröffnet Unternehmen eine Reihe überzeugender Vorteile, z. B. die Nutzung unbegrenzt virtualisierbarer Ressourcen, die nutzungsbasiert abgerechnet werden. Darüber hinaus können Sie die in der Cloud verfügbaren Rechenzentren nutzen, anstatt eigene Rechenzentren einzurichten und zu unterhalten. Auf diese Weise lassen sich IT- und Hardwarekosten senken. 
 
 Mit [SQL Server in Azure Virtual Machines](http://msdn.microsoft.com/library/azure/jj823132.aspx), Sie können vorhandene lokale Anwendungen in Azure mit minimalen oder gar keine codeänderungen. Administratoren und Entwickler verwenden dabei dieselben Entwicklungs- und Verwaltungstools wie für ihre lokalen Projekte. 
 
 Verschieben einer Datenbank aus einer lokalen SQL Server mit SQL Server auf einem virtuellen Azure-Computer in der Regel ausführen, stehen diese Pfade: 
 
-  **Verschieben der Datenbank:** stehen zahlreiche Tools und Techniken, vorhandene lokale Datenbanken zu SQL Server-virtuellen Computern in Azure zu verschieben. Richtlinien und Empfehlungen zur Migration zu SQL Server in Azure Virtual Machines finden Sie unter [Vorbereitung auf die Migration zu SQL Server auf Azure Virtual Machines](http://msdn.microsoft.com/library/dn133142.aspx) sowie [Migrieren zu SQL Server auf einem virtuellen Azure-Computer ](http://msdn.microsoft.com/library/jj156165.aspx). 
 
   Darüber hinaus beginnend mit SQL Server 2014, einen Assistenten für neue [Bereitstellen einer SQL Server-Datenbank auf einem Microsoft Azure Virtual Machines](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) steht für die Sie zum Bereitstellen der Datenbank in eine andere SQL Server-Instanz, die auf einem virtuellen Azure-Computer ausgeführt. 
 
-  **Verschieben des gesamten virtuellen Computers:** Sie können eine eigene SQL Server-virtuellen Computern in Azure oder von einem Plattformimage erstellen. Anschließend können Sie einen Datenträger, auf dem bereits Daten gespeichert sind, hochladen und an den virtuellen Computer anfügen, oder Sie fügen einen leeren Datenträger an den virtuellen Computer an. Mit einer Instanz des SQL Server-Daten auf Azure Virtual Machines mit angefügten Datenträgern bietet einer weiteren permanenten speicherlösung für Ihre Daten- und Anwendungsdaten verwendet werden. Umfassende Informationen und Vorgehensweisen finden Sie unter [SQL Server-Bereitstellung in Azure Virtual Machines](http://msdn.microsoft.com/library/dn133141.aspx). 
 
 Wenn Sie planen, die Anwendungsebenen (z. B. die Darstellungsebene arbeitet, der Geschäftslogikebene und der Datenbankebene) zu virtuellen Computern in Azure verschieben, es wird empfohlen, dass Sie die Empfehlungen im Überprüfen der [Anwendungsmuster und Entwicklung Strategien für die SQL Server in Azure Virtual Machines](http://msdn.microsoft.com/library/dn574746.aspx) Artikel. Das Ziel dieses Artikels ist um Lösungsarchitekten und-Entwicklern eine Grundlage für gute Anwendungsarchitektur und erleichtert befolgen können, wenn die Migration bestehender Anwendungen zu Azure sowie Entwicklung neuer Anwendungen in Azure bereitzustellen. In diesem Artikel wird jedes Anwendungsmuster unter den folgenden Gesichtspunkten beleuchtet: lokales Szenario, entsprechende cloudfähige Lösung und zweckdienliche technische Empfehlungen. Darüber hinaus behandelt der Artikel die Azure-spezifische Entwicklungsstrategien, damit Sie Ihre Anwendungen ordnungsgemäß entwerfen können. 
 
## <a name="see-also"></a>Siehe auch 
 [SQL Server 2014 CTP2-Produkthandbuch](http://www.microsoft.com/download/details.aspx?id=39269)  
 [SQL Server 2014](http://www.microsoft.com/sqlserver/sql-server-2014.aspx)  
 [Blogreihe über Microsoft SQL Server Hybrid Cloud](http://blogs.msdn.com/b/azure/archive/2013/10/16/microsoft-sql-server-hybrid-cloud-blog-series.aspx)  
 [Migrieren von datenorientierten Anwendungen zu Azure](http://msdn.microsoft.com/library/jj156154.aspx) 
 
 