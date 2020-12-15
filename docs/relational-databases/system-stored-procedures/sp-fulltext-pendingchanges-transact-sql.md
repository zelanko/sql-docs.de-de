---
description: sp_fulltext_pendingchanges (Transact-SQL)
title: sp_fulltext_pendingchanges (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_pendingchanges_TSQL
- sp_fulltext_pendingchanges
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_pendingchanges
ms.assetid: fee042fe-4781-4a33-a01b-d98fb5629f1b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fa2b81ce294183b005aa59de141d78945f6b3f04
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97427425"
---
# <a name="sp_fulltext_pendingchanges-transact-sql"></a>sp_fulltext_pendingchanges (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt nicht verarbeitete Änderungen, z. B. ausstehende Einfügungs-, Update- und Löschvorgänge, für eine angegebene Tabelle zurück, die die Änderungsnachverfolgung verwendet.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_fulltext_pendingchanges table_id  
```  
  
## <a name="arguments"></a>Argumente  
 *table_id*  
 ID der Tabelle. Falls die Tabelle nicht volltextindiziert ist oder die Änderungsnachverfolgung für die Tabelle nicht aktiviert ist, wird ein Fehler zurückgegeben.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**Schlüssel**|*|Der Wert des Volltextschlüssels aus der angegebenen Tabelle.|  
|**DocId**|**bigint**|Eine interne Dokumentbezeichnerspalte (DocId), die dem Schlüsselwert entspricht.|  
|**Status**|**int**|0 = Zeile wird aus dem Volltextindex entfernt.<br /><br /> 1 = Zeile ist volltextindiziert.<br /><br /> 2 = Zeile ist auf dem aktuellen Stand.<br /><br /> -1 = Zeile befindet sich in einem Übergangsstatus (Batch, ohne Commit) oder in einem Fehlerzustand.|  
|**DocState**|**tinyint**|Eine Rohsicherung der internen DocId-Zuordnungsstatusspalte.|  
  
 <sup>* Der Datentyp für Key ist identisch mit dem Datentyp der Volltextschlüsselspalte in der Basistabelle.</sup>  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="remarks"></a>Hinweise  
 Falls keine Änderungen zur Verarbeitung vorhanden sind, wird ein leeres Rowset zurückgegeben.  
  
 Volltextsuche-Abfragen geben keine Zeilen mit einem **Status** -Wert von 0 zurück. Das liegt daran, dass die Zeile aus der Basistabelle gelöscht wurde und darauf wartet, aus dem Volltextindex gelöscht zu werden.  
  
 Verwenden Sie die **TableFullTextPendingChanges** -Eigenschaft der OBJECTPROPERTYEX-Funktion, um festzustellen, wie viele Änderungen für eine bestimmte Tabelle ausstehen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)  
  
  
