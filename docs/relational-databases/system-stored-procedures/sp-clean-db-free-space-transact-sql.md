---
description: sp_clean_db_free_space (Transact-SQL)
title: sp_clean_db_free_space (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_clean_db_free_space_TSQL
- sp_clean_db_free_space
dev_langs:
- TSQL
helpviewer_keywords:
- sp_clean_db_free_space
- ghost records
ms.assetid: faa96f7e-be92-47b1-8bc5-4dbba5331655
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 508ead96133a178e5abbe939defcefa4d6c33492
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546259"
---
# <a name="sp_clean_db_free_space-transact-sql"></a>sp_clean_db_free_space (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt restliche aufgrund der Datenänderungsroutinen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Datenbankseiten belassene Informationen. sp_clean_db_free_space bereinigt alle Seiten in allen Dateien der Datenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql 
sp_clean_db_free_space   
  [ @dbname = ] 'database_name'   
  [ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>Argumente  
 @dbname = '*database_name*'  
 Der Name der zu bereinigenden Datenbank. *dbname* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
 @cleaning_delay = '*delay_in_seconds*'  
 Gibt das Intervall zwischen dem Bereinigen von Seiten an. Hierdurch werden die Auswirkungen auf das E/A-System verringert. *delay_in_seconds* ist vom Datentyp **int** und hat den Standardwert 0.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Löschvorgänge aus einer Tabelle oder aus Aktualisierungs Vorgängen, die bewirken, dass eine Zeile verschoben wird, können auf einer Seite sofort Speicherplatz freigeben, indem Verweise auf die Zeile entfernt werden. Unter bestimmten Umständen kann die Zeile jedoch als inaktiver Datensatz (ghost record) weiter physisch auf der Datenseite vorhanden sein. Inaktive Datensätze werden regelmäßig durch einen im Hintergrund ausgeführten Prozess entfernt. Diese verbleibenden Daten werden von nicht [!INCLUDE[ssDE](../../includes/ssde-md.md)] als Antwort auf Abfragen zurückgegeben. In Umgebungen, in denen die physische Sicherheit der Daten-oder Sicherungsdateien gefährdet ist, können Sie jedoch verwenden, `sp_clean_db_free_space` um diese inaktiven Datensätze zu bereinigen. Verwenden Sie [sp_clean_db_file_free_space (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md), um diesen Vorgang pro Datenbankdatei auszuführen. 
  
 Die zum Ausführen von sp_clean_db_free_space erforderliche Dauer hängt von der Größe der Datei, dem freien Speicherplatz und der Kapazität des Datenträgers ab. Da das Ausführen von die e `sp_clean_db_free_space` /a-Aktivität erheblich beeinträchtigen kann, empfiehlt es sich, dieses Verfahren außerhalb der normalen Betriebsstunden auszuführen.  
  
 Bevor Sie Ausführen `sp_clean_db_free_space` , wird empfohlen, eine vollständige Datenbanksicherung zu erstellen.  
  
 Mit der zugehörigen [sp_clean_db_file_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md) gespeicherten Prozedur kann eine einzelne Datei bereinigt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der `db_owner` Daten Bank Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Restinformationen aus der `AdventureWorks2012`-Datenbank gelöscht.  
  
```sql  
USE master;  
GO  
EXEC sp_clean_db_free_space @dbname = N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Prozess Leit Faden für inaktive Cleanup](../ghost-record-cleanup-process-guide.md)    
 [sp_clean_db_file_free_space (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md)
  
  
