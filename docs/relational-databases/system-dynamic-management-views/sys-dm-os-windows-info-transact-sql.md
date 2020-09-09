---
description: sys.dm_os_windows_info (Transact-SQL)
title: sys. dm_os_windows_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_windows_info
- dm_os_windows_info_TSQL
- sys.dm_os_windows_info
- sys.dm_os_windows_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_windows_info dynamic management view
ms.assetid: adc81283-fdc2-46c0-bb48-abe82bbf2459
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ba205fe097367dc273d22d49d54f51a31cedbbfc
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89531757"
---
# <a name="sysdm_os_windows_info-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt in einer Zeile Informationen zur Windows-Betriebssystemversion zurück.  
  
  Gilt nur für SQL Server, die unter Windows ausgeführt wird. Verwenden Sie [sys. dm_os_host_info &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md), um eine ähnliche Information für SQL Server, die auf einem nicht-Windows-Host ausgeführt wird, wie z. b. Linux, anzuzeigen. 
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Für Windows wird die Releasenummer zurückgegeben. Eine Liste der Werte mit Beschreibungen finden Sie unter [Betriebssystemversion (Windows)](/windows/desktop/SysInfo/operating-system-version). Lässt keine NULL-Werte zu.|  
|**windows_service_pack_level**|**nvarchar(256)**| Für Windows wird die Service Pack Zahl zurückgegeben. Lässt keine NULL-Werte zu. |  
|**windows_sku**|**int**|Für Windows wird die Windows-SKU-ID (Stock Keeping Unit) zurückgegeben. Eine Liste mit SKU-IDs und Beschreibungen finden Sie unter [Funktion "GetProductInfo"](https://msdn.microsoft.com/library/ms724358.aspx). Lässt NULL-Werte zu. |  
|**os_language_version**|**int**| Für Windows gibt den Windows-Gebiets Schema Bezeichner (LCID) des Betriebssystems zurück. Eine Liste mit LCID-Werten und Beschreibungen finden Sie unter [Von Microsoft zugewiesene Gebietsschemabezeichner (LCIDs)](https://go.microsoft.com/fwlink/?LinkId=208080). Lässt keine NULL-Werte zu.|  
  
  
## <a name="permissions"></a>Berechtigungen  
Die SELECT-Berechtigung für sys. dm_os_windows_info wird standardmäßig der public-Rolle erteilt. Wenn Sie widerrufen wird, ist die View Server State-Berechtigung auf dem Server erforderlich.  

## <a name="limitations-and-restrictions"></a>Einschränkungen
Verwenden Sie [sys. dm_os_host_info &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md), um die Informationen zur Ausführung von SQL auf einem nicht-Windows-Host (z. b. Linux) anzuzeigen. 
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Spalten aus der Sicht **sys.dm_os_windows_info** zurückgegeben.  
  
```  
SELECT windows_release, windows_service_pack_level, windows_sku, os_language_version  
FROM sys.dm_os_windows_info;  
```  
  
 Hier ist ein Beispielresultset.  
  
 `windows_release  windows_service_pack_level   windows_sku   os_language_version`  
  
 `---------------  ---------------------------  ------------  -------------------`  
  
 `6.0              Service Pack 2                4            1033`  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  

