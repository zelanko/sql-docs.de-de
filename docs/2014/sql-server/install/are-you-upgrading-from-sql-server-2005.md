---
title: Führen Sie ein Upgrade von SQL Server 2005 aus? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/15/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d50a66a-1845-4116-8b3a-7b5a2eeb78e6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2db6a47de02b49397847dc9d713277ffcb152156
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75656577"
---
# <a name="are-you-upgrading-from-sql-server-2005"></a>Führen Sie ein Upgrade von SQL Server 2005 aus?
  Das Ende des erweiterten Support für SQL Server 2005 ist ein guter Grund für das Upgrade auf eine neuere Version von SQL Server und der Azure SQL-Datenbank. Ein Upgrade ermöglicht es Ihnen, Sicherheit und Compliance beizubehalten, eine bahnbrechende Leistung zu erzielen, und die Infrastruktur Ihrer Datenplattform zu optimieren.  
  
 Weitere Informationen, Anleitungen und Tools zum Planen und Automatisieren Ihres Upgrades oder Ihrer Migration finden Sie unter [SQL Server 2005-Supportende](https://www.microsoft.com/sql-server/sql-server-2005).  
  
## <a name="why-upgrade"></a>Gründe für ein Upgrade  
  
> [!IMPORTANT]  
>  Der erweiterte Support für SQL Server 2005 wird am 12. April 2016 eingestellt. Wenn Sie SQL Server 2005 nach dem 12. April 2016 noch einsetzen, erhalten Sie keine Sicherheitsupdates mehr.  
  
 Um das Datenblatt im PDF-Format zum Aktualisieren von SQL Server 2005 zu erhalten, [Klicken Sie hier](https://info.microsoft.com/rs/157-GQE-382/images/EN-CNTNT-Infographic-UpgradeSQL2005Datasheet.pdf) (nicht auf das Miniaturbild unten).  
  
 ![Datenblatt zum Upgrade von SQL Server 2005](../../../2014/sql-server/install/media/sqlserver2005eos.png "Datenblatt zum Upgrade von SQL Server 2005")  
  
## <a name="choose-your-upgrade-option"></a>Wählen Sie Ihre Upgradeoption  
 Wenn Sie ein Upgrade von relationalen Datenbanken von SQL Server 2005 ausführen, finden Sie hier die Optionen für relationalen Speicher auf der Microsoft-Plattform.  
  
 Um eine umfassendere Analyse dieser Optionen anzuzeigen, [klicken Sie hier](https://sql05upgrade.azurewebsites.net/).  
  
|Relationale Speicheroption|Vorteile|Weitere zu berücksichtigende Faktoren|  
|-------------------------------|--------------|-------------------------------|  
|**Lokale SQL Server-Infrastruktur**<br /><br /> Diese Option bietet sich für Datenbankanwendungen jeder Art an, von Transaktionssystemen bis hin zu Data Warehouses.<br /><br /> Weitere Informationen finden Sie unter [SQL Server 2014](https://www.microsoft.com/EN-US/server-cloud/products/sql-server/).|Sie haben die bestmögliche Kontrolle über Features und Skalierbarkeit, da Sie sowohl Hardware als auch Software selbst verwalten.<br /><br /> Wenn Sie von SQL Server 2005 aktualisieren, ist dies die einfachste Umgebung.|Sie müssen vorab die größte Investition leisten und haben im laufenden Betrieb den höchsten Verwaltungsaufwand, da Sie Ihre eigene Hardware und Software kaufen, warten und verwalten müssen.|  
|**SQL Server auf virtuellen Azure-Computern gehostet**<br /><br /> Ziehen Sie diese Option in Erwägung, wenn Ihnen die folgenden Punkte wichtig sind.<br />: Vorteile der Migration zu einer gehosteten Umgebung.<br />-Kontrolle über die Betriebsumgebung.<br />-Vertraute Funktionsgruppe SQL Server.<br /><br /> Weitere Informationen finden Sie unter [SQL Server in der Übersicht über Azure Virtual Machines](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).<br /><br /> Informationen zur Migration finden Sie unter [Migrieren einer Datenbank zu SQL Server auf einem virtuellen Azure-Computer](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/).|Die Bereitstellung kann schnell aus einer Bibliothek mit Images virtueller Computer erfolgen.<br /><br /> Sie erhalten den vollständigen Funktionsumfang von SQL Server.<br /><br /> Sie sparen die Kosten für Hardware und Serversoftware. Sie zahlen nur für die Nutzungsstunden.|Sie müssen sowohl die SQL Server- als auch die Betriebssystemsoftware konfigurieren und verwalten.|  
|**Gehosteter Azure SQL-Datenbankdienst**<br /><br /> Ziehen Sie diese Option in Betracht, wenn Sie eine kostengünstigere Lösung mit weniger Wartung wünschen.<br /><br /> Diese Option eignet sich besonders für Apps, die nicht zu allen Zeiten die gleiche Kapazität erfordern oder externen Zugriff bereitstellen müssen.<br /><br /> Weitere Informationen finden Sie unter [SQL-Datenbank](https://azure.microsoft.com/services/sql-database/).<br /><br /> Informationen zur Migration finden Sie unter [Migrieren einer SQL Server-Datenbank zu Azure SQL-Datenbank](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/).|Sie können schnell bereitstellen und einfach zentral hochskalieren.<br /><br /> Sie zahlen nur für die Nutzungsstunden.<br /><br /> Die Kosten für den Dienst beinhalten nicht nur die Speicherung, sondern darüber hinaus auch Hochverfügbarkeit und automatische Sicherungen.|Azure SQL-Datenbank bringt den Verzicht auf einige Features von SQL Server mit sich, die in einer gehosteten Cloudumgebung nicht anwendbar sind. Weitere Informationen finden Sie unter [Azure SQL-Datenbank – Transact-SQL-Informationen](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/).<br /><br /> Außerdem beträgt die maximale Datenbankgröße für Azure SQL-Datenbank 500 GB, im Vergleich dazu beträgt sie 524 PB für SQL Server.|  
  
 Für bestimmte Daten und Anwendungen kann außerdem eine nicht relationale oder NoSQL-Lösung sinnvoll sein.  
  
|Nicht-relationale Lösung|Vorteile|  
|------------------------------|--------------|  
|**Azure DocumentDB**<br /><br /> Erwägen Sie diese Option für moderne skalierbare Web- und mobile Anwendungen, die JSON-Daten verwenden und eine Kombination aus stabiler Abfrage- und Transaktionsdatenverarbeitung benötigen.<br /><br /> Weitere Informationen finden Sie unter [DocumentDB](https://azure.microsoft.com/services/documentdb/).|Ihre Dokumente werden indiziert, und Sie können die vertraute SQL-Syntax für Abfragen darauf verwenden.<br /><br /> Die Datenbank besitzt kein Schema.<br /><br /> Sie können Dokumenten Eigenschaften hinzufügen, ohne die Indizes neu erstellen zu müssen.<br /><br /> Sie erhalten JSON- und JavaScript-Unterstützung direkt innerhalb der Datenbank-Engine.<br /><br /> Sie erhalten systemeigene Unterstützung für räumliche Daten und Integration mit anderen Azure-Services, einschließlich Azure Search, HDInsight, und Data Factory.<br /><br /> Sie erhalten Speicherung mit geringer Latenz und hoher Leistung bei reservierten Durchsatzniveaus.|  
|**Azure-Tabellen Speicher**<br /><br /> Erwägen Sie diese Option, um Petabytes teilweise strukturierter Daten in einer kostengünstigen Lösung zu speichern.<br /><br /> Weitere Informationen finden Sie unter [Tabellenspeicher](https://azure.microsoft.com/services/storage/tables/).|Sie können Ihre Apps und Ihr Tabellenschema weiterentwickeln, ohne die Daten offline nehmen zu müssen.<br /><br /> Sie können zentral hochskalieren, ohne Ihr Dataset horizontal partitionieren zu müssen.<br /><br /> Sie erhalten geografisch redundanten Speicher, der Daten über mehrere Regionen repliziert.|  
  
 Um den Bericht „Migrieren von SQL Server 2005“ von Directions on Microsoft herunterzuladen, der weitere Details zu den Upgradeoptionen enthält, [klicken Sie hier](https://info.microsoft.com/CO-SQL-CNTNT-FY16-09Sep-14-ModernizationDirOnMFST-Register.html) (nicht auf das Miniaturbild unten).  
  
 ![Bericht zum Migrieren von SQL Server 2005](../../../2014/sql-server/install/media/sqlserver2005migratingdoc.png "Bericht zum Migrieren von SQL Server 2005")  
  
## <a name="plan-your-upgrade"></a>Planen des Upgrades  
  
-   Lesen Sie die Informationen zur Planung Ihres Upgrades in den folgenden Blogbeiträgen des SQL Server-Teams.  
  
    -   [Planen eines effizienten Upgrades von SQL Server 2005: Schritt 1 von 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx)  
  
    -   [Planen eines effizienten Upgrades von SQL Server 2005: Schritt 2 von 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx)  
  
    -   [Planen eines effizienten Upgrades von SQL Server 2005: Schritt 3 von 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)  
  
-   Überprüfen Sie die Anforderungen und Überlegungen unter [Planen einer SQL Server-Installation](../../../2014/sql-server/install/planning-a-sql-server-installation.md), einschließlich der [Hardware-und Software Anforderungen für die Installation von SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Lesen Sie, wie Sie das Upgrade durchführen können  
  
    -   Gehen Sie die verfügbaren Upgrademethoden durch, und erfahren Sie im Thema [Aktualisieren der Datenbank-Engine](../../database-engine/install-windows/upgrade-database-engine.md), wie Sie sie planen und testen können.  
  
        > [!IMPORTANT]  
        >  Sie können ein Upgrade eines SQL Server 2005-Servers auf einen SQL Server 2014-Server nicht an Ort und Stelle ausführen. Sie müssen zuerst SQL Server 2014 installieren und dann Ihre SQL Server 2005-Datenbanken zur neuen Installation migrieren.  
  
    -   Um den ausführlicheren technischen Upgradeleitfaden im PDF-Format herunterzuladen, [klicken Sie hier](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf).  
  
-   Weitere Informationen, Anleitungen und Tools zum Planen und Automatisieren Ihres Upgrades oder Ihrer Migration finden Sie unter [SQL Server 2005-Supportende](https://www.microsoft.com/sql-server/sql-server-2005).  
  
## <a name="get-sql-server-2014"></a>SQL Server 2014 herunterladen  
 [Klicken Sie hier](https://www.microsoft.com/evalcenter/evaluate-sql-server-2014), um eine Evaluierungsversion von SQL Server 2014 herunterzuladen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server 2014](https://docs.microsoft.com/sql/getting-started/getting-started-sql-server-2014)   
 [SQL Server 2005-Support Ende](https://www.microsoft.com/sql-server/sql-server-2005)   
 [Upgrade von SQL Server 2005 auf SQL Server 2016](https://msdn.microsoft.com/library/mt168847.aspx)  
  
  
