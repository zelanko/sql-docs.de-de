---
title: MSreplication_objects (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_objects
- MSreplication_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_objects system table
ms.assetid: 08f9710d-976d-448e-bead-ac9835e87bc5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 57a4c20f6aac12f1671b88dc04b0366290abe127
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881494"
---
# <a name="msreplication_objects-transact-sql"></a>MSreplication_objects (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSreplication_objects** Tabelle enthält eine Zeile für jedes Objekt, das der Replikation in der Abonnenten Datenbank zugeordnet ist. Diese Tabelle wird in der Abonnement Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**ung**|**sysname**|Der Name der Veröffentlichung.|  
|**object_name**|**sysname**|Der Name des Objekts.|  
|**object_type**|**char(2)**|Der Objekttyp:<br /><br /> **u** = Tabelle.<br /><br /> **t** =-auslöst.<br /><br /> **p** = gespeicherte Prozedur.|  
|**Artikel**|**sysname**|Der Name des Artikels, dem das Objekt zugeordnet ist|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
