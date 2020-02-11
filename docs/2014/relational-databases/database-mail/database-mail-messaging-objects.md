---
title: Messagingobjekte für Datenbank-E-Mail | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], host databases
- Database Mail [SQL Server], messaging objects
- mail host databases [SQL Server]
- host databases [Database Mail]
ms.assetid: 5aa2886e-1db1-4066-85df-57ccf4538c54
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3657e45d18ac84ad737a016150692730f736b55f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62917703"
---
# <a name="database-mail-messaging-objects"></a>Messagingobjekte für Datenbank-E-Mail
  Die **msdb** -Datenbank ist die Hostdatenbank der Datenbank-E-Mail. Diese Datenbank enthält die gespeicherten Prozeduren und Messagingobjekte für Datenbank-E-Mail. Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] enthält den Assistenten zum Konfigurieren von Datenbank-E-Mail, um Datenbank-E-Mail zu aktivieren, Profile und Konten zu erstellen und zu verwalten sowie Datenbank-E-Mail-Optionen zu konfigurieren.  
  
##  <a name="ComponentsAndConcepts"></a> Objekte in der **msdb** -Datenbank  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] muss in der **msdb** -Datenbank aktiviert sein. Allerdings wird für Datenbank-E-Mail kein [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Netzwerk verwendet. Deshalb müssen Benutzer keinen [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Endpunkt erstellen, um Datenbank-E-Mail zu verwenden. Für den externen Datenbank-E-Mail-Vorgang wird eine standardmäßige [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindung verwendet, um mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu kommunizieren.  
  
 Datenbank-E-Mail legt in der **msdb** -Datenbank die folgenden Objekte offen, wenn Datenbank-E-Mail aktiviert ist.  
  
 Diese Objekte sind die Schnittstelle für Datenbank-E-Mail innerhalb der Mailhost-Datenbank. Andere Objekte werden installiert, um die Funktionalität zu implementieren, die von den oben aufgeführten Objekten bereitgestellt wird. Diese Objekte sind jedoch für die interne Verwendung reserviert.  
  
|Name|type|BESCHREIBUNG|  
|----------|----------|-----------------|  
|[sysmail_allitems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-allitems-transact-sql)|`View`|Listet alle an Datenbank-E-Mail übergebenen Nachrichten auf.|  
|[sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql)|`View`|Listet Meldungen über das Verhalten von [Database Mail External Program](database-mail-external-program.md)auf.|  
|[sysmail_faileditems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-faileditems-transact-sql)|`View`|Informationen über Nachrichten, die Datenbank-E-Mail nicht senden konnte.|  
|[sysmail_mailattachments &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql)|`View`|Informationen über Anlagen von Datenbank-E-Mail-Nachrichten.|  
|[sysmail_sentitems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-sentitems-transact-sql)|`View`|Informationen über Nachrichten, die mit Datenbank-E-Mail gesendet wurden.|  
|[sysmail_unsentitems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql)|`View`|Informationen über Nachrichten, die Datenbank-E-Mail gerade zu senden versucht.|  
|[sp_send_dbmail &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql)|`Stored Procedure`|Sendet E-Mail-Nachrichten mithilfe von Datenbank-E-Mail.|  
|[sysmail_delete_log_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql)|`Stored Procedure`|Löscht Nachrichten aus dem Datenbank-E-Mail-Protokoll.|  
|[sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql)|`Stored Procedure`|Löscht E-Mail-Elemente aus der Datenbank-E-Mail-Warteschlange.|  
|[sysmail_help_status_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-help-status-sp-transact-sql)|`Stored Procedure`|Zeigt an, ob Datenbank-E-Mail gestartet wird.|  
|[sysmail_start_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql)|`Stored Procedure`|Startet die Service Broker-Objekte, die vom externen Programm verwendet werden. Diese Objekte werden standardmäßig gestartet.|  
|[sysmail_stop_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql)|`Stored Procedure`|Beendet die Service Broker-Objekte, die vom externen Programm verwendet werden.|  
  

  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](database-mail.md)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
