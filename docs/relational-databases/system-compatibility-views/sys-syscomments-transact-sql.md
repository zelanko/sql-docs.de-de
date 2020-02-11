---
title: sys. syscomments (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscomments_TSQL
- syscomments
- syscomments_TSQL
- sys.syscomments
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syscomments compatibility view
- syscomments system table
ms.assetid: 767dd410-6bc9-4c4a-ab0f-6d2cf6163426
author: rothja
ms.author: jroth
ms.openlocfilehash: 183fa2fc1a674ec1cc987c265f5a0d4c399e27cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68010750"
---
# <a name="syssyscomments-transact-sql"></a>sys.syscomments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die Tabelle enthält Einträge für alle Sichten, Regeln, Standards, Trigger, CHECK-Einschränkungen, DEFAULT-Einschränkungen und gespeicherten Prozeduren innerhalb der Datenbank. Die **Text** -Spalte enthält die ursprünglichen SQL-Definitions Anweisungen.  
  
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Stattdessen wird die Verwendung von sys.sql_modules empfohlen. Weitere Informationen finden Sie unter [sys. sql_modules &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Name**|**int**|ID des Objekts, auf das sich der Text bezieht.|  
|**Zahl**|**smallint**|Nummer innerhalb der Prozedurgruppierung, wenn eine Gruppierung vorliegt.<br /><br /> 0 = Einträge sind keine Prozeduren.|  
|**ColId**|**smallint**|Zeilensequenznummer für Objektdefinitionen, die 4.000 Zeichen überschreiten.|  
|**Stands**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**CTEXT**|**varbinary (8000)**|Die Rohbytes der SQL-Definitionsanweisung.|  
|**TextType**|**smallint**|0 = Vom Benutzer anzugebender Kommentar<br /><br /> 1 = Vom System anzugebender Kommentar<br /><br /> 4 = Verschlüsselter Kommentar|  
|**Kurse**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**.**|**bit**|Gibt an, ob die Prozedurdefinition verborgen ist.<br /><br /> 0 = Nicht verborgen<br /><br /> 1 = Verborgen<br /><br /> ** \* Wichtig \* \* ** Verwenden Sie CREATE PROCEDURE mit dem Schlüsselwort Encryption, um Definitionen gespeicherter Prozeduren zu verbergen.|  
|**komprimierte**|**bit**|Es wird immer 0 zurückgegeben. Zeigt an, ob die Prozedur komprimiert ist.|  
|**text**|**nvarchar(4000)**|Tatsächlicher Text der SQL-Definitionsanweisung.<br /><br /> Die Semantik des decodierten Ausdrucks entspricht dem ursprünglichen Text. Es gibt jedoch keine syntaktische Garantie. Leerzeichen werden beispielsweise aus dem decodierten Ausdruck entfernt.<br /><br /> Mit [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]dieser kompatiblen Ansicht werden Informationen aus aktuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Strukturen abgerufen, und es können mehr Zeichen als die **nvarchar (4000)** -Definition zurückgegeben werden. **sp_help** gibt **nvarchar (4000)** als Datentyp der Text Spalte zurück. Bei der Arbeit mit **syscomments** sollten Sie **nvarchar (max)** verwenden. Verwenden Sie für neue Entwicklungsaufgaben nicht **syscomments**.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitäts Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
