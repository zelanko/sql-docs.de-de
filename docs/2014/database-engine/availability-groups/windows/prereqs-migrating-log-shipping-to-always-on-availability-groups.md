---
title: Voraussetzungen für das Migrieren vom Protokoll Versand zu AlwaysOn-Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 865e8d720e9977f582ac5ae8a0e75d995fc82629
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62789553"
---
# <a name="prerequisites-for-migrating-from-log-shipping-to-alwayson-availability-groups-sql-server"></a>Voraussetzungen für das Migrieren vom Protokollversand zu AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  In diesem Thema werden die erforderlichen Komponenten zum Konvertieren einer primären Datenbank für den Protokollversand zusammen mit einer oder mehreren sekundären Datenbanken in eine primäre AlwaysOn-Datenbank und sekundäre Datenbank(en) beschrieben.  
  
> [!NOTE]  
>  Sie können jede primäre oder sekundäre (ggf. lesbare) Datenbank in einer Verfügbarkeitsgruppe als primäre Datenbank für den Protokollversand konfigurieren.  
  
 **In diesem Thema:**  
  
-   [Erforderliche Komponenten für Verfügbarkeitsgruppen](#AGPrereqsRealAddress)  
  
-   [Erforderliche Komponenten für den Protokollversand](#LogShipPrereqs)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
-   [Verwandte Inhalte](#RelatedContent)  
  
##  <a name="availability-group-prerequisites"></a><a name="AGPrereqsRealAddress"></a>Verfügbarkeits Gruppen Voraussetzungen  
 Damit Sicherungsaufträge auf dem primären Replikat der Verfügbarkeitsgruppe ausgeführt werden können, verwenden Sie die folgenden Sicherungseinstellungen für AlwaysOn-Verfügbarkeitsgruppen:  
  
|Eigenschaft|Einstellung|  
|--------------|-------------|  
|Die Voreinstellung für die automatisierte Sicherung der Verfügbarkeitsgruppe.|Nur auf dem primären Replikat|  
|Sicherungspriorität des primären Replikats.|>0|  
  
 **Weitere Informationen finden Sie unter:**  
  
 [Anzeigen von Verfügbarkeitsgruppeneigenschaften &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)  
  
 [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="log-shipping-prerequisites"></a><a name="LogShipPrereqs"></a>Anforderungen an den Protokoll Versand  
  
-   Die primäre Datenbank für den Protokollversand muss sich auf der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] befinden, auf der das anfängliche/aktuelle primäre Replikat der Verfügbarkeitsgruppe gehostet wird.  
  
-   Damit eine angegebene sekundäre Datenbank für den Protokollversand in eine sekundäre AlwaysOn-Datenbank konvertiert werden kann, muss Folgendes erfüllt sein:  
  
    -   Sie muss den gleichen Namen wie die primäre Datenbank verwenden.  
  
    -   Sie muss auf einer Serverinstanz befinden, auf der ein sekundäres Replikat für die Verfügbarkeitsgruppe gehostet wird.  
  
 Sobald der Sicherungsauftrag auf der primären Datenbank ausgeführt wurde, deaktivieren Sie den Sicherungsauftrag, und sobald der Wiederherstellungsauftrag auf einer angegebenen sekundären Datenbank ausgeführt wurde, deaktivieren Sie den Wiederherstellungsauftrag.  
  
 Nachdem Sie alle sekundären Datenbanken für die Verfügbarkeitsgruppe erstellt haben, sofern Sie Sicherungen auf sekundären Replikaten ausführen möchten, müssen Sie die Voreinstellung zur automatisierten Sicherung der Verfügbarkeitsgruppe neu konfigurieren.  
  
 **Weitere Informationen finden Sie unter:**  
  
 [Konvertieren einer Protokollversandkonfiguration in eine Verfügbarkeitsgruppe](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (ein SQL Server-Blog)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **Protokollversand**  
  
-   [Aktualisieren des Protokoll Versands auf SQL Server 2014 &#40;Transact-SQL-&#41;](../../log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Entfernen des Protokollversands &#40;SQL Server&#41;](../../log-shipping/remove-log-shipping-sql-server.md)  
  
 **AlwaysOn-Verfügbarkeitsgruppen**  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Dialogfelds Neue Verfügbarkeitsgruppe &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Erstellen einer Verfügbarkeitsgruppe &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
-   [Erstellen einer Verfügbarkeitsgruppe &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [Konvertieren einer Protokollversandkonfiguration in eine Verfügbarkeitsgruppe](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx)  
  
     [Hinzufügen einer primären Datenbank für den Protokollversand und mindestens einer sekundären Datenbank zu einer vorhandenen Verfügbarkeitsgruppe](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/01/use-log-shipping-to-prepare-secondary-databases-for-an-existing-availability-group.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server-Technikblogs](https://blogs.msdn.com/b/psssql/)  
  
-   **Whitepaper:**  
  
     [Migrationshandbuch: Migrieren zu AlwaysOn-Verfügbarkeitsgruppen von vorherigen Bereitstellungen, in denen Datenbankspiegelung und Protokollversand kombiniert sind](https://msdn.microsoft.com/library/jj635217)  
  
     [Microsoft-Whitepapers für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokoll Versand &#40;SQL Server&#41;](../../log-shipping/about-log-shipping-sql-server.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Überwachen von Verfügbarkeitsgruppen (SQL Server)](monitoring-of-availability-groups-sql-server.md)  
  
  
