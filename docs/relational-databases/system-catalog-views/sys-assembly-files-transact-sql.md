---
description: sys.assembly_files (Transact-SQL)
title: sys. assembly_files (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.assembly_files
- assembly_files_TSQL
- assembly_files
- sys.assembly_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_files catalog view
ms.assetid: 1a384a2c-5556-4d12-a2ba-4da781363143
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f1e0a3b19a23cfd999ec2b4c1fc5468f53b746ee
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542680"
---
# <a name="sysassembly_files-transact-sql"></a>sys.assembly_files (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jede Datei, aus der eine Assembly besteht.  
    
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|Die ID der Assembly, zu der die Datei gehört.|  
|**name**|**nvarchar(260)**|Der Name der Assemblydatei.|  
|**file_id**|**int**|Die ID der Datei. Sie ist innerhalb einer Assembly eindeutig. Die Datei-ID 1 stellt die Assembly-DLL dar.|  
|**content**|**varbinary(max)**|Der Inhalt der Datei.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [CLR-assemblykatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Assemblyproperty &#40;Transact-SQL-&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
