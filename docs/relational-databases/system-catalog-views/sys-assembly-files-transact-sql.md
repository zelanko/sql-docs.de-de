---
title: Sys. assembly_files (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0279d6c2850dff07b365e7543f387f6cf6e9f328
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62516082"
---
# <a name="sysassemblyfiles-transact-sql"></a>sys.assembly_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Datei, aus der eine Assembly besteht.  
    
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|Die ID der Assembly, zu der die Datei gehört.|  
|**name**|**nvarchar(260)**|Der Name der Assemblydatei.|  
|**file_id**|**int**|Die ID der Datei. Sie ist innerhalb einer Assembly eindeutig. Die Datei-ID 1 stellt die Assembly-DLL dar.|  
|**content**|**varbinary(max)**|Der Inhalt der Datei.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-Assemblykatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
