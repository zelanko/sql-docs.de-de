---
title: sys. Messages (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- messages_TSQL
- sys.messages_TSQL
- sys.messages
- messages
dev_langs:
- TSQL
helpviewer_keywords:
- error messages [SQL Server]
- sys.messages catalog view
- error numbers [SQL Server]
ms.assetid: 8c16ecdf-68f4-4a2a-b594-086e3344e58a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f1b75961f4d41a87e86c9a103a62ca128ce443e3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720428"
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>Meldungskatalogsichten (für Fehlermeldungen): sys.messages
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jede **message_id** oder **language_id** der Fehlermeldungen im System, sowohl für System definierte als auch für benutzerdefinierte Meldungen. Weitere Informationen finden Sie unter [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md).  
   
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**message_id**|**int**|ID der Meldung. Ist innerhalb des gesamten Servers eindeutig. Bei Meldungs-IDs unterhalb von 50000 handelt es sich um Systemmeldungen.|  
|**language_id**|**smallint**|Die Sprach-ID, für die der Text in **Text** verwendet wird, wie in " **syslanguages**" definiert. Dies ist für eine angegebene **message_id**eindeutig.|  
|**severity**|**tinyint**|Schweregrad des Fehlers, der zwischen 1 und 25 liegen kann. Dies ist für alle Nachrichten Sprachen innerhalb einer **message_id**identisch.|  
|**is_event_logged**|**bit**|1 = Bei einer Fehlerausgabe wird eine Meldung in das Ereignisprotokoll geschrieben. Dies ist für alle Nachrichten Sprachen innerhalb einer **message_id**identisch.|  
|**text**|**nvarchar (2048)**|Text der Meldung, die verwendet wird, wenn die entsprechende **language_id** aktiv ist.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Nachrichten &#40;für Fehler&#41; Katalog Sichten &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [Programmierung von Ausnahme Meldungs Feldern](https://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [Fehlermeldungen](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [Ereignisse und Fehler Datenbank-Engine](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
