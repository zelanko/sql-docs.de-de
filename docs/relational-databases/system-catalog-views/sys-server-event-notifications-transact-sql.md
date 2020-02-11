---
title: sys. server_event_notifications (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_event_notifications
- sys.server_event_notifications
- sys.server_event_notifications_TSQL
- server_event_notifications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_notifications catalog view
ms.assetid: 1a83a044-3130-4551-95ca-162525846ff5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e3eaa1bdfa45e0c3e0b0412b8852e134c43c3eb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124991"
---
# <a name="sysserver_event_notifications-transact-sql"></a>sys.server_event_notifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jedes Ereignisbenachrichtigungsobjekt auf Serverebene zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name der Serverereignisbenachrichtigung. Er ist für alle Ereignisbenachrichtigungen auf Serverebene eindeutig.|  
|**object_id**|**int**|Objekt-ID. Sie ist innerhalb der **master** -Datenbank eindeutig.|  
|**parent_class**|**tinyint**|Klasse des übergeordneten Objekts. Ist immer 100 = Server.|  
|**parent_class_desc**|**nvarchar (60)**|Die Beschreibung der Klasse des übergeordneten Objekts. Ist immer SERVER.|  
|**parent_id**|**int**|Ist immer 0.|  
|**create_date**|**datetime**|Erstellungsdatum.|  
|**modify_date**|**datetime**|Datum der letzten Objektänderungen mithilfe einer ALTER-Anweisung.|  
|**service_name**|**nvarchar(256)**|Name des Zieldienstes, an den die Benachrichtigung gesendet wird.|  
|**broker_instance**|**nvarchar(128)**|Der Service Broker, bei dem der benannte Zieldienst definiert ist.|  
|**creator_sid**|**varbinary(85)**|SID des Anmeldenamens, der die Anweisung ausführt, mit der die Ereignisbenachrichtigung erstellt wird. NULL, wenn WITH FAN_IN nicht in der Definition der Ereignisbenachrichtigung angegeben ist.|  
|**principal_id**|**int**|ID des Serverprinzipals, der der Besitzer ist.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
