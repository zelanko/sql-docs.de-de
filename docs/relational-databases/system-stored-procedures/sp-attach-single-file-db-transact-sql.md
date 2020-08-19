---
description: sp_attach_single_file_db (Transact-SQL)
title: sp_attach_single_file_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_attach_single_file_db
- sp_attach_single_file_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_single_file_db
ms.assetid: 13bd1044-9497-4293-8390-1f12e6b8e952
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bbaa3da6832ba3a7ec5bad2fc8eb2988f9984470
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447370"
---
# <a name="sp_attach_single_file_db-transact-sql"></a>sp_attach_single_file_db (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Fügt eine Datenbank mit nur einer Datendatei an den aktuellen Server an. **sp_attach_single_file_db** kann nicht mit mehreren Datendateien verwendet werden.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Es empfiehlt sich, stattdessen CREATE DATABASE *database_name* for Attach zu verwenden. Weitere Informationen finden Sie unter [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md). Verwenden Sie diese Prozedur nicht für eine replizierte Datenbank.  
  
> [!IMPORTANT]  
>  Das Anfügen oder Wiederherstellen von Datenbanken aus unbekannten oder nicht vertrauenswürdigen Quellen wird nicht empfohlen. Solche Datenbanken können bösartigen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code ausführt oder Fehler verursacht, indem er das Schema oder die physische Datenbankstruktur ändert. Bevor Sie eine Datenbank aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, führen Sie auf einem Nichtproduktionsserver [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) für die Datenbank aus. Überprüfen Sie außerdem den Code in der Datenbank, z.B. gespeicherte Prozeduren oder anderen benutzerdefinierten Code.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_attach_single_file_db [ @dbname= ] 'dbname'  
    , [ @physname= ] 'physical_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'dbname'` Der Name der Datenbank, die an den Server angefügt werden soll. Der Name muss eindeutig sein. *dbname* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @physname = ] 'physical_name'` Der physische Name der Datenbankdatei, einschließlich des Pfads. *physical_name* ist vom Datentyp **nvarchar (260)** und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieses Argument entspricht dem FILENAME-Parameter der CREATE DATABASE-Anweisung. Weitere Informationen finden Sie unter [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
 Wenn Sie eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbank mit Volltextkatalogdateien an eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Serverinstanz anfügen, werden die Katalogdateien von ihrem vorherigen Speicherort aus zusammen mit den anderen Datenbankdateien angefügt. Dies entspricht der Vorgehensweise in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Weitere Informationen finden Sie unter [Upgrade der Volltextsuche](../../relational-databases/search/upgrade-full-text-search.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie **sp_attach_single_file_db** nur für Datenbanken, die zuvor vom Server getrennt wurden, indem Sie einen expliziten **sp_detach_db** Vorgang oder für kopierte Datenbanken verwenden.  
  
 **sp_attach_single_file_db** funktioniert nur in Datenbanken, die über eine einzelne Protokolldatei verfügen. Wenn **sp_attach_single_file_db** die Datenbank an den Server anfügt, wird eine neue Protokolldatei erstellt. Wenn die Datenbank schreibgeschützt ist, wird die Protokolldatei an ihrem bisherigen Speicherort erstellt.  
  
> [!NOTE]  
>  Eine Datenbankmomentaufnahme kann nicht getrennt oder angefügt werden.  
  
 Verwenden Sie diese Prozedur nicht für eine replizierte Datenbank.  
  
## <a name="permissions"></a>Berechtigungen  
 Informationen dazu, wie Berechtigungen verarbeitet werden, wenn eine Datenbank angefügt wird, finden Sie unter [Create Database &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] getrennt und eine Datei aus [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] an den aktuellen Server angefügt.  
  
```  
USE master;  
GO  
EXEC sp_detach_db @dbname = 'AdventureWorks2012';  
EXEC sp_attach_single_file_db @dbname = 'AdventureWorks2012',   
    @physname =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_Data.mdf';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
