---
description: 'Tabellen von Datenschichtanwendung: sysdac_instances_internal'
title: sysdac_instances_internal (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdac_instances_internal_TSQL
- sysdac_instances_internal
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_instances_internal
ms.assetid: d2d52cc4-3463-431a-b779-6fbfdeee1dfc
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7ccda567989211074c8d151de7f2b3936ccd2b69
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544610"
---
# <a name="data-tier-application-tables---sysdac_instances_internal"></a>Tabellen von Datenschichtanwendung: sysdac_instances_internal
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt eine Zeile für jede Instanz der Datenebenenanwendung (DAC) an, die für eine [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz bereitgestellt wird. Diese Tabelle wird im dbo-Schema in der msdb-Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|instance_id|**uniqueidentifier**|Der Bezeichner der DAC-Instanz.|  
|instance_name|**sysname**|Der Name der DAC-Instanz, die bei der Bereitstellung der Instanz angegeben wurde.|  
|type_name|**sysname**|Der Name der DAC, die bei der Erstellung des DAC-Pakets angegeben wurde.|  
|type_version|**nvarchar (64)**|Die Version der DAC, die bei der Erstellung des DAC-Pakets angegeben wurde.|  
|description|**nvarchar(4000)**|Eine Beschreibung der DAC, die bei der Erstellung des DAC-Pakets geschrieben wurde.|  
|type_stream|**varbinary(max)**|Ein Bitdatenstrom, der die codierte Darstellung der in der DAC enthaltenen logischen Objekte, z. B. Tabellen und Sichten, enthält.|  
|date_created|**datetime**|Datum und Uhrzeit der Erstellung der DAC-Instanz.|  
|created_by|**sysname**|Der Anmeldename, unter dem die DAC-Instanz erstellt wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Der schreibgeschützte Zugriff auf diese Ansicht ist für alle Benutzer verfügbar, die über Berechtigungen zum Herstellen einer Verbindung mit der Master-Datenbank verfügen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenebenenanwendungen](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)  
  
  
