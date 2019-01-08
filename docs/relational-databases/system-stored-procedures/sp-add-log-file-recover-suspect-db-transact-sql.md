---
title: Sp_add_log_file_recover_suspect_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_file_recover_suspect_db_TSQL
- sp_add_log_file_recover_suspect_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_file_recover_suspect_db
ms.assetid: b41ca3a5-7222-4c22-a012-e66a577a82f6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 525af6370b7e1af1591162109382005adbbf0bac
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52505650"
---
# <a name="spaddlogfilerecoversuspectdb-transact-sql"></a>sp_add_log_file_recover_suspect_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt einer Dateigruppe eine Protokolldatei hinzu, wenn die Wiederherstellung für eine Datenbank wegen unzureichendem Protokollspeicherplatzes (Fehler 9002) nicht ausgeführt werden kann. Nach dem Hinzufügen der das **Sp_add_log_file_recover_suspect_db** deaktiviert die Einstellung für die fehlerverdächtig und führt die Wiederherstellung der Datenbank. Die Parameter sind identisch mit denen für ALTER DATABASE *Database_name* ADD LOG FILE.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_log_file_recover_suspect_db [ @dbName= ] 'database' ,   
    [ @name = ] 'logical_file_name' ,   
    [ @filename= ] 'os_file_name' ,   
    [ @size = ] 'size' ,   
    [ @maxsize = ] 'max_size' ,   
    [ @filegrowth = ] 'growth_increment'  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@dbName =** ] **"**_Datenbank_**"**  
 Der Name der Datenbank. *Datenbank* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@name=** ] **"**_Logical_file_name_**"**  
 Ist der Name in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verweisen auf die Datei. Der Name muss auf dem Server eindeutig sein. *Logical_file_name* ist **nvarchar(260)**, hat keinen Standardwert.  
  
 [  **@filename =** ] **"**_Os_file_name_**"**  
 Der Pfad und der Dateiname, die vom Betriebssystem für die Datei verwendet werden. Die Datei muss sich auf dem Server befinden, auf dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] installiert ist. *Os_file_name* ist **nvarchar(260)**, hat keinen Standardwert.  
  
 [  **@size=** ] **"**_Größe_ **"**  
 Die Anfangsgröße der Datei. *Größe* ist **nvarchar(20)**, hat den Standardwert NULL. Geben Sie eine ganze Zahl (ohne Dezimalstellen) an. Die Suffixe MB und KB können verwendet werden, um Megabyte bzw. Kilobyte als Einheit anzugeben. Die Standardeinheit ist MB. Der Mindestwert ist 512 KB. Wenn *Größe* nicht angegeben ist, wird der Standardwert ist 1 MB.  
  
 [  **@maxsize=** ] **"**_Max_size_ **"**  
 Die maximale Größe, auf die die Datei vergrößert werden kann. *Max_size* ist **nvarchar(20)**, hat den Standardwert NULL. Geben Sie eine ganze Zahl (ohne Dezimalstellen) an. Die Suffixe MB und KB können verwendet werden, um Megabyte bzw. Kilobyte als Einheit anzugeben. Die Standardeinheit ist MB.  
  
 Wenn *Max_size* nicht angegeben ist, wird die Datei wird vergrößert, bis der Datenträger voll ist. Das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows warnt den Administrator, bevor der Speicherplatz auf einem Datenträger erschöpft ist.  
  
 [  **@filegrowth=** ] **"**_Growth_increment_ **"**  
 Die Menge an Speicherplatz, die der Datei jedes Mal dann hinzugefügt wird, wenn neuer Speicherplatz erforderlich wird. *Growth_increment* ist **nvarchar(20)**, hat den Standardwert NULL. Durch den Wert 0 wird angezeigt, dass die Datei nicht vergrößert wird. Geben Sie eine ganze Zahl (ohne Dezimalstellen) an. Der Wert kann in MB, KB oder Prozent (%) angegeben werden. Wenn der Wert in Prozent angegeben wird, ist growth increment der angegebene Prozentsatz der Dateigröße zum Zeitpunkt der Vergrößerung. Bei Zahlen ohne Angabe von MB, KB oder % wird standardmäßig MB verwendet.  
  
 Wenn *Growth_increment* NULL ist, der Standardwert ist 10 % und der Wert für die minimale Größe beträgt 64 KB. Die angegebene Größe wird auf den nächsten durch 64 KB teilbaren Wert gerundet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="permissions"></a>Berechtigungen  
 Führen Sie die Berechtigungen erhalten standardmäßig Mitglieder der **Sysadmin** festen Serverrolle. Diese Berechtigungen sind nicht übertragbar.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wurde die `db1`-Datenbank bei der Wiederherstellung aufgrund unzureichenden Protokollspeicherplatzes (Fehler 9002) als fehlerverdächtig gekennzeichnet.  
  
```  
USE master;  
GO  
EXEC sp_add_log_file_recover_suspect_db db1, logfile2,  
'C:\Program Files\Microsoft SQL  
    Server\MSSQL13.MSSQLSERVER\MSSQL\Data\db1_logfile2.ldf',   
    '1MB';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_add_data_file_recover_suspect_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-data-file-recover-suspect-db-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
