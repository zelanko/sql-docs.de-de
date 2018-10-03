---
title: Sys.syspermissions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syspermissions_TSQL
- syspermissions_TSQL
- sys.syspermissions
- syspermissions
dev_langs:
- TSQL
helpviewer_keywords:
- syspermissions system table
- sys.syspermissions compatibility view
ms.assetid: ba9a9a88-55d2-41a7-b09b-342e8b9a54c5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 20ac49b8da959732c54e912898b375c9175d546d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822568"
---
# <a name="syssyspermissions-transact-sql"></a>sys.syspermissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält Informationen zu Berechtigungen, die Benutzern, Gruppen und Rollen in der Datenbank erteilt oder verweigert werden.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID des Objekts für Objektberechtigungen.<br /><br /> 0 = Anweisungsberechtigungen.|  
|**Empfänger**|**smallint**|ID des Benutzers, der Gruppe oder der Rolle, auf den bzw. die sich die Berechtigung auswirkt.|  
|**Berechtigende (Grantor)**|**smallint**|ID des Benutzers, der Gruppe oder der Rolle, der bzw. die die Berechtigung erteilt oder verweigert hat.|  
|**actadd**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**actmod**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**seladd**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**selmod**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**updadd**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**updmod**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**refadd**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**refmod**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Siehe auch  
 [Zuordnen von Systemtabellen zu Systemsichten &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
