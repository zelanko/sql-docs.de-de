---
title: sys. dm_os_enumerate_fixed_drives (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/18/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_enumerate_fixed_drives
- sys.dm_os_enumerate_fixed_drives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_enumerate_fixed_drives dynamic management view
ms.assetid: 2e27489e-cf69-4a89-9036-77723ac3de66
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c45db91b29c85d6ffced4e31e01fb8f24f338c16
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830528"
---
# <a name="sysdm_os_enumerate_fixed_drives-transact-sql"></a>sys. dm_os_enumerate_fixed_drives (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Eingeführt in SQL Server 2019.

Listet Volumes auf, die auf Laufwerk Buchstaben wie bereitgestellt werden `C:\` .

|Spaltenname|Datentyp|BESCHREIBUNG|
|-----------------|---------------|-----------------|  
|`fixed_drive_path`|`nvarchar(512)`|Der Pfad zum Volume, wie z `C:\` . b..|  
|`drive_type`|`int`|Code für den Laufwerkstyp. Siehe [ `GetDriveTypeW` Function](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`drive_type_desc`|`nvarchar(512)`|Die Beschreibung des Laufwerks Typs. Siehe [ `GetDriveTypeW` Function](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`free_space_in_bytes`|`bigint`|Freier Speicherplatz auf dem Datenträger in Byte.|

## <a name="permissions"></a>Berechtigungen

Der Benutzer muss `VIEW SERVER STATE` über die-Berechtigung auf dem Server verfügen.

## <a name="see-also"></a>Weitere Informationen  

 [Dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Mit e/a verbundene dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
