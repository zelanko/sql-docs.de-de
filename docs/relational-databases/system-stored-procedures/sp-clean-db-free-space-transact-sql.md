---
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ea9690011e963e6374b562f37d64573546a170c3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85871121"
---
# <a name="sp_clean_db_free_space-transact-sql"></a>sp_clean_db_free_space (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt restliche aufgrund der Datenänderungsroutinen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Datenbankseiten belassene Informationen. sp_clean_db_free_space bereinigt alle Seiten in allen Dateien der Datenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_clean_db_free_space   
[ @dbname ] = 'database_name'   
[ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @dbname =] '*database_name*'  
 Der Name der zu bereinigenden Datenbank. *dbname* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
 [ @cleaning_delay =] '*delay_in_seconds*'  
 Gibt das Intervall zwischen dem Bereinigen von Seiten an. Hierdurch werden die Auswirkungen auf das E/A-System verringert. *delay_in_seconds* ist vom Datentyp **int** und hat den Standardwert 0.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Löschvorgänge aus einer Tabelle oder aus Aktualisierungs Vorgängen, die bewirken, dass eine Zeile verschoben wird, können auf einer Seite sofort Speicherplatz freigeben, indem Verweise auf die Zeile entfernt werden. Unter bestimmten Umständen kann die Zeile jedoch als inaktiver Datensatz (ghost record) weiter physisch auf der Datenseite vorhanden sein. Inaktive Datensätze werden regelmäßig durch einen im Hintergrund ausgeführten Prozess entfernt. Diese verbleibenden Daten werden von nicht [!INCLUDE[ssDE](../../includes/ssde-md.md)] als Antwort auf Abfragen zurückgegeben. In Umgebungen, in denen die physische Sicherheit der Daten- oder Sicherungsdateien gefährdet ist, können Sie jedoch die inaktiven Datensätze mithilfe von sp_clean_db_free_space löschen.  
  
 Die zum Ausführen von sp_clean_db_free_space erforderliche Dauer hängt von der Größe der Datei, dem freien Speicherplatz und der Kapazität des Datenträgers ab. Weil sich das Ausführen von sp_clean_db_free_space erheblich auf die E/A-Aktivität auswirken kann, sollten Sie diese Prozedur außerhalb der normalen Betriebszeit ausführen.  
  
 Vor dem Ausführen von sp_clean_db_free_space sollten Sie eine vollständige Datenbanksicherung durchführen.  
  
 Mit der zugehörigen [sp_clean_db_file_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md) gespeicherten Prozedur kann eine einzelne Datei bereinigt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Datenbankrolle db_owner.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Restinformationen aus der `AdventureWorks2012`-Datenbank gelöscht.  
  
```  
USE master;  
GO  
EXEC sp_clean_db_free_space   
@dbname = N'AdventureWorks2012' ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)
 <br>[Prozess Leit Faden für inaktive Cleanup](../ghost-record-cleanup-process-guide.md) 
  
  
