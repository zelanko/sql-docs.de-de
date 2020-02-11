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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 61e1329fe35ae032b5d35f94dd2e1ce5e8d08d38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130519"
---
# <a name="sysarticlecolumns-transact-sql"></a>sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **sysarticlecolumns** -Tabelle enthält eine Zeile für jede Tabellenspalte, die in einer Momentaufnahme-oder Transaktions Veröffentlichung veröffentlicht wird, und ordnet jede Spalte dem Artikel zu. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifiziert einen Artikel.|  
|**ColId**|**smallint**|Identifiziert eine Spalte in einem Artikel.|  
|**is_udt**|**bit**|Zeigt an, ob die Spalte dem benutzerdefinierten Datentyp (UDT) zugehört. Der Wert **1** gibt eine UDT-Spalte an.|  
|**is_xml**|**bit**|Gibt an, ob die Spalte eine **XML** -Spalte ist. Der Wert **1** gibt eine XML-Spalte an.|  
|**is_max**|**bit**|Gibt an, ob die Spalte eine Spalte mit einem großen Wert ( **varchar (max)**, **nvarchar (max)** und **varbinary (max)** ist. Der Wert **1** gibt eine Spalte mit großen Werten an.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
