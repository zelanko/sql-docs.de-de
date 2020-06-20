---
title: Entfernen des Protokollversands (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], removing
- removing log shipping
- deleting log shipping
ms.assetid: 859373db-c744-4a4b-8479-45163f61e8cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 14fdc36c66073e89dcc2014aed4319a2ce78a98f
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931111"
---
# <a name="remove-log-shipping-sql-server"></a>Entfernen des Protokollversands (SQL Server)
  In diesem Thema wird beschrieben, wie der Protokollversand in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]entfernt wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So entfernen Sie den Protokollversand mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die gespeicherten Prozeduren für den Protokollversand erfordern die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-remove-log-shipping"></a>So entfernen Sie den Protokollversand  
  
1.  Stellen Sie eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, die derzeit als primärer Server für den Protokollversand verwendet wird, und erweitern Sie diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, klicken Sie mit der rechten Maustaste auf die primäre Datenbank für den Protokollversand, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie unter **Seite auswählen**auf **Transaktionsprotokollversand**.  
  
4.  Entfernen Sie das Kontrollkästchen vor **Diese Datenbank als primäre Datenbank in einer Protokollversandkonfiguration aktivieren** .  
  
5.  Klicken Sie auf **OK** , um den Protokollversand aus dieser primären Datenbank zu entfernen.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-remove-log-shipping"></a>So entfernen Sie den Protokollversand  
  
1.  Führen Sie auf dem primären Server für den Protokollversand [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) aus, um die Informationen zur sekundären Datenbank vom primären Server zu löschen.  
  
2.  Führen Sie auf dem sekundären Server für den Protokollversand [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) aus, um die sekundäre Datenbank zu löschen.  
  
    > [!NOTE]  
    >  Falls keine anderen sekundären Datenbanken mit der gleichen sekundären ID vorhanden sind, wird **sp_delete_log_shipping_secondary_primary** von **sp_delete_log_shipping_secondary_database** aufgerufen und löscht den Eintrag für die sekundäre ID sowie die Kopier- und Wiederherstellungsaufträge.  
  
3.  Führen Sie auf dem primären Server für den Protokollversand **sp_delete_log_shipping_primary_database** aus, um die Informationen zur Protokollversandkonfiguration vom primären Server zu löschen. Dadurch wird auch der Sicherungsauftrag gelöscht.  
  
4.  Deaktivieren Sie auf dem primären Server für den Protokollversand den Sicherungsauftrag. Weitere Informationen finden sie unter [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).  
  
5.  Deaktivieren Sie auf dem sekundären Server für den Protokollversand den Kopier- und Wiederherstellungsauftrag.  
  
6.  Wenn Sie die sekundäre Datenbank für den Protokollversand nicht mehr verwenden, können Sie sie auch vom sekundären Server löschen.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Aktualisieren des Protokoll Versands auf SQL Server 2014 &#40;Transact-SQL-&#41;](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Konfigurieren des Protokollversands &#40;SQL Server&#41;](configure-log-shipping-sql-server.md)  
  
-   [Hinzufügen einer sekundären Datenbank zu einer Protokollversandkonfiguration &#40;SQL Server&#41;](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [Entfernen einer sekundären Datenbank aus einer Protokollversandkonfiguration &#40;SQL Server&#41;](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [Überwachen des Protokollversands &#40;Transact-SQL&#41;](monitor-log-shipping-transact-sql.md)  
  
-   [Failover zu einer sekundären Datenbank für den Protokollversand &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](about-log-shipping-sql-server.md)   
 [Protokollversandtabellen und gespeicherte Prozeduren](log-shipping-tables-and-stored-procedures.md)  
  
  
