---
title: sys. dm_os_host_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/10/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_os_host_info
- sys.dm_os_host_info_TSQL
- dm_os_host_info
- dm_os_host_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_host_info dynamic management view
ms.assetid: 9bb6ef86-957b-4ca1-ad20-ca2f8460a86d
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8275ed39d49c8fdb64c1d2f26cc1d218c525500c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830509"
---
# <a name="sysdm_os_host_info-transact-sql"></a>sys. dm_os_host_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Gibt eine Zeile zurück, in der Informationen zur Betriebssystemversion angezeigt werden.  
  
|Spaltenname |Datentyp |BESCHREIBUNG |  
|-----------------|---------------|-----------------|  
|**host_platform** |**nvarchar(256)** |Der Typ des Betriebssystems: Windows oder Linux |
|**host_distribution** |**nvarchar(256)** |Die Beschreibung des Betriebssystems. |
|**host_release**|**nvarchar(256)**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Betriebssystemversion (Versionsnummer). Eine Liste der Werte mit Beschreibungen finden Sie unter [Betriebssystemversion (Windows)](/windows/desktop/SysInfo/operating-system-version). <br> Für Linux wird eine leere Zeichenfolge zurückgegeben. |  
|**host_service_pack_level**|**nvarchar(256)**|Service Pack-Ebene des Windows-Betriebssystems. <br> Für Linux wird eine leere Zeichenfolge zurückgegeben. |  
|**host_sku**|**int**|Windows-SKU-ID (Stock Keeping Unit). Eine Liste mit SKU-IDs und Beschreibungen finden Sie unter [Funktion "GetProductInfo"](https://msdn.microsoft.com/library/ms724358.aspx). Lässt NULL-Werte zu. <br> Für Linux wird NULL zurückgegeben. |  
|**os_language_version**|**int**|Windows-Gebietsschemabezeichner (LCID) des Betriebssystems. Eine Liste mit LCID-Werten und Beschreibungen finden Sie unter [Von Microsoft zugewiesene Gebietsschemabezeichner (LCIDs)](https://go.microsoft.com/fwlink/?LinkId=208080). Lässt keine NULL-Werte zu.|  

## <a name="remarks"></a>Bemerkungen  
Diese Ansicht ähnelt [sys. dm_os_windows_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)und fügt Spalten hinzu, um Windows und Linux zu unterscheiden.
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
Die- `SELECT` Berechtigung für `sys.dm_os_host_info` wird der `public` Rolle standardmäßig erteilt. Wenn widerrufen, wird `VIEW SERVER STATE` die-Berechtigung auf dem Server benötigt.   
 
> [!CAUTION]
>  Ab Version [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1,3 [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] erfordert Version 17 die- `SELECT` Berechtigung für, um eine Verbindung mit `sys.dm_os_host_info` herzustellen [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] . Wenn `SELECT` die Berechtigung in widerrufen wird `public` , können nur Anmeldungen mit `VIEW SERVER STATE` der-Berechtigung eine Verbindung mit der neuesten Version von SSMS herstellen. (Andere Tools, wie z `sqlcmd.exe` . b., können ohne Berechtigung für eine Verbindung herstellen `SELECT` `sys.dm_os_host_info` .)

  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Spalten aus der **sys. dm_os_host_info** -Sicht zurückgegeben.  
  
```  
SELECT host_platform, host_distribution, host_release, 
    host_service_pack_level, host_sku, os_language_version  
FROM sys.dm_os_host_info;  
```  

Im folgenden finden Sie ein Beispiel für ein Resultset unter Windows:
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Windows   |Windows Server 2012 R2 Standard    |6.3    |   |7  |1033 |  

Im folgenden finden Sie ein Beispiel für ein Resultset unter Linux:
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Linux |Ubuntu |16.04  |   |NULL   |1033 |  

  
## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_os_sys_info &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_windows_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)  
 

