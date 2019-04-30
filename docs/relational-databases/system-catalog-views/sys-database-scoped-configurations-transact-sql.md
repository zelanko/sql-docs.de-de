---
title: Sys. database_scoped_configurations (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: af6c2996877f4ab7d8a2305c4f6fe4b30a0127cc
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473738"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Konfiguration. 
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|Die ID der Konfigurationsoption.|  
|**name**|**nvarchar(60)**|Der Name der Konfigurationsoption. Weitere Informationen zu den möglichen Konfigurationen, finden Sie unter [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**value**|**sqlvariant**|Der Wert für diese Konfigurationsoption für das primäre Replikat.|  
|**value_for_secondary**|**sqlvariant**|Der Wert für diese Konfigurationsoption für die sekundären Replikate.|  
|**is_value_default**|**bit** |Gibt an, ob der festgelegte Wert der Standardwert ist.|
  
##  <a name="Permissions"></a> Berechtigungen  
Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="remarks"></a>Hinweise  
Wenn NULL zurückgegeben wird, als Wert für **Value_for_secondary**, dies bedeutet, dass die sekundäre Datenbank zur primären festgelegt ist.  
 
Die datenbankweit gültigen Konfigurationseinstellungen werden mit der Datenbank übertragen. Dies bedeutet, dass die vorhandenen Konfigurationseinstellungen bei der Wiederherstellung oder dem Anfügen einer bestimmten Datenbank erhalten bleiben.
  
## <a name="see-also"></a>Siehe auch  
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
