---
title: Konfigurieren von Sicherungskomprimierung (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 430905eb-d218-458c-bd48-aeee6fbb7446
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bcfc0dea167b972f4e463333ab6851b038a284ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62922251"
---
# <a name="configure-backup-compression-sql-server"></a>Konfigurieren von Sicherungskomprimierung (SQL Server)
  Die Sicherungskomprimierung wird bei der Installation standardmäßig deaktiviert. Das Standardverhalten für die Sicherungskomprimierung wird auf Serverebene durch die Konfigurationsoption **backup compression default** definiert. Sie können jedoch die Standardeinstellung auf Serverebene überschreiben, wenn Sie eine einzelne Sicherung erstellen oder eine Reihe von Routinesicherungen einplanen. Zum Ändern der Standardeinstellung auf Serverlevel gehen Sie unter [Anzeigen oder Konfigurieren der Serverkonfigurationsoption Standardeinstellung für die Sicherungskomprimierung](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).  
  
## <a name="override-the-backup-compression-default"></a>Überschreiben der Standardeinstellung für die Sicherungskomprimierung  
 Sie können das Verhalten der Sicherungskomprimierung für eine einzelne Sicherung, einen Sicherungsauftrag oder eine Protokollversandkonfiguration ändern.  
  
-   **[!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
     Verwenden Sie WITH NO_COMPRESSION oder WITH COMPRESSION in der [BACKUP](/sql/t-sql/statements/backup-transact-sql)-Anweisung, um die Standardeinstellung für die Serversicherungskomprimierung zu überschreiben.  
  
     Bei einer Protokollversandkonfiguration können Sie das Verhalten der Sicherungskomprimierung für Protokollsicherungen mithilfe von [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql) steuern.  
  
-   **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
     Informationen zum Anzeigen oder Konfigurieren der Standardoption für die Sicherungskomprimierung für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], gehen Sie unter [Anzeigen oder Konfigurieren der Serverkonfigurationsoption Standardeinstellung für die Sicherungskomprimierung](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).  
  
     Sie können die Standardeinstellung für die Serversicherungskomprimierung beim Erstellen einer Sicherung überschreiben, indem Sie die Optionen **Sicherung komprimieren** oder **Sicherung nicht komprimieren** in einem der folgenden Dialogfelder angeben:  
  
    -   [Datenbank sichern (Seite Optionen)](back-up-database-backup-options-page.md)  
  
         Beim Sichern einer Datenbank können Sie die Sicherungskomprimierung für eine einzelne Datenbank, Datei oder Protokollsicherung steuern.  
  
    -   [Verwenden des Wartungsplanungs-Assistenten](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
         Mit dem Wartungsplanungs-Assistenten können Sie die Sicherungskomprimierung bei jeder Gruppe von geplanten vollständigen oder differenziellen Datenbank- bzw. Protokollsicherungen steuern.  
  
    -   Integration Services (SSIS) [Task "Datenbank sichern"](../../integration-services/control-flow/back-up-database-task.md)  
  
         Sie können das Verhalten der Sicherungskomprimierung steuern, wenn Sie ein Paket für die Sicherung einer einzelnen oder mehrerer Datenbanken erstellen.  
  
    -   [Sicherungseinstellungen für den Transaktionsprotokollversand](../databases/log-shipping-transaction-log-backup-settings.md)  
  
         Sie können das Sicherungskomprimierungsverhalten von Protokollsicherungen steuern.  
  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherungskomprimierung &#40;SQL Server&#41;](backup-compression-sql-server.md)  
  
  
