---
title: Sp_helplanguage (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 29f366517986620444e018a5348e623aa541b00a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560630"
---
# <a name="sphelplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu einer bestimmten alternativen Sprache oder zu allen Sprachen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@language=** ] **"***Sprache***"**  
 Der Name der alternativen Sprache, für die Informationen angezeigt werden sollen. *language* ist vom Datentyp **sysname**und hat den Standardwert NULL. Wenn *Sprache* wird angegeben, werden Informationen zu der angegebenen Sprache zurückgegeben. Wenn Language nicht angegeben ist, Informationen zu allen Sprachen in der **sys.syslanguages** -kompatibilitätssicht zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|Sprachen-ID|  
|**DateFormat-Einstellung**|**NCHAR(3)**|Datumsformat.|  
|**DATEFIRST**|**tinyint**|Erster Tag der Woche: 1 für Montag, 2 für Dienstag usw., bis 7 für Sonntag.|  
|**Aktualisieren**|**int**|Version des letzten Upgrades von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für diese Sprache.|  
|**name**|**sysname**|Name der Sprache.|  
|**alias**|**sysname**|Alternativer Name der Sprache|  
|**Monate**|**nvarchar(372)**|Monatsnamen|  
|**ShortMonths**|**nvarchar(132)**|Kurznamen für die Monate|  
|**Tage**|**nvarchar(217)**|Tagesnamen|  
|**LCID**|**int**|Windows-Gebietsschema-ID für die Sprache.|  
|**msglangid**|**smallint**|ID der Meldungsgruppe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-information-about-a-single-language"></a>A. Zurückgeben von Informationen zu einer einzelnen Sprache  
 Das folgende Beispiel zeigt Informationen zur alternativen Sprache `French` an.  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. Zurückgeben von Informationen zu allen Sprachen  
 Das folgende Beispiel zeigt Informationen zu allen installierten alternativen Sprachen an.  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
