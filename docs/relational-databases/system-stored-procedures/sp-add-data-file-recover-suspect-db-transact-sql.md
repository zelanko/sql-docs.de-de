---
description: sp_add_data_file_recover_suspect_db (Transact-SQL)
title: sp_add_data_file_recover_suspect_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_data_file_recover_suspect_db
- sp_add_data_file_recover_suspect_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_data_file_recover_suspect_db
ms.assetid: b25262aa-a228-48b7-8739-6581c760b171
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae07b655dd7b693876c61b600315ac8874d988ff
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481650"
---
# <a name="sp_add_data_file_recover_suspect_db-transact-sql"></a>sp_add_data_file_recover_suspect_db (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Fügt einer Dateigruppe eine Datendatei hinzu, wenn die Wiederherstellung für eine Datenbank wegen unzureichendem Speicherplatzes (Fehler 1105) für die Dateigruppe nicht ausgeführt werden kann. Nachdem die Datei hinzugefügt wurde, deaktiviert diese gespeicherte Prozedur die Einstellung, die die Datenbank als fehlerverdächtig kennzeichnet, und führt die Wiederherstellung der Datenbank durch. Die Parameter sind dieselben wie für ALTER DATABASE *database_name* Add File.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_data_file_recover_suspect_db [ @dbName= ] 'database'   
    , [ @filegroup = ] 'filegroup_name'   
    , [ @name = ] 'logical_file_name'   
    , [ @filename= ] 'os_file_name'   
    , [ @size = ] 'size'   
    , [ @maxsize = ] 'max_size'   
    , [ @filegrowth = ] 'growth_increment'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbName = ] 'database_ '` Der Name der Datenbank. *Database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @filegroup = ] 'filegroup_name_ '` Die Datei Gruppe, der die Datei hinzugefügt werden soll. *filegroup_name* ist vom Datentyp **nvarchar (260)** und hat den Standardwert NULL, der die primäre Datei angibt.  
  
`[ @name = ] 'logical_file_name_ '` Der Name, der in verwendet wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um auf die Datei zu verweisen. Der Name muss auf dem Server eindeutig sein. *logical_file_name* ist vom Datentyp **nvarchar (260)** und hat keinen Standardwert.  
  
`[ @filename = ] 'os_file_name_ '` Der Pfad und der Dateiname, die vom Betriebssystem für die Datei verwendet werden. Die Datei muss sich auf einer Instanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)]s befinden. *os_file_name* ist vom Datentyp **nvarchar (260)** und hat keinen Standardwert.  
  
`[ @size = ] 'size_ '` Die Anfangs Größe der Datei. *size* ist vom Datentyp **nvarchar (20)** und hat den Standardwert NULL. Geben Sie eine ganze Zahl (ohne Dezimalstellen) an. Die Suffixe MB und KB können verwendet werden, um Megabyte bzw. Kilobyte als Einheit anzugeben. Die Standardeinheit ist MB. Der Mindestwert ist 512 KB. Wenn die *Größe* nicht angegeben wird, beträgt der Standardwert 1 MB.  
  
`[ @maxsize = ] 'max_size_ '` Die maximale Größe, auf die die Datei vergrößert werden kann. *max_size* ist vom Datentyp **nvarchar (20)** und hat den Standardwert NULL. Geben Sie eine ganze Zahl (ohne Dezimalstellen) an. Die Suffixe MB und KB können verwendet werden, um Megabyte bzw. Kilobyte als Einheit anzugeben. Die Standardeinheit ist MB.  
  
 Wenn *max_size* nicht angegeben ist, wird die Datei vergrößert, bis der Datenträger voll ist. Das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows warnt den Administrator, bevor der Speicherplatz auf einem Datenträger erschöpft ist.  
  
`[ @filegrowth = ] 'growth_increment_ '` Der Speicherplatz, der der Datei jedes Mal hinzugefügt wird, wenn neuer Speicherplatz erforderlich ist. *growth_increment* ist vom Datentyp **nvarchar (20)** und hat den Standardwert NULL. Durch den Wert 0 wird angezeigt, dass die Datei nicht vergrößert wird. Geben Sie eine ganze Zahl (ohne Dezimalstellen) an. Der Wert kann in MB, KB oder Prozent (%) angegeben werden. Wenn der Wert in Prozent angegeben wird, ist growth increment der angegebene Prozentsatz der Dateigröße zum Zeitpunkt der Vergrößerung. Bei Zahlen ohne Angabe von MB, KB oder % wird standardmäßig MB verwendet.  
  
 Wenn *growth_increment* NULL ist, ist der Standardwert 10%, und der Mindestwert beträgt 64 KB. Die angegebene Größe wird auf den nächsten durch 64 KB teilbaren Wert gerundet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Ausführungs Berechtigungen werden standardmäßig Mitgliedern der festen Server Rolle **sysadmin** zugewiesen. Diese Berechtigungen sind nicht übertragbar.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wurde die `db1`-Datenbank bei der Wiederherstellung aufgrund unzureichenden Speicherplatzes (Fehler 1105) in der `fg1`-Dateigruppe als fehlerverdächtig gekennzeichnet.  
  
```  
USE master;  
GO  
EXEC sp_add_data_file_recover_suspect_db db1, fg1, file2,  
    'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\db1_file2.mdf', '1MB';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_add_log_file_recover_suspect_db &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
