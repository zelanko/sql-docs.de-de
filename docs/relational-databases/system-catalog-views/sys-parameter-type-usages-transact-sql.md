---
description: sys.parameter_type_usages (Transact-SQL)
title: sys. parameter_type_usages (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.parameter_type_usages
- sys.parameter_type_usages_TSQL
- parameter_type_usages_TSQL
- parameter_type_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.parameter_type_usages catalog view
ms.assetid: af0e167b-bffb-4525-84ec-3607f9268d3d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f20fbf0face7b4b99c7c2d5b5920139e68670052
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542509"
---
# <a name="sysparameter_type_usages-transact-sql"></a>sys.parameter_type_usages (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeile für jeden benutzerdefinierten Parametertyp zurück.  
  
> [!NOTE]  
>  Diese Sicht gibt nicht die Zeilen für Parameter von nummerierten Prozeduren zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID des Objekts, zu dem dieser Parameter gehört.|  
|**parameter_id**|**int**|ID des Parameters. Ist eindeutig innerhalb des Objekts.|  
|**user_type_id**|**int**|ID des benutzerdefinierten Datentyps.<br /><br /> Stellen Sie einen Join mit der [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) -Katalogsicht für diese Spalte her, um den Namen des Typs zurückzugeben.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Skalare Typenkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
