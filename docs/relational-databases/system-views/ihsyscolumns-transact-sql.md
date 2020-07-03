---
title: IHsyscolumns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38522539230fd35aca058f9a26b53a3f4baa682b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889178"
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **ihsyscolenns** -Sicht macht Spalten Informationen für Artikel verfügbar, die von einem nicht-SQL Server-Verleger veröffentlicht wurden. Diese Sicht wird in der Verteil Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Spalte oder des Prozedurparameters.|  
|**id**|**int**|Die Objekt-ID der Tabelle, zu der diese Spalte gehört, oder die ID der gespeicherten Prozedur, der dieser Parameter zugeordnet ist.|  
|**xtype**|**tinyint**|Der physische Speichertyp aus [sys.sysTypen &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|Die ID des erweiterten benutzerdefinierten Datentyps.|  
|**length**|**bigint**|Die maximale physische Speicher Länge von [sys.sysTypen &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**int**|Die Spalten- oder Parameter-ID.|  
|**xoffset**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bleiben**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|Die ID des Standards für diese Spalte.|  
|**-**|**int**|Die ID der Regel oder der CHECK-Einschränkung für diese Spalte.|  
|**Zahl**|**int**|Die Nummer der unter Prozedur, wenn die Prozedur gruppiert wird (**0** für nicht Prozedur Einträge).|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**int**|Der Offset in die Zeile, in der diese Spalte angezeigt wird.|  
|**collationid**|**int**|Die ID der Spaltensortierung. Ist für nicht zeichenbasierte Spalten NULL.|  
|**language**|**int**|Die Sprachen-ID für die Spalte.|  
|**status**|**int**|Das Bitmuster, das zum Beschreiben einer Eigenschaft der Spalte oder des Parameters verwendet wird:<br /><br /> **0x08** = die Spalte lässt NULL-Werte zu.<br /><br /> **0x10** = ANSI-Auffüll Zeichen war wirksam, als **varchar** -oder **varbinary** -Spalten hinzugefügt wurden. Nachfolgende Leerzeichen werden bei **varchar** -Spalten beibehalten, nachfolgende Nullen werden bei **varbinary** -Spalten beibehalten.<br /><br /> **0x40** = der Parameter ist ein Output-Parameter.<br /><br /> **0x80** = die Spalte ist eine Identitäts Spalte.|  
|**type**|**int**|Der physische Speichertyp aus [sys.sysTypen &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**usertype**|**tinyint**|Die ID des benutzerdefinierten Datentyps aus [sys.sysTypen &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**printfmt**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**int**|Der Genauigkeitsgrad für diese Spalte.|  
|**scale**|**int**|Die Dezimalstellen in dieser Spalte.|  
|**IsComputed**|**int**|Das Flag, das anzeigt, ob die Spalte berechnet ist:<br /><br /> **0** = nicht berechnet.<br /><br /> **1** = berechnet.|  
|**isoutparam**|**int**|Gibt an, ob der Prozedurparameter ein Ausgabeparameter ist.<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**IsNullable**|**int**|Gibt an, ob die Spalte NULL-Werte zulässt.<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**Sortierung**|**int**|Der Name der Sortierung der Spalte. Ist für nicht zeichenbasierte Spalten NULL.|  
|**tdscollation**|**int**|Der Name der Sortierung der Spalte, wenn diese in einem Tabular Data Stream (TDS) zurückgegeben wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Replikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
