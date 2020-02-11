---
title: sp_create_removable (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_create_removable
- sp_create_removable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_create_removable
ms.assetid: 06e36ae5-f70d-4a26-9a7f-ee4b9360b355
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6f842b96a9b179548688a4c655a566087ba1ebf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108623"
---
# <a name="sp_create_removable-transact-sql"></a>sp_create_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt eine Datenbank für austauschbare Medien. Erstellt drei oder mehr Dateien (eine für die Systemkatalogtabellen, eine für das Transaktionsprotokoll und eine oder mehrere für die Datentabellen) und platziert die Datenbank in diesen Dateien.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Es wird empfohlen, stattdessen [Create Database](../../t-sql/statements/create-database-sql-server-transact-sql.md) zu verwenden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_create_removable   
   [ @dbname = ] 'dbname',   
   [ @syslogical= ] 'syslogical',   
   [ @sysphysical = ] 'sysphysical',   
   [ @syssize = ] syssize,   
   [ @loglogical = ] 'loglogical',   
   [ @logphysical = ] 'logphysical',   
   [ @logsize = ] logsize,   
   [ @datalogical1 = ] 'datalogical1',   
   [ @dataphysical1 = ] 'dataphysical1',   
   [ @datasize1 = ] datasize1 ,   
   [ @datalogical16 = ] 'datalogical16',   
   [ @dataphysical16 = ] 'dataphysical16',   
   [ @datasize16 = ] datasize16 ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'dbname'`Der Name der Datenbank, die für die Verwendung auf einem Wechsel Datenträger erstellt werden soll. *dbname* ist vom **Datentyp vom Datentyp sysname**.  
  
`[ @syslogical = ] 'syslogical'`Der logische Name der Datei, die die System Katalog Tabellen enthält. *syslogisch* ist vom **Datentyp vom Datentyp sysname**.  
  
`[ @sysphysical = ] 'sysphysical'`Der physische Name. Enthält einen vollqualifizierten Pfad der Datei, die die Systemkatalogtabellen enthält. *sysphysical* ist vom Datentyp **nvarchar (260)**.  
  
`[ @syssize = ] syssize`Die Größe der Datei in Megabyte, die die System Katalog Tabellen enthält. *syssize* ist vom Datentyp **int**. Die minimale *syssize* ist 1.  
  
`[ @loglogical = ] 'loglogical'`Der logische Name der Datei, die das Transaktionsprotokoll enthält. *loglogisch* ist vom **Datentyp vom Datentyp sysname**.  
  
`[ @logphysical = ] 'logphysical'`Der physische Name. Enthält einen vollqualifizierten Pfad der Datei, die die Transaktionsprotokolltabellen enthält. *logphysical* ist vom Datentyp **nvarchar (260)**.  
  
`[ @logsize = ] logsize`Die Größe der Datei in Megabyte, die das Transaktionsprotokoll enthält. *logsize* ist vom Datentyp **int**. Die minimale *logsize* ist 1.  
  
`[ @datalogical1 = ] 'datalogical'`Der logische Name einer Datei, die die Datentabellen enthält. *datalogisch ist vom Datentyp* **vom Datentyp sysname**.  
  
 Die Anzahl von Datendateien muss zwischen 1 und 16 liegen. In der Regel wird mehr als eine Datendatei erstellt, wenn zu erwarten ist, dass die Datenbank umfangreich wird und auf mehrere Datenträger verteilt werden muss.  
  
`[ @dataphysical1 = ] 'dataphysical'`Der physische Name. Enthält einen vollqualifizierten Pfad der Datei, die die Datentabellen enthält. *dataphysical ist vom Datentyp* **nvarchar (260)**.  
  
`[ @datasize1 = ] 'datasize'`Die Größe einer Datei in Megabyte, die Datentabellen enthält. *datasize ist vom Datentyp* **int**. Der minimale *DataSize* -Wert ist 1.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie diese gespeicherte Prozedur, wenn Sie eine Kopie einer Datenbank auf austauschbaren Medien erstellen, wie z. B. auf CD, und die Datenbank an andere Benutzer verteilen möchten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Berechtigung CREATE DATABASE, CREATE ANY DATABASE oder ALTER ANY DATABASE.  
  
 Zur Steuerung der Datenträgernutzung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wird die Berechtigung zum Erstellen von Datenbanken in der Regel auf einige wenige Anmeldekonten beschränkt.  
  
### <a name="permissions-on-data-and-log-files"></a>Berechtigungen für Daten und Protokolldateien  
 Bei der Durchführung bestimmter Vorgänge an einer Datenbank werden die entsprechenden Berechtigungen für ihre Daten und Protokolldateien festgelegt. Durch die Berechtigungen wird verhindert, dass die Dateien versehentlich manipuliert werden, wenn sie sich in einem Verzeichnis mit offenen Berechtigungen befinden.  
  
|Vorgang auf Datenbank|Berechtigungen, die für die Dateien festgelegt sind|  
|---------------------------|------------------------------|  
|Ändern, um eine neue Datei hinzuzufügen|Erstellt|  
|Gesichert|Angefügt|  
|Wiederherstellen|Getrennt|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] legt keine Berechtigungen für Daten und Protokolldateien fest.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die `inventory`-Datenbank als austauschbare Datenbank erstellt.  
  
```  
EXEC sp_create_removable 'inventory',   
   'invsys',  
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\invsys.mdf'  
, 2,   
   'invlog',  
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\invlog.ldf', 4,  
   'invdata',  
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\invdata.ndf',   
10;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_certify_removable &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-certify-removable-transact-sql.md)   
 [Alter Database &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [sp_detach_db &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_helpfilegroup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
