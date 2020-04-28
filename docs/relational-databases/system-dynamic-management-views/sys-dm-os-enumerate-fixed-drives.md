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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fa5834c14bfb1fafe3123c28a60359d64d059dfc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "71342515"
---
# <a name="sysdm_os_enumerate_fixed_drives-transact-sql"></a>sys. dm_os_enumerate_fixed_drives (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Eingeführt in SQL Server 2019.

Listet Volumes auf, die auf Laufwerk Buchstaben wie `C:\`bereitgestellt werden.

|Spaltenname|Datentyp|BESCHREIBUNG|
|-----------------|---------------|-----------------|  
|`fixed_drive_path`|`nvarchar(512)`|Der Pfad zum Volume, wie `C:\`z. b..|  
|`drive_type`|`int`|Code für den Laufwerkstyp. Siehe [ `GetDriveTypeW` Function](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`drive_type_desc`|`nvarchar(512)`|Die Beschreibung des Laufwerks Typs. Siehe [ `GetDriveTypeW` Function](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`free_space_in_bytes`|`bigint`|Freier Speicherplatz auf dem Datenträger in Byte.|

## <a name="permissions"></a>Berechtigungen

Der Benutzer muss über `VIEW SERVER STATE` die-Berechtigung auf dem Server verfügen.

## <a name="see-also"></a>Weitere Informationen  

 [Dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Mit e/a verbundene dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
