---
title: sys. dm_os_loaded_modules (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f43e03e482bb7125100ed7bed56337fb75a2e711
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900092"
---
# <a name="sysdm_os_loaded_modules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt für jedes in den Serveradressbereich geladene Modul eine Zeile zurück.  
  
> [!NOTE]  
>  Um dies in aufzurufen [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys. dm_pdw_nodes_os_loaded_modules**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|Adresse des Moduls im Prozess.|  
|**file_version**|**varchar (23)**|Version der Datei. Hält das folgende Format ein:<br /><br /> x.x:x.x|  
|**product_version**|**varchar (23)**|Version des Produkts. Hält das folgende Format ein:<br /><br /> x.x:x.x|  
|**gen**|**bit**|1 = Modul ist eine Debugversion des geladenen Moduls.|  
|**patched**|**bit**|1 = Modul wurde gepatcht.|  
|**vorab**|**bit**|1 = Modul ist eine Vorabversion des geladenen Moduls.|  
|**private_build**|**bit**|1 = Modul ist ein privater Build des geladenen Moduls.|  
|**special_build**|**bit**|1 = Modul ist ein spezieller Build des geladenen Moduls.|  
|**Kurse**|**int**|Sprache der Versionsinformationen des Moduls.|  
|**Geschäfts**|**nvarchar(256)**|Name des Unternehmens, von dem das Modul erstellt wurde.|  
|**Beschreibung**|**nvarchar(256)**|Beschreibung des Moduls.|  
|**name**|**nvarchar(255)**|Name des Moduls. Schließt den vollständigen Pfad des Moduls ein.|  
|**pdw_node_id**|**int**|**Gilt für**:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server dynamischen Verwaltungs Sichten im Zusammenhang mit dem Betriebs System &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
