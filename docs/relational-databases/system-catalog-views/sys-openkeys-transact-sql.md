---
title: Sys.openkeys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- openkeys_TSQL
- sys.openkeys_TSQL
- openkeys
- sys.openkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.openkeys catalog view
ms.assetid: 719a1259-2398-4fcb-ba05-aeabba7aec21
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1b4f88ac93671485c6398b537946166a3200e952
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43058992"
---
# <a name="sysopenkeys-transact-sql"></a>sys.openkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Diese Katalogsicht gibt Informationen zu den Verschlüsselungsschlüsseln zurück, die in der aktuellen Sitzung geöffnet sind.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Die ID der Datenbank, die den Schlüssel enthält.|  
|**database_name**|**sysname**|Der Name der Datenbank, die den Schlüssel enthält.|  
|**key_id**|**int**|ID des Schlüssels. Die ID ist innerhalb der Datenbank eindeutig.|  
|**key_name**|**sysname**|Name des Schlüssels. Ist innerhalb der Datenbank eindeutig.|  
|**key_guid**|**varbinary**|Die GUID des Schlüssels. Ist innerhalb der Datenbank eindeutig.|  
|**opened_date**|**datetime**|Datum und Uhrzeit, zu der der Schlüssel geöffnet wurde.|  
|**status**|**int**|1, wenn der Schlüssel in den Metadaten gültig ist. 0, wenn der Schlüssel nicht in den Metadaten vorhanden ist.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)  
  
  
