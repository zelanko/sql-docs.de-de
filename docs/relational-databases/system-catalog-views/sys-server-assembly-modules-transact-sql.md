---
title: server_assembly_modules (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_assembly_modules_TSQL
- sys.server_assembly_modules
- server_assembly_modules
- sys.server_assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_assembly_modules catalog view
ms.assetid: af799e38-2d16-49b2-bcf5-6f9199af899e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a257f63328fe0abcf121b82b619bc58b70b7c6f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711701"
---
# <a name="sysserverassemblymodules-transact-sql"></a>sys.server_assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes Assemblymodul der Trigger auf Serverebene des Typs TA (CLR-Assemblytrigger). Diese Sicht ordnet die Assemblytrigger der zugrunde liegenden CLR-Implementierung zu. Sie können diese Beziehung mit **sys.server_triggers**verknüpfen. Die Assembly muss in die **master** -Datenbank geladen werden. Das Tupel (object_id) ist der Schlüssel für die Beziehung.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Dies ist ein FOREIGN KEY-Rückverweis auf das Objekt, für das dieses Assemblymodul definiert wird.|  
|**assembly_id**|**int**|ID der Assembly, aus der dieses Modul erstellt wurde. Die Assembly muss in die master-Datenbank geladen werden.|  
|**assembly_class**|**sysname**|Name der Klasse innerhalb der Assembly, die dieses Modul definiert.|  
|**assembly_method**|**sysname**|Name der Methode innerhalb der Klasse, die dieses Modul definiert. Ist für Aggregatfunktionen (AF) gleich NULL.|  
|**execute_as_principal_id**|**int**|ID des Serverprinzipals, der mit EXECUTE AS verwendet wird.<br /><br /> NULL als Standardwert oder bei Verwendung von EXECUTE AS CALLER.<br /><br /> ID des angegebenen Prinzipals bei EXECUTE AS SELF ausführen AS \<principal >.<br /><br /> -2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Objekt-Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
