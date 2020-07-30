---
title: sys. dm_io_pending_io_requests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_pending_io_requests
- dm_io_pending_io_requests
- dm_io_pending_io_requests_TSQL
- sys.dm_io_pending_io_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_pending_io_requests dynamic management view
ms.assetid: d1fb46dd-5c74-4c04-9ecf-8934b1bedb5b
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d189ba90bb8597f2c23b143528cba1c8b225709
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396336"
---
# <a name="sysdm_io_pending_io_requests-transact-sql"></a>sys.dm_io_pending_io_requests (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt eine Zeile für jede ausstehende E/A-Anforderung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück.  
  
> [!NOTE]  
>  Um dies von oder aus aufzurufen [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , verwenden Sie den Namen **sys. dm_pdw_nodes_io_pending_io_requests**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**io_completion_request_address**|**varbinary(8)**|Arbeitsspeicheradresse der E/A-Anforderung. Lässt keine NULL-Werte zu.|  
|**io_type**|**nvarchar(60)**|Typ der ausstehenden E/A-Anforderung. Lässt keine NULL-Werte zu.|  
|**io_pending_ms_ticks**|**bigint**|Nur zur internen Verwendung. Lässt keine NULL-Werte zu.| 
|**io_pending**|**int**|Gibt an, ob die E/A-Anforderung ausstehend ist oder von Windows abgeschlossen wurde. Eine E/A-Anforderung kann noch ausstehend sein, selbst wenn Windows die Anforderung abgeschlossen hat, aber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] noch keinen Kontextwechsel ausgeführt hat, bei dem die E/A-Anforderung verarbeitet und aus dieser Liste entfernt würde. Lässt keine NULL-Werte zu.|  
|**io_completion_routine_address**|**varbinary(8)**|Interne Funktion, die nach Abschluss der E/A-Anforderung aufgerufen wird. Lässt NULL-Werte zu.|  
|**io_user_data_address**|**varbinary(8)**|Nur zur internen Verwendung. Lässt NULL-Werte zu.|  
|**scheduler_address**|**varbinary(8)**|Das Zeitplanungsmodul, in dem diese E/A-Anforderung ausgestellt wurde. Die E/A-Anforderung wird in der Liste ausstehender E/A-Anforderungen des Zeitplanungsmoduls angezeigt. Weitere Informationen finden Sie unter [sys. dm_os_schedulers &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md). Lässt keine NULL-Werte zu.|  
|**io_handle**|**varbinary(8)**|Dateihandle der Datei, die in der E/A-Anforderung verwendet wird. Lässt NULL-Werte zu.|  
|**io_offset**|**bigint**|Offset der E/A-Anforderung. Lässt keine NULL-Werte zu.|  
|**io_handle_path**|**nvarchar(256)**| Der Pfad der Datei, die in der e/a-Anforderung verwendet wird. Lässt NULL-Werte zu.|
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="permissions"></a>Berechtigungen  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist die- `VIEW SERVER STATE` Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die- `VIEW DATABASE STATE` Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [In Beziehung stehende dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


