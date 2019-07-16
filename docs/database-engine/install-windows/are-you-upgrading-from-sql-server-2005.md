---
title: Führen Sie ein Upgrade von SQL Server 2005, 2008 oder 2008R2 aus? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ad40e66f-71fe-4ee6-9ce3-17127e7b1d7a
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: jroth
ms.openlocfilehash: ab4e56eb51a03d9c1bdbc8e0c4f87f98ddfbf57d
ms.sourcegitcommit: e366f702c49d184df15a9b93c2c6a610e88fa0fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826535"
---
# <a name="are-you-upgrading-from-sql-server-2005-2008-or-2008r2"></a>Führen Sie ein Upgrade von SQL Server 2005, 2008 oder 2008R2 aus?

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 Die Einstellung des erweiterten Supports für SQL Server stellt einen guten Grund für das Upgrade auf eine neuere Version von SQL Server und Azure SQL-Datenbank dar. Ein Upgrade ermöglicht es Ihnen, Sicherheit und Compliance beizubehalten, eine bahnbrechende Leistung zu erzielen, und die Infrastruktur Ihrer Datenplattform zu optimieren.  
  
 Weitere Informationen, Anleitungen und Tools zum Planen und Automatisieren Ihres Upgrades oder Ihrer Migration finden Sie unter [Ende des Supports für SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005) und [Ende des Supports für SQL Server 2008](https://www.microsoft.com/cloud-platform/windows-sql-server-2008).  
  
## <a name="why-upgrade"></a>Warum jetzt für ein Upgrade entscheiden?  
  
> [!IMPORTANT]  
>  Der erweiterte Support für SQL Server 2005 wurde am 12. April 2016 eingestellt. Wenn Sie SQL Server 2005 nach dem 12. April 2016 noch einsetzen, erhalten Sie keine Sicherheitsupdates mehr.  

> [!IMPORTANT]  
>  Der erweiterte Support für SQL Server 2008 und 2008R2 wurde am 09. Juli 2019 eingestellt. Wenn Sie SQL Server 2008 oder 2008R2 nach dem 09. Juli 2019 weiter einsetzen, erhalten Sie keine Sicherheitsupdates mehr. Weitere Informationen finden Sie im Blog [Announcing new options for SQL Server 2008 (Ankündigung neuer Optionen für SQL Server 2008)](https://azure.microsoft.com/blog/announcing-new-options-for-sql-server-2008-and-windows-server-2008-end-of-support/). Um den Support kostenlos zu verlängern, können Sie Ihren SQL Server zu einer Azure-VM migrieren. Weitere Informationen finden Sie unter [Erweiterter Support für SQL Server 2008 und 2008 R2 mit Azure](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-2008-eos-extend-support).  
  
## <a name="choose-your-upgrade-option"></a>Wählen Sie Ihre Upgradeoption  
Wenn Sie ein Upgrade für relationale Datenbanken von SQL Server ausführen, finden Sie hier die Optionen für die relationale Speicherung auf der Microsoft-Plattform.  
  
Um eine umfassendere Analyse dieser Optionen anzuzeigen, lesen Sie [PaaS im Vergleich zu IaaS](/azure/sql-database/sql-database-paas-vs-sql-server-iaas).  
  
|Relationale Speicheroption|Vorteile|Weitere zu berücksichtigende Faktoren|  
|-------------------------------|--------------|-------------------------------|  
|**SQL Server auf virtuellen Azure-Computern gehostet**<br /><br /> Ziehen Sie diese Option in Erwägung, wenn Ihnen die folgenden Punkte wichtig sind:<br /><br /> Vorzüge der Migration zu einer gehosteten Umgebung.<br /><br /> Kontrolle über die Betriebsumgebung.<br /><br /> Vertrauter Funktionsumfang von SQL Server.|**Sie können den Support für SQL Server 2008 und 2008 R2 kostenlos um bis zu 3 Jahre [verlängern](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-2008-eos-extend-support).** <br /><br /> Die Bereitstellung kann schnell aus einer Bibliothek mit Images virtueller Computer erfolgen.<br /><br /> Sie erhalten den vollständigen Funktionsumfang von SQL Server.<br /><br /> Sie sparen die Kosten für Hardware und Serversoftware. Sie zahlen nur für die Nutzungsstunden.|Sie müssen sowohl SQL Server als auch die Betriebssystemsoftware verwalten.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Übersicht zu SQL Server auf virtuellen Azure-Computern](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).<br /><br /> Informationen zur Migration finden Sie unter [Migrieren einer Datenbank zu SQL Server auf einem virtuellen Azure-Computer](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/).|  
|**Verwaltete Azure SQL-Datenbank-Instanz (PaaS)** <br /><br /> Ziehen Sie diese Option in Betracht, wenn Sie eine kostengünstigere Lösung mit weniger Wartung wünschen.<br /><br /> Eine verwaltete Instanz ähnelt einer Instanz der Microsoft SQL Server-Datenbank-Engine und bietet gemeinsame Ressourcen für Datenbanken und zusätzliche instanzbezogene Funktionen. <br /><br />Die verwaltete Instanz unterstützt die Datenbankmigration von lokalen Standorten mit nur minimalen oder gar keinen Datenbankänderungen.|Nutzen Sie die Vorteile datenbankübergreifender Abfragen innerhalb derselben verwalteten Instanz sowie die Unterstützung von CLR- und SQL-Aufträgen. <br /><br /> Eine Verfügbarkeit von 99,995 % wird garantiert.<br /><br /> Die Kosten für den Dienst beinhalten nicht nur die Speicherung, sondern darüber hinaus auch Hochverfügbarkeit, Patchen und automatische Sicherungen.|Es gibt einige Transact-SQL-Unterschiede (T-SQL) zwischen der verwalteten Azure SQL-Datenbank-Instanz und einer lokalen Installation von SQL Server. Weitere Informationen finden Sie unter [Verwaltete Instanz der Azure SQL-Datenbank: T-SQL-Informationen](/azure/sql-database/sql-database-managed-instance-transact-sql-information).<br /><br /> Weitere Informationen zu verwalteten Instanzen von SQL-Datenbank finden Sie unter [Verwaltete Azure SQL-Datenbank-Instanz: Übersicht](/azure/sql-database/sql-database-managed-instance-index) und [Verwaltete Azure SQL-Datenbank-Instanz: Funktionen](/azure/sql-database/sql-database-managed-instance).<br /><br /> Informationen zur Migration finden Sie unter [Migrieren einer SQL Server-Datenbank zu einer verwalteten Instanz von Azure SQL-Datenbank](/azure/sql-database/sql-database-managed-instance-migrate).|  
|**Einzelne Azure SQL-Datenbank oder Pool für elastische Datenbanken (PaaS)** <br /><br /> Ziehen Sie diese Option in Betracht, wenn Sie eine kostengünstigere Lösung mit weniger Wartung wünschen.<br /><br /> Diese Option eignet sich besonders gut für Anwendungen mit Clouddesign, wenn die Produktivität der Entwickler und die schnelle Markteinführung neuer Lösungen entscheidend sind oder externer Zugriff bereitgestellt werden muss. <br /><br />Die am häufigsten verwendeten SQL Server-Funktionen sind verfügbar, aber nicht so viele Funktionen wie für eine verwaltete Instanz von Azure SQL-Datenbank. |Sie können schnell bereitstellen und einfach zentral hochskalieren.<br /><br /> Eine Verfügbarkeit von 99,995 % wird garantiert.<br /><br /> Sie können für die Verwendung pro Sekunde oder Stunde bezahlen. <br /><br /> Die Kosten für den Dienst beinhalten nicht nur die Speicherung, sondern darüber hinaus auch Hochverfügbarkeit, Patchen und automatische Sicherungen.|Es gibt einige Transact-SQL-Unterschiede (T-SQL) zwischen Azure SQL-Datenbank und einer lokalen Installation von SQL Server. Weitere Informationen finden Sie unter [Azure SQL-Datenbank – Transact-SQL-Informationen](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/).<br /><br /> Außerdem beträgt die maximale Datenbankgröße für Azure SQL-Datenbank 100 TB im Vergleich zu 524 PB für SQL Server. Weitere Informationen finden Sie unter [Resource limits for single databases (Ressourceneinschränkungen für Singletons)](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases).<br /><br /> Weitere Informationen zu SQL-Datenbank finden Sie in der [Übersicht](https://azure.microsoft.com/services/sql-database/) und der [Dokumentation zu Azure SQL-Datenbank](/azure/sql-database/sql-database-technical-overview).<br /><br /> Informationen zur Migration finden Sie unter [Migrieren einer SQL Server-Datenbank zu Azure SQL-Datenbank](/azure/sql-database/sql-database-single-database-migrate).|  
|**Lokale SQL Server-Infrastruktur**<br /><br /> Diese Option bietet sich für Datenbankanwendungen jeder Art an, von Transaktionssystemen bis hin zu Data Warehouses.|Sie haben die bestmögliche Kontrolle über Features und Skalierbarkeit, da Sie sowohl Hardware als auch Software selbst verwalten.<br /><br /> Wenn Sie ein Upgrade von einer älteren Instanz von SQL Server ausführen, ist dies die Umgebung mit den meisten Gemeinsamkeiten.|Sie müssen vorab die größte Investition leisten und haben im laufenden Betrieb den höchsten Verwaltungsaufwand, da Sie Ihre eigene Hardware und Software kaufen, warten und verwalten müssen.<br /><br /> Weitere Informationen finden Sie unter [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-rtm).|  

Für bestimmte Daten und Anwendungen kann außerdem eine nicht relationale oder NoSQL-Lösung sinnvoll sein.  
  
|Nicht-relationale Lösung|Vorteile|  
|------------------------------|--------------|  
|**Azure Cosmos DB**<br /><br /> Erwägen Sie diese Option für moderne skalierbare Webanwendungen und mobile Anwendungen, die JSON-Daten verwenden und eine Kombination aus stabiler Abfrage- und Transaktionsdatenverarbeitung benötigen.<br /><br /> Weitere Informationen finden Sie unter [Cosmos DB](https://azure.microsoft.com/services/cosmos-db/).<br /><br /> Informationen zum Importieren von Daten finden Sie unter [Import data to Cosmos DB (Importieren von Daten in Cosmos DB)](https://docs.microsoft.com/azure/cosmos-db/import-data/).|Ihre Dokumente werden indiziert, und Sie können die vertraute SQL-Syntax für Abfragen darauf verwenden.<br /><br /> Die Datenbank besitzt kein Schema.<br /><br /> Sie können Dokumenten Eigenschaften hinzufügen, ohne die Indizes neu erstellen zu müssen.<br /><br /> Sie erhalten JSON- und JavaScript-Unterstützung direkt innerhalb der Datenbank-Engine.<br /><br /> Sie erhalten systemeigene Unterstützung für räumliche Daten und Integration mit anderen Azure-Services, einschließlich Azure Search, HDInsight, und Data Factory.<br /><br /> Sie erhalten Speicherung mit geringer Latenz und hoher Leistung bei reservierten Durchsatzniveaus.|  
|**Azure-Tabellenspeicher**<br /><br /> Erwägen Sie diese Option, um Petabytes teilweise strukturierter Daten in einer kostengünstigen Lösung zu speichern.<br /><br /> Weitere Informationen finden Sie unter [Tabellenspeicher](https://azure.microsoft.com/services/storage/tables/).|Sie können Ihre Apps und Ihr Tabellenschema weiterentwickeln, ohne die Daten offline nehmen zu müssen.<br /><br /> Sie können zentral hochskalieren, ohne Ihr Dataset horizontal partitionieren zu müssen.<br /><br /> Sie erhalten geografisch redundanten Speicher, der Daten über mehrere Regionen repliziert.|  
  
## <a name="plan-your-upgrade"></a>Planen des Upgrades  
  
-   In den folgenden Blogbeiträgen des SQL Server-Teams erhalten Sie Informationen zur Planung des Upgrades Ihrer SQL Server 2005-Instanz. 
    - Planen eines effizienten Upgrades von SQL Server 2005: [Schritt 1 von 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx), [Schritt 2 von 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx), [Schritt 3 von 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)
- Bereiten Sie sich auf das [Ende des Supports für SQL Server 2008](https://www.microsoft.com/sql-server/sql-server-2008) vor.
  
-   Überprüfen Sie die Voraussetzungen und Überlegungen unter [Planning a SQL Server Installation (Planen einer SQL Server-Installation)](../../sql-server/install/planning-a-sql-server-installation.md), einschließlich der [Hardware and Software Requirements for Installing SQL Server (Hardware- und Softwareanforderungen für die Installation von SQL Server)](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Lesen Sie, wie Sie das Upgrade durchführen können  
  
    -   Gehen Sie die verfügbaren Upgrademethoden durch, und erfahren Sie im Artikel [Aktualisieren der Datenbank-Engine](../../database-engine/install-windows/upgrade-database-engine.md), wie Sie die Methoden planen und testen können.  
  
        > [!IMPORTANT]  
        >- Sie können ein Upgrade einer SQL Server 2005-Instanz auf einen SQL Server 2017-Server nicht an Ort und Stelle ausführen. Sie müssen zuerst eine Instanz von SQL Server 2017 installieren und dann Ihre SQL Server 2005-Datenbanken zur neuen Installation migrieren. Weitere Informationen finden Sie im Abschnitt zum Upgrade von Neuinstallationen im Thema [Wählen einer Upgrademethode für die Datenbank-Engine](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
        >- Sie können ein Upgrade von SQL 2008 und SQL 2008r2 auf SQL 2017 durchführen. Weitere Informationen finden Sie unter [Unterstützte Versions- und Editionsupgrades](supported-version-and-edition-upgrades-2017.md). 


-    Weitere Informationen, Anleitungen und Tools zum Planen und Automatisieren Ihres Upgrades oder Ihrer Migration finden Sie unter [Ende des Supports für SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005) und [Ende des Supports für SQL Server 2008](https://www.microsoft.com/cloud-platform/windows-sql-server-2008).  
  
## <a name="get-sql-server"></a>SQL Server erwerben  
 Eine Evaluierungskopie von SQL Server können Sie unter [SQL Server-Downloads](https://www.microsoft.com/sql-server/sql-server-downloads) herunterladen.  
  
## <a name="next-steps"></a>Next Steps  
 [SQL Server (2017)](https://www.microsoft.com/sql-server/sql-server-2017)   
 [SQL Server 2005-Supportende](https://www.microsoft.com/sql-server/sql-server-2005)   
 [Ende des Supports für SQL Server 2008](https://www.microsoft.com/cloud-platform/windows-sql-server-2008)
  
  
