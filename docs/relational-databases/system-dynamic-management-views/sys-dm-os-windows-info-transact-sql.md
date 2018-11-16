---
title: dm_os_windows_info (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f258d7e49f86ed8015d8e51f2373633b7d7f10c4
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51663138"
---
# <a name="sysdmoswindowsinfo-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt in einer Zeile Informationen zur Windows-Betriebssystemversion zurück.  
  
  Gilt nur für SQL Server unter Windows. Verwenden, um ähnliche Informationen finden in SQL Server auf einem nicht-Windows-Host, z.B. Linux, [dm_os_host_info &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Für Windows können Sie die Release-Anzahl zurück. Eine Liste der Werte mit Beschreibungen finden Sie unter [Betriebssystemversion (Windows)](/windows/desktop/SysInfo/operating-system-version). Lässt keine NULL-Werte zu.|  
|**windows_service_pack_level**|**nvarchar(256)**| Für Windows gibt die Nummer des Service Packs. Lässt keine NULL-Werte zu. |  
|**windows_sku**|**int**|Für Windows gibt die Stock beibehalten Unit (SKU) von Windows-ID. Eine Liste mit SKU-IDs und Beschreibungen finden Sie unter [Funktion "GetProductInfo"](https://msdn.microsoft.com/library/ms724358.aspx). Lässt NULL-Werte. |  
|**os_language_version**|**int**| Für Windows gibt den Windows-Gebietsschemabezeichner (LCID) des Betriebssystems. Eine Liste mit LCID-Werten und Beschreibungen finden Sie unter [Von Microsoft zugewiesene Gebietsschemabezeichner (LCIDs)](https://go.microsoft.com/fwlink/?LinkId=208080). Lässt keine NULL-Werte zu.|  
  
  
## <a name="permissions"></a>Berechtigungen  
Die SELECT-Berechtigung für dm_os_windows_info wird standardmäßig die public-Rolle gewährt. Wenn aufgehoben wird, ist die VIEW SERVER STATE-Berechtigung auf dem Server erforderlich.  

## <a name="limitations-and-restrictions"></a>Einschränkungen
Verwenden, um Informationen für die Ausführung von SQL auf einem nicht-Windows-Host, z.B. Linux, finden Sie unter [dm_os_host_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
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
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  

