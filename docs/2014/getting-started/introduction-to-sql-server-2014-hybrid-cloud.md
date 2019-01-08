---
title: Einführung in SQL Server 2014 Hybridcloud | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 6dc42752-1fcd-4ab9-8194-c3001ea342e7
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 026ed516989bde6f2c0b305d6af159f13a82f156
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358452"
---
# <a name="introduction-to-sql-server-2014-hybrid-cloud"></a>Einführung in SQL Server 2014 Hybrid Cloud
 Für die meisten Anwendungen gelten eine Reihe zentraler Herausforderungen. Dazu gehören hohe Effizienz, maximaler Geschäftswert, komplexe Hardwarekonfigurationen, Deckung von Bedarfsspitzen und die Einhaltung branchen- und unternehmensspezifischer Auflagen. Angesichts all dieser Faktoren kann sich die Entwicklung einer unternehmensfähigen Technologie sehr schwierig gestalten. Die Microsoft Hybrid Cloud-Strategie wird diesen Anforderungen gerecht, indem sie Unterstützung für herkömmliche, private Clouds, öffentliche Clouds und Hybrid Cloud-Umgebungen bietet. 
 
 Wenn Ihr Unternehmen eine flexible IT-Infrastruktur erforderlich, die bei Bedarf skaliert werden können sind, können Sie eine private Cloud in Ihrem Rechenzentrum oder eine öffentliche Cloud in Azure global-Rechenzentren erstellen. Wenn Sie Ihr Rechenzentrum erweitern, um es mit der öffentlichen Cloud zu kombinieren, sprechen wird von einem Hybrid Cloud-Modell. 
 
 In diesem Thema werden die SQL Server 2014-Funktionen vorgestellt, die die Hybrid Cloud-Szenarien unterstützen. Ausführliche Informationen zur Microsoft Hybrid Cloud-Strategie und zu SQL Server finden Sie auf der Website [Hybrid IT für SQL Server](https://www.microsoft.com/sqlserver/solutions-technologies/hybrid-It.aspx) . 
 
## <a name="sql-server-azure-and-hybrid-cloud"></a>SQLServer, Azure und Hybridcloud 
 Microsoft-Technologien ermöglichen folgende Arten der Codeausführung: lokal und in der Cloud, cloudbasiert auf der Grundlage lokaler Daten oder vollständig in der Cloud, wobei Ihnen die Kapazitäten mehrerer Rechenzentren zur Verfügung stehen. Sie können Ihre Anwendungen also nach Ihrem eigenen Zeitplan in die Cloud verlagern und den Wert bereits getätigter IT-Investitionen dabei voll ausschöpfen. 
 
 In diesem Artikel konzentrieren wir uns auf Hybrid Cloud-Szenarien, die von einem lokalen SQL Server zum öffentlichen Azure-Cloud-Angebote umfassen: [SQLServer auf virtuellen Azure-Computern](https://msdn.microsoft.com/library/azure/jj823132.aspx) und [Azure-Speicher](http://www.azure.com/documentation/services/storage/). Insbesondere erörtern wir die folgenden Szenarien: 
 
-  [Sichern und Wiederherstellen von Datenbanken in und aus Azure Storage](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#backup) 
 
-  [Vorhalten von Datenbankreplikaten in Azure Virtual Machines](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#replica) 
 
-  [Store SQL Server-Datendateien im Azure-Speicher](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#store) 
 
-  [Migrieren Sie vorhandene SQL Server-Datenbanken zu Azure Virtual Machines](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#migrate) 
 
### <a name="hybrid-cloud-scenarios-for-sql-server-and-microsoft-azure"></a>Hybrid Cloud-Szenarien für SQLServer und Microsoft Azure 
 
#### <a name="backup"></a> Sichern und Wiederherstellen von Datenbanken in und aus Azure Storage 
 Eine der grundlegendsten Administratoraufgaben ist die Sicherung und Wiederherstellung von Datenbanken. Mit SQL Server und Azure können Sie problemlos Ihre Datenbanken in der Cloud sichern. 
 
 Die wichtigsten Vorteile der Verwendung der Funktionen sichern und Wiederherstellen von SQL Server mit Azure Storage als Sicherungsziel gehören: 
 
-  Unbegrenzter kostengünstiger Speicher 
 
-  Hochverfügbarer Speicher (keine Datenverluste dank geografischer Replikation) 
 
-  Externer Speicher zur Erfüllung der Notfallwiederherstellungs- und Kompatibilitätsanforderungen 
 
-  Vereinfachte Remotesicherung und -wiederherstellung 
 
 Im Folgenden sind die Sicherungs- und Wiederherstellungsfunktionen von SQL Server aufgeführt, die für lokale Szenarien und die Cloud verfügbar sind: 
 
-  Die [SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md) Feature können Sie in Azure Storage sichern, indem Sie URL als Sicherungsziel angeben. Mit dieser Funktion können Sie manuelle Sicherungen ausführen oder eine eigene Sicherungsstrategie konfigurieren. Dabei gehen Sie genauso vor wie bei der lokalen Speicherung oder anderen externen Speicheroptionen. 
 
-  Die [Sicherungsverschlüsselung](../relational-databases/backup-restore/backup-encryption.md) Feature ermöglicht es Ihnen, zum Verschlüsseln der Daten beim Erstellen einer Sicherung für Ihre Speicherziele: lokale und Azure Storage. 
 
-  Die [Sicherungskomprimierung (SQL Server)](../relational-databases/backup-restore/backup-compression-sql-server.md) Feature können Sie eine Sicherung erstellen, die kleiner ist als eine nicht komprimierte Sicherung derselben Daten. Die Komprimierung einer Sicherung erfordert weniger Geräte-E/A-Vorgänge und steigert deshalb deutlich die Sicherungsleistung. Dies kann viele Vorteile bringen, beim Sichern von Dateien im Azure-Speicher zu speichern. 
 
-  Die [SQL Server Managed Backup für Azure](https://msdn.microsoft.com/library/dn606152(v=sql.120).aspx) Funktion ermöglicht Ihnen, automatisch Sicherungen SQL Server-Datenbanken [Azure Storage](http://www.azure.com/documentation/services/storage/). Mit dieser Funktion können Sie SQL Server konfigurieren, um die Sicherungsstrategie zu verwalten und Sicherungen für eine einzelne oder mehrere Datenbanken zu planen oder um Standardwerte auf Instanzebene festzulegen. 
 
-  Die [SQL Server Backup to Azure Tool](https://www.microsoft.com/download/details.aspx?id=40740) ermöglicht die Sicherung in Azure Blob Storage. außerdem verschlüsselt und komprimiert lokal oder in der Cloud gespeicherte SQL Server-Sicherungen. Dieses Tool unterstützt eine einzelne Cloudsicherungsstrategie für mehrere Versionen von SQL Server wie SQL Server 2005, 2008, 2008 R2 und 2014. 
 
#### <a name="replica"></a> Vorhalten von Datenbankreplikaten in Azure Virtual Machines 
 Eine zuverlässige notfallwiederherstellungslösung für Ihre Datenbanken ist von wesentlicher Bedeutung für Ihre geschäftlichen Erfolg. Die meisten Kunden müssen einen eigenen Standort für die Notfallwiederherstellung einrichten und zusätzliche Hardware für Datenbankreplikate anschaffen. Mit SQL Server und Azure können Sie ein oder mehrere Replikate Ihrer Datenbanken in der Cloud verwalten. 
 
 Die wichtigsten Vorteile der Verwaltung von sekundärer Replikaten in Azure umfassen: 
 
-  Kostengünstige Notfallwiederherstellungslösung 
 
-  Transparentes Anwendungsfailover 
 
-  Verfügbare Replikate zur Auslagerung von Lesearbeitslasten und Sicherungen 
 
 Sie können sekundäre Replikate in Azure mithilfe einer der folgenden Methoden verwalten: 
 
-  Die [Assistent zum Hinzufügen eines Azure-Replikaten](https://msdn.microsoft.com/library/dn463980\(v=sql.120\).aspx) ermöglicht Ihnen, ein oder mehrere Replikate Ihrer Datenbanken auf einem virtuellen Computer in Azure für die notfallwiederherstellung bereitzustellen. 
 
-  AlwaysOn-Verfügbarkeitsgruppen, datenbankspiegelung und Protokollversand sind die häufigsten Technologien, die hochverfügbarkeit Ihrer Anwendung behandeln können und notfallwiederherstellung. Weitere Informationen finden Sie unter [Hochverfügbarkeit und Notfallwiederherstellung für SQL Server auf Azure Virtual Machines](https://msdn.microsoft.com/library/azure/jj870962.aspx). 
 
#### <a name="store"></a> Store SQL Server-Datendateien im Azure-Speicher 
 Speichern von lokalen SQL Server-Datendateien im Azure-Speicher bietet einen flexiblen, zuverlässigen und unbegrenzten externen Speicher für Ihre Datenbanken. Ab SQL Server 2014, können Sie [SQL Server-Datendateien in Azure mit Miceosoft](https://docs.microsoft.com/sql/relational-databases/databases/sql-server-data-files-in-microsoft-azure) zum Speichern von SQL Server-Datenbankdateien im Azure-Speicher. Mit diesem Feature können Sie Verschieben von Daten und-Protokolldateien von einer lokalen Datenbank in Azure Storage, Beibehaltung der Compute-Knoten des SQL Server, die lokal ausgeführt wird. Dieses Feature ermöglicht Ihnen, unbegrenzte Speicherkapazität in Azure Storage. 
 
 Die wichtigsten Vorteile von SQL Server-Datendateien, Azure Storage gespeichert sind: 
 
-  Unbegrenzter kostengünstiger Speicher im Azure-Speicher 
 
-  Optimale Lösung, um Lesezugriffe auf ältere Daten in die Cloud auszulagern und auf diese Weise lokale Berichterstellungsanwendungen zu entlasten. 
 
-  Einfachere Notfallwiederherstellung durch die Trennung von Serverinstanz (eine SQL Server-Instanz) und Daten (SQL Server-Datendateien). Dadurch können Sie problemlos anfügen die Datenbank in eine andere Instanz von SQL Server in einer lokalen Umgebung oder in einem virtuellen Azure-Computer bei einem Notfall. 
 
#### <a name="migrate"></a> Migrieren Sie vorhandene SQL Server-Datenbanken zu Azure Virtual Machines 
 Das Cloud Computing eröffnet Unternehmen eine Reihe überzeugender Vorteile, z. B. die Nutzung unbegrenzt virtualisierbarer Ressourcen, die nutzungsbasiert abgerechnet werden. Darüber hinaus können Sie die in der Cloud verfügbaren Rechenzentren nutzen, anstatt eigene Rechenzentren einzurichten und zu unterhalten. Auf diese Weise lassen sich IT- und Hardwarekosten senken. 
 
 Mit [SQL Server auf Azure Virtual Machines](https://msdn.microsoft.com/library/azure/jj823132.aspx), Sie können die vorhandenen lokalen Anwendungen bei minimalen Kosten in Azure verschieben und ohne codeänderungen. Administratoren und Entwickler verwenden dabei dieselben Entwicklungs- und Verwaltungstools wie für ihre lokalen Projekte. 
 
 Verschieben einer Datenbank aus einer lokalen SQL Server mit SQL Server auf einem virtuellen Azure-Computer in der Regel akzeptiert einen der folgenden Pfade: 
 
-  **Verschieben nur der Datenbank an:** Es gibt mehrere Tools und Techniken nutzen, um vorhandene lokale Datenbanken zu SQL Server auf Azure Virtual Machines verschieben. Richtlinien und Empfehlungen zur Migration zu SQL Server auf Azure Virtual Machines, finden Sie unter [bereit für die Migration zu SQL Server auf Azure Virtual Machines](https://msdn.microsoft.com/library/dn133142.aspx) sowie [Migrieren zu SQL Server auf einem virtuellen Azure-Computer ](https://msdn.microsoft.com/library/jj156165.aspx). 
 
   Darüber hinaus beginnend mit SQL Server 2014, einen Assistenten für neue [SQL Server-Datenbank mit einem Microsoft Azure-Computer bereitstellen](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) steht für die Sie zum Bereitstellen der Datenbank in eine andere SQL Server-Instanz, die in einem Azure-Computer ausgeführt. 
 
-  **Verschieben des gesamten virtuellen Computers:** Sie können die nutzen Sie eigene SQL Server-Computer in Azure oder von einem Plattformimage erstellen. Anschließend können Sie einen Datenträger, auf dem bereits Daten gespeichert sind, hochladen und an den virtuellen Computer anfügen, oder Sie fügen einen leeren Datenträger an den virtuellen Computer an. Mit einer Instanz des SQL Server-Daten in Azure Virtual Machines mit angefügten Datenträgern bietet einer weiteren permanenten speicherlösung für Ihre Daten- und Anwendungsdaten. Umfassende Informationen und Vorgehensweisen finden Sie unter [SQL Server-Bereitstellung in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133141.aspx). 
 
 Wenn Sie beabsichtigen, die Anwendungsebenen (z. B. der Präsentationsebene, Geschäfts- und Datenbankebene) auf Azure Virtual Machines verlagern, es wird empfohlen, dass Sie die Empfehlungen im Artikel der [Anwendungsmuster und Entwicklung Strategien für die SQL Server auf Azure Virtual Machines](https://msdn.microsoft.com/library/dn574746.aspx) Artikel. Das Ziel dieses Artikels ist, Lösungsarchitekten und Entwicklern eine Grundlage für gute Anwendungsarchitektur und-Entwurf, die sie befolgen können, bei der Migration vorhandener Anwendungen in Azure sowie Entwicklung neuer Anwendungen in Azure bieten. In diesem Artikel wird jedes Anwendungsmuster unter den folgenden Gesichtspunkten beleuchtet: lokales Szenario, entsprechende cloudfähige Lösung und zweckdienliche technische Empfehlungen. Darüber hinaus behandelt der Artikel Azure-spezifische Entwicklungsstrategien, sodass Sie Ihre Anwendungen ordnungsgemäß entwerfen können. 
 
## <a name="see-also"></a>Siehe auch 
 [SQL Server 2014 CTP2-Produkthandbuch](https://www.microsoft.com/download/details.aspx?id=39269)  
 [SQL Server 2014](https://www.microsoft.com/sqlserver/sql-server-2014.aspx)  
 [Microsoft SQL Server Hybrid Cloud-Blogreihe](https://blogs.msdn.com/b/azure/archive/2013/10/16/microsoft-sql-server-hybrid-cloud-blog-series.aspx)  
 [Migrieren von datenorientierten Anwendungen zu Azure](https://msdn.microsoft.com/library/jj156154.aspx) 
 
 
