---
title: Voraussetzungen für das Konvertieren des Protokollversands in Verfügbarkeitsgruppen
description: In diesem Artikel werden die Voraussetzungen beschrieben, die für das Konvertieren des Protokollversands in eine Always On-Verfügbarkeitsgruppe erforderlich sind.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a4ee9154593b5c1d2d3d1bdf083796134d441fad
ms.sourcegitcommit: 827ad02375793090fa8fee63cc372d130f11393f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2020
ms.locfileid: "89480812"
---
# <a name="prerequisites-to-convert-log-shipping-to-always-on-availability-groups"></a>Voraussetzungen für das Konvertieren des Protokollversands in Always On-Verfügbarkeitsgruppen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

  In diesem Thema werden die erforderlichen Komponenten zum Konvertieren einer primären Datenbank für den Protokollversand zusammen mit einer oder mehreren sekundären Datenbanken in eine primäre AlwaysOn-Datenbank und sekundäre Datenbank(en) beschrieben.  
  
> [!NOTE]  
>  Sie können jede primäre oder sekundäre (ggf. lesbare) Datenbank in einer Verfügbarkeitsgruppe als primäre Datenbank für den Protokollversand konfigurieren.  
  
  
##  <a name="availability-group-prerequisites"></a><a name="AGPrereqsRealAddress"></a> Erforderliche Komponenten für Verfügbarkeitsgruppen  
 Damit Sicherungsaufträge auf dem primären Replikat der Verfügbarkeitsgruppe ausgeführt werden können, verwenden Sie die folgenden Sicherungseinstellungen für AlwaysOn-Verfügbarkeitsgruppen:  
  
|Eigenschaft|Einstellung|  
|--------------|-------------|  
|Die Voreinstellung für die automatisierte Sicherung der Verfügbarkeitsgruppe.|Nur auf dem primären Replikat|  
|Sicherungspriorität des primären Replikats.|>0|  
  
 **Weitere Informationen:**  
  
 [Anzeigen von Verfügbarkeitsgruppeneigenschaften &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-properties-sql-server.md)  
  
 [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="log-shipping-prerequisites"></a><a name="LogShipPrereqs"></a> Erforderliche Komponenten für den Protokollversand  
  
-   Die primäre Datenbank für den Protokollversand muss sich auf der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] befinden, auf der das anfängliche/aktuelle primäre Replikat der Verfügbarkeitsgruppe gehostet wird.  
  
-   Damit eine angegebene sekundäre Datenbank für den Protokollversand in eine sekundäre AlwaysOn-Datenbank konvertiert werden kann, muss Folgendes erfüllt sein:  
  
    -   Sie muss den gleichen Namen wie die primäre Datenbank verwenden.  
  
    -   Sie muss auf einer Serverinstanz befinden, auf der ein sekundäres Replikat für die Verfügbarkeitsgruppe gehostet wird.  
  
 Sobald der Sicherungsauftrag auf der primären Datenbank ausgeführt wurde, deaktivieren Sie den Sicherungsauftrag, und sobald der Wiederherstellungsauftrag auf einer angegebenen sekundären Datenbank ausgeführt wurde, deaktivieren Sie den Wiederherstellungsauftrag.  
  
 Nachdem Sie alle sekundären Datenbanken für die Verfügbarkeitsgruppe erstellt haben, sofern Sie Sicherungen auf sekundären Replikaten ausführen möchten, müssen Sie die Voreinstellung zur automatisierten Sicherung der Verfügbarkeitsgruppe neu konfigurieren.  
  
 **Weitere Informationen:**  
  
 [Converting a log shipping configuration to Availability Group (Konvertieren einer Protokollversandkonfiguration in eine Verfügbarkeitsgruppe)](https://blogs.msdn.microsoft.com/sqlalwayson/2012/01/09/converting-a-logshipping-configuration-to-availability-group/) (ein SQL Server-Blog)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **Protokollversand**  
  
-   [Aktualisieren des Protokollversands auf SQL Server 2016 &#40;Transact-SQL&#41;](../../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Entfernen des Protokollversands &#40;SQL Server&#41;](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
 **AlwaysOn-Verfügbarkeitsgruppen**  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Dialogfelds Neue Verfügbarkeitsgruppe &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Erstellen einer Verfügbarkeitsgruppe &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [Erstellen einer Verfügbarkeitsgruppe &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [Konvertieren einer Protokollversandkonfiguration in eine Verfügbarkeitsgruppe](https://blogs.msdn.microsoft.com/sqlalwayson/2012/01/09/converting-a-logshipping-configuration-to-availability-group/)  
  
     [Hinzufügen einer primären Datenbank für den Protokollversand und mindestens einer sekundären Datenbank zu einer vorhandenen Verfügbarkeitsgruppe](https://blogs.msdn.microsoft.com/sqlalwayson/2012/02/01/add-a-log-shipping-primary-database-and-secondary-databases-to-an-existing-availability-group/)  
  
     [SQL Server Always On Team Blogs: The official SQL Server Always On Team Blog (SQL Server Always On-Teamblogs: Der offizielle SQL Server Always On-Teamblog)](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
     [CSS SQL Server-Technikblogs](https://docs.microsoft.com/archive/blogs/psssql/)  
  
-   **Whitepaper:**  
  
     [Migrationshandbuch: Migrieren zu AlwaysOn-Verfügbarkeitsgruppen von vorherigen Bereitstellungen, in denen Datenbankspiegelung und Protokollversand kombiniert sind](https://msdn.microsoft.com/library/jj635217)  
  
     [Microsoft-Whitepapers für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](https://techcommunity.microsoft.com/t5/DataCAT/bg-p/DataCAT/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Überwachen von Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)  
  
  
