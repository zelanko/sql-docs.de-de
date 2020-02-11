---
title: sys. dm_os_dispatcher_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_dispatcher_pools_TSQL
- dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_os_dispatcher_pools DMV
ms.assetid: b9edbc83-c6bc-4753-9bb5-a454cfe7d6bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: cf8e1700f51f808811a1f5a61f86777547c9cb65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265855"
---
# <a name="sysdm_os_dispatcher_pools-transact-sql"></a>sys.dm_os_dispatcher_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu Sitzungsverteilerpools zurück. Verteilerpools sind von Systemkomponenten verwendete Threadpools für die Hintergrundverarbeitung.  
  
> [!NOTE]  
>  Um dies von oder [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]aus aufzurufen, verwenden Sie den Namen **sys. dm_pdw_nodes_os_dispatcher_pools**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|dispatcher_pool_address|**varbinary(8)**|Die Adresse des Verteilerpools. dispatcher_pool_address ist eindeutig. Lässt keine NULL-Werte zu.|  
|type|**nvarchar(256)**|Der Typ des Verteilerpools. Lässt keine NULL-Werte zu. Es gibt zwei Typen von Verteilerpools:<br /><br /> DISP_POOL_XE_ENGINE<br /><br /> DISP_POOL_XE_SESSION<br /><br /> Abfragen der DMV für die vollständige Liste|  
|name|**nvarchar(256)**|Der Name des Verteilerpools Lässt keine NULL-Werte zu.|  
|dispatcher_count|**int**|Die Anzahl aktiver Verteilerthreads Lässt keine NULL-Werte zu.|  
|dispatcher_ideal_count|**int**|Die Anzahl zu verwendender Verteilerthreads, die der Verteilerpool erhöhen kann. Lässt keine NULL-Werte zu.|  
|dispatcher_timeout_ms|**int**|Die Zeit in Millisekunden, die ein Verteiler auf neue Arbeit wartet, bevor er beendet wird. Lässt keine NULL-Werte zu.|  
|dispatcher_waiting_count|**int**|Die Anzahl von Verteilerthreads im Leerlauf. Lässt keine NULL-Werte zu.|  
|queue_length|**int**|Die Anzahl von Arbeitselementen, die auf die Verarbeitung durch den Verteilerpool warten. Lässt keine NULL-Werte zu.|  
|pdw_node_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="permissions"></a>Berechtigungen

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ist die `VIEW SERVER STATE` -Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die `VIEW DATABASE STATE` -Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   

## <a name="see-also"></a>Weitere Informationen  
  
  


