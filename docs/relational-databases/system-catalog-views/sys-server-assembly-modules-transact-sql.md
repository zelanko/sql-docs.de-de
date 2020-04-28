---
title: sys. server_assembly_modules (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 714d0ca36bc48206ee7431454a61b51d2c31afb0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68060560"
---
# <a name="sysserver_assembly_modules-transact-sql"></a>sys.server_assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes Assemblymodul der Trigger auf Serverebene des Typs TA (CLR-Assemblytrigger). Diese Sicht ordnet die Assemblytrigger der zugrunde liegenden CLR-Implementierung zu. Sie können diese Beziehung mit **sys. server_triggers**verknüpfen. Die Assembly muss in die **Master** -Datenbank geladen werden. Das Tupel (object_id) ist der Schlüssel für die Beziehung.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Dies ist ein FOREIGN KEY-Rückverweis auf das Objekt, für das dieses Assemblymodul definiert wird.|  
|**assembly_id**|**int**|ID der Assembly, aus der dieses Modul erstellt wurde. Die Assembly muss in die master-Datenbank geladen werden.|  
|**assembly_class**|**sysname**|Name der Klasse innerhalb der Assembly, die dieses Modul definiert.|  
|**assembly_method**|**sysname**|Name der Methode innerhalb der Klasse, die dieses Modul definiert. Ist für Aggregatfunktionen (AF) gleich NULL.|  
|**execute_as_principal_id**|**int**|ID des Serverprinzipals, der mit EXECUTE AS verwendet wird.<br /><br /> NULL als Standardwert oder bei Verwendung von EXECUTE AS CALLER.<br /><br /> ID des angegebenen Prinzipals, wenn EXECUTE AS Self \<EXECUTE AS Principal>.<br /><br /> -2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
