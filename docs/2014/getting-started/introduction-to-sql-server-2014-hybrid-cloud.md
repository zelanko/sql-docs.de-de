---
title: Einführung in SQL Server 2014 Hybrid Cloud | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6dc42752-1fcd-4ab9-8194-c3001ea342e7
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 711d9d5bf7a3268b400eae4b1b117b4034133f5c
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228070"
---
# <a name="introduction-to-sql-server-2014-hybrid-cloud"></a>Einführung in SQL Server 2014 Hybrid Cloud
 Für die meisten Anwendungen gelten eine Reihe zentraler Herausforderungen. Dazu gehören hohe Effizienz, maximaler Geschäftswert, komplexe Hardwarekonfigurationen, Deckung von Bedarfsspitzen und die Einhaltung branchen- und unternehmensspezifischer Auflagen. Angesichts all dieser Faktoren kann sich die Entwicklung einer unternehmensfähigen Technologie sehr schwierig gestalten. Die Microsoft Hybrid Cloud-Strategie wird diesen Anforderungen gerecht, indem sie Unterstützung für herkömmliche, private Clouds, öffentliche Clouds und Hybrid Cloud-Umgebungen bietet. 
 
 Wenn Ihr Unternehmen eine flexible IT-Infrastruktur benötigt, die Bedarfs gesteuert skaliert werden kann, können Sie eine Private Cloud in Ihrem Rechenzentrum oder in einer Public Cloud in globalen Azure-Rechenzentren erstellen. Wenn Sie Ihr Rechenzentrum erweitern, um es mit der öffentlichen Cloud zu kombinieren, sprechen wird von einem Hybrid Cloud-Modell. 
 
 In diesem Thema werden die SQL Server 2014-Funktionen vorgestellt, die die Hybrid Cloud-Szenarien unterstützen. Ausführliche Informationen zur Microsoft Hybrid Cloud-Strategie und zu SQL Server finden Sie auf der Website [Hybrid IT für SQL Server](https://www.microsoft.com/sqlserver/solutions-technologies/hybrid-It.aspx) . 
 
## <a name="sql-server-azure-and-hybrid-cloud"></a>SQL Server, Azure und Hybrid Cloud 
 Microsoft-Technologien ermöglichen folgende Arten der Codeausführung: lokal und in der Cloud, cloudbasiert auf der Grundlage lokaler Daten oder vollständig in der Cloud, wobei Ihnen die Kapazitäten mehrerer Rechenzentren zur Verfügung stehen. Sie können Ihre Anwendungen also nach Ihrem eigenen Zeitplan in die Cloud verlagern und den Wert bereits getätigter IT-Investitionen dabei voll ausschöpfen. 
 
 In diesem Artikel konzentrieren wir uns auf die Hybrid Cloud Szenarien, die vom lokalen SQL Server bis hin zu Azure-Public Cloud angeboten sind: [SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/azure/jj823132.aspx) und [Azure Storage](https://www.azure.com/documentation/services/storage/). Insbesondere werden die folgenden Szenarios erläutert: 
 
-  [Sichern und Wiederherstellen von Datenbanken in/aus Azure Storage](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#backup) 
 
-  [Warten von Daten Bank Replikaten in Azure Virtual Machines](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#replica) 
 
-  [Speichern von SQL Server Datendateien in Azure Storage](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#store) 
 
-  [Migrieren vorhandener SQL Server-Datenbanken zu Azure Virtual Machines](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#migrate) 
 
### <a name="hybrid-cloud-scenarios-for-sql-server-and-microsoft-azure"></a>Hybrid Cloud-Szenarien für SQL Server und Microsoft Azure 
 
#### <a name="backup"></a>Sichern und Wiederherstellen von Datenbanken in/aus Azure Storage 
 Eine der grundlegendsten Administratoraufgaben ist die Sicherung und Wiederherstellung von Datenbanken. Mit SQL Server und Azure können Sie Ihre Datenbanken sicher in der Cloud sichern. 
 
 Die wichtigsten Vorteile der Verwendung der Sicherungs-und Wiederherstellungs Funktionen von SQL Server mit Azure Storage als Sicherungs Ziel sind: 
 
-  Unbegrenzter kostengünstiger Speicher 
 
-  Hochverfügbarer Speicher (keine Datenverluste dank geografischer Replikation) 
 
-  Externer Speicher zur Erfüllung der Notfallwiederherstellungs- und Konformitätsanforderungen 
 
-  Vereinfachte Remotesicherung und -wiederherstellung 
 
 Im Folgenden sind die Sicherungs- und Wiederherstellungsfunktionen von SQL Server aufgeführt, die für lokale Szenarien und die Cloud verfügbar sind: 
 
-  Mit der [SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md) -Funktion können Sie eine Sicherung auf Azure Storage durch Angeben von URL als Sicherungs Ziel durch geben. Mit dieser Funktion können Sie manuelle Sicherungen ausführen oder eine eigene Sicherungsstrategie konfigurieren. Dabei gehen Sie genauso vor wie bei der lokalen Speicherung oder anderen externen Speicheroptionen. 
 
-  Mit dem Feature für die [Sicherungs Verschlüsselung](../relational-databases/backup-restore/backup-encryption.md) können Sie die Daten beim Erstellen einer Sicherung für Ihre Speicher Ziele verschlüsseln: lokal und Azure Storage. 
 
-  Mithilfe der [Sicherungs Komprimierung (SQL Server)](../relational-databases/backup-restore/backup-compression-sql-server.md) können Sie eine Sicherung erstellen, die kleiner als eine nicht komprimierte Sicherung derselben Daten ist. Die Komprimierung einer Sicherung erfordert weniger Geräte-E/A-Vorgänge und steigert deshalb deutlich die Sicherungsleistung. Dies kann beim Speichern von Sicherungsdateien in Azure Storage sehr nützlich sein. 
 
-  Mit der SQL Server Funktion " [verwaltete Sicherung in Azure](https://msdn.microsoft.com/library/dn606152(v=sql.120).aspx) " können Sie SQL Server-Datenbanken automatisch auf [Azure Storage](https://www.azure.com/documentation/services/storage/)sichern. Mit dieser Funktion können Sie SQL Server konfigurieren, um die Sicherungsstrategie zu verwalten und Sicherungen für eine einzelne oder mehrere Datenbanken zu planen oder um Standardwerte auf Instanzebene festzulegen. 
 
-  Das [SQL Server Backup to Azure Tool](https://www.microsoft.com/download/details.aspx?id=40740) ermöglicht die Sicherung Azure BLOB Storage und verschlüsselt und komprimiert SQL Server Sicherungen, die lokal oder in der Cloud gespeichert sind. Dieses Tool unterstützt eine einzelne Cloudsicherungsstrategie für mehrere Versionen von SQL Server wie SQL Server 2005, 2008, 2008 R2 und 2014. 
 
#### <a name="replica"></a>Warten von Daten Bank Replikaten in Azure Virtual Machines 
 Eine stabile Notfall Wiederherstellungslösung für Ihre Datenbanken ist entscheidend für den Erfolg Ihres Unternehmens. Die meisten Kunden müssen einen eigenen Standort für die Notfallwiederherstellung einrichten und zusätzliche Hardware für Datenbankreplikate anschaffen. Mit SQL Server und Azure können Sie ein oder mehrere Replikate Ihrer Datenbanken in der Cloud verwalten. 
 
 Die wichtigsten Vorteile der Verwaltung sekundärer Replikate in Azure sind: 
 
-  Kostengünstige Notfallwiederherstellungslösung 
 
-  Transparentes Anwendungsfailover 
 
-  Verfügbare Replikate zur Auslagerung von Lesearbeitslasten und Sicherungen 
 
 Sie können sekundäre Replikate in Azure mit einer der folgenden Methoden verwalten: 
 
-  Mit dem [Assistenten zum Hinzufügen von Azure-Replikaten](https://msdn.microsoft.com/library/dn463980\(v=sql.120\).aspx) können Sie ein oder mehrere Replikate Ihrer Datenbanken auf einem virtuellen Computer in Azure zur Notfall Wiederherstellung bereitstellen 
 
-  AlwaysOn-Verfügbarkeitsgruppen, Daten Bank Spiegelung und Protokoll Versand sind die gängigsten Technologien, die Sie verwenden können, um die Hochverfügbarkeit und die Notfall Wiederherstellungs Anforderungen Ihrer Anwendung zu erfüllen. Weitere Informationen finden Sie unter [Hochverfügbarkeit und Notfall Wiederherstellung für SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/azure/jj870962.aspx). 
 
#### <a name="store"></a>Speichern von SQL Server Datendateien in Azure Storage 
 Das Speichern von lokalen SQL Server-Datendateien in Azure Storage bietet einen flexiblen, zuverlässigen und unbegrenzten externen Speicher für Ihre Datenbanken. Ab SQL Server 2014 können Sie [SQL Server Datendateien in miceosoft Azure](https://docs.microsoft.com/sql/relational-databases/databases/sql-server-data-files-in-microsoft-azure) verwenden, um SQL Server Datenbankdateien in Azure Storage zu speichern. Mit dieser Funktion können Sie Daten-und Protokolldateien aus einer lokalen Datenbank in Azure Storage verschieben, während der Computeknoten von SQL Server lokal ausgeführt wird. Diese Funktion ermöglicht es Ihnen, in Azure Storage unbegrenzte Speicherkapazität zu haben. 
 
 Die wichtigsten Vorteile der Speicherung von SQL Server-Datendateien Azure Storage sind: 
 
-  Unbegrenzter kostengünstiger Speicher in Azure Storage 
 
-  Optimale Lösung, um Lesezugriffe auf ältere Daten in die Cloud auszulagern und auf diese Weise lokale Berichterstellungsanwendungen zu entlasten. 
 
-  Einfachere Notfallwiederherstellung durch die Trennung von Serverinstanz (eine SQL Server-Instanz) und Daten (SQL Server-Datendateien). Auf diese Weise können Sie die Datenbank problemlos an eine andere Instanz von SQL Server in einer lokalen Umgebung oder auf einem virtuellen Azure-Computer anfügen, wenn ein Notfall eintritt. 
 
#### <a name="migrate"></a>Migrieren vorhandener SQL Server-Datenbanken zu Azure Virtual Machines 
 Das Cloud Computing eröffnet Unternehmen eine Reihe überzeugender Vorteile, z. B. die Nutzung unbegrenzt virtualisierbarer Ressourcen, die nutzungsbasiert abgerechnet werden. Darüber hinaus können Sie die in der Cloud verfügbaren Rechenzentren nutzen, anstatt eigene Rechenzentren einzurichten und zu unterhalten. Auf diese Weise lassen sich IT- und Hardwarekosten senken. 
 
 Mit [SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/azure/jj823132.aspx)können Sie die vorhandenen lokalen Anwendungen mit minimalen oder gar keinen Codeänderungen in Azure verschieben. Administratoren und Entwickler verwenden dabei dieselben Entwicklungs- und Verwaltungstools wie für ihre lokalen Projekte. 
 
 Das Verschieben einer Datenbank aus einer lokalen SQL Server in SQL Server, die auf einem virtuellen Azure-Computer ausgeführt wird, hat in der Regel einen der folgenden Pfade: 
 
-  **Verschieben nur der Datenbank:** Es gibt mehrere Tools und Techniken, mit denen Sie vorhandene lokale Datenbanken in SQL Server in Azure Virtual Machines verschieben können. Richtlinien und Empfehlungen zur Migration zu SQL Server in Azure Virtual Machines finden Sie unter Vorbereiten der Migration [zu SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133142.aspx) und auch [Migrieren zu SQL Server auf einem virtuellen Azure-Computer](https://msdn.microsoft.com/library/jj156165.aspx). 
 
   Außerdem können Sie ab SQL Server 2014 mit einem neuen Assistenten eine [SQL Server Datenbank auf einem Microsoft Azure virtuellen Computer](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) bereitstellen, um die Datenbank auf einer anderen SQL Server Instanz bereitzustellen, die auf einem virtuellen Azure-Computer ausgeführt wird. 
 
-  **Verschieben des gesamten virtuellen Computers:** Sie können Ihre eigenen SQL Server virtuellen Computer in Azure verwenden oder mithilfe des Platt Form Images erstellen. Anschließend können Sie einen Datenträger, auf dem bereits Daten gespeichert sind, hochladen und an den virtuellen Computer anfügen, oder Sie fügen einen leeren Datenträger an den virtuellen Computer an. Das vorhanden sein einer SQL Server-Daten Instanz in Azure Virtual Machines mit angefügten Datenträgern bietet einen weiteren permanenten Speicher für Ihre Datendateien und Anwendungsdaten. Umfassende Informationen und Anleitungen finden Sie unter [SQL Server Bereitstellung in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133141.aspx). 
 
 Wenn Sie beabsichtigen, die Anwendungsebenen (z. b. die Präsentationsebene, die Geschäfts Schicht und die Datenbankebene) in Azure Virtual Machines zu verschieben, sollten Sie die Empfehlungen im Artikel [Anwendungs Muster und Entwicklungsstrategien für SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/dn574746.aspx) überprüfen. Das Ziel dieses Artikels ist, Lösungsarchitekten und Entwicklern eine Grundlage für gute Anwendungsarchitektur und deren Entwurf zu bieten, die sie bei der Migration der vorhandenen Anwendungen nach Azure sowie bei der Entwicklung neuer Anwendungen in Azure verfolgen können. In diesem Artikel wird jedes Anwendungsmuster unter den folgenden Gesichtspunkten beleuchtet: lokales Szenario, entsprechende cloudfähige Lösung und zweckdienliche technische Empfehlungen. Darüber hinaus behandelt der Artikel Azure-spezifische Entwicklungsstrategien für einen ordnungsgemäßen Entwurf Ihrer Anwendungen. 
 
## <a name="see-also"></a>Siehe auch 
 [SQL Server 2014 CTP2-Produkthandbuch](https://www.microsoft.com/download/details.aspx?id=39269)  
 [SQL Server 2014](https://www.microsoft.com/sqlserver/sql-server-2014.aspx)  
 [Blogreihe über die Microsoft SQL Server Hybrid Cloud](https://azure.microsoft.com/blog/microsoft-sql-server-hybrid-cloud-blog-series/)  
 [Migrieren Daten orientierter Anwendungen zu Azure](https://azure.microsoft.com/blog/cloud-services-series-migrating-data-centric-applications-to-windows-azure/) 
 
