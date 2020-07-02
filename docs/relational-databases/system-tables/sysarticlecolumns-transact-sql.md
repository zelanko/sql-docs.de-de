---
title: sysarticlecolumns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns system table
ms.assetid: 55918592-e05d-43b6-843b-7e4d82fa6275
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3c295da10074efbd6e4ee1b014b754ac8622ba73
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753849"
---
# <a name="sysarticlecolumns-transact-sql"></a>sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Die **sysarticlecolumns** -Tabelle enthält eine Zeile für jede Tabellenspalte, die in einer Momentaufnahme-oder Transaktions Veröffentlichung veröffentlicht wird, und ordnet jede Spalte dem Artikel zu. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifiziert einen Artikel.|  
|**colid**|**smallint**|Identifiziert eine Spalte in einem Artikel.|  
|**is_udt**|**bit**|Zeigt an, ob die Spalte dem benutzerdefinierten Datentyp (UDT) zugehört. Der Wert **1** gibt eine UDT-Spalte an.|  
|**is_xml**|**bit**|Gibt an, ob die Spalte eine **XML** -Spalte ist. Der Wert **1** gibt eine XML-Spalte an.|  
|**is_max**|**bit**|Gibt an, ob die Spalte eine Spalte mit einem großen Wert ( **varchar (max)**, **nvarchar (max)** und **varbinary (max)** ist. Der Wert **1** gibt eine Spalte mit großen Werten an.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
