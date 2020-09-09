---
description: sys.sp_xtp_merge_checkpoint_files (Transact-SQL)
title: sys. sp_xtp_merge_checkpoint_files (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/28/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_merge_checkpoint_files_TSQL
- sys.sp_xtp_merge_checkpoint_files
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_merge_checkpoint_files
ms.assetid: da04df2a-f7a1-41e7-a1ef-2d5d68919892
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9bd8cf3735ecc240a0d99929fc0ef1c40d931887
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541051"
---
# <a name="syssp_xtp_merge_checkpoint_files-transact-sql"></a>sys.sp_xtp_merge_checkpoint_files (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  **sys. sp_xtp_merge_checkpoint_files** führt alle Daten-und Änderungs Dateien im angegebenen Transaktions Bereich zusammen.  
  
 Weitere Informationen finden Sie unter [Erstellen und Verwalten von Speicher für Speicher optimierte Objekte](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
||  
|-|  
|**Hinweis**: Diese gespeicherte Prozedur ist in veraltet [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] . Er wird nicht mehr benötigt und kann nicht verwendet werden, da er gestartet wird [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] .|  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_xtp_merge_checkpoint_files database_name, @transaction_lower_bound, @transaction_upper_bound  
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 *database_name*  
 Der Name der Datenbank, für die die Zusammenführung aufgerufen werden soll. Wenn die Datenbank keine Tabellen im Arbeitsspeicher aufweist, gibt diese Prozedur einen Benutzerfehler zurück. Falls die Datenbank offline ist, wird ein Fehler zurückgegeben.  
  
 *lower_bound_Tid*  
 Die (BIGINT) untere Grenze von Transaktionen für eine Datendatei, wie in [sys. dm_db_xtp_checkpoint_files &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md) entsprechend der Start Prüf Punkt Datei der Zusammenführung angezeigt. Bei einem ungültigen transactionId-Wert wird ein Fehler generiert.  
  
 *upper_bound_Tid*  
 Die obere Grenze (BIGINT) von Transaktionen für eine Datendatei, wie in [sys. dm_db_xtp_checkpoint_files &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md)gezeigt. Bei einem ungültigen transactionId-Wert wird ein Fehler generiert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="cursors-returned"></a>Zurückgegebene Cursor  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die feste Serverrolle sysadmin und die feste Datenbankrolle db_owner.  
  
## <a name="remarks"></a>Hinweise  
 Führt alle Daten und Änderungsdateien innerhalb des gültigen Bereichs zusammen, um eine einzelne Daten- und Änderungsdatei zu erstellen. Die Mergerichtlinie wird von dieser Prozedur nicht berücksichtigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
