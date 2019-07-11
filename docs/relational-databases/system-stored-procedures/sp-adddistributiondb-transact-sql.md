---
title: Sp_adddistributiondb (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/30/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistributiondb_TSQL
- sp_adddistributiondb
helpviewer_keywords:
- sp_adddistributiondb
ms.assetid: e9bad56c-d2b3-44ba-a4d7-ff2fd842e32d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a6fb689832069ab8be4a260fecaa27b6b29f7ca5
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716741"
---
# <a name="spadddistributiondb-transact-sql"></a>sp_adddistributiondb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt eine neue Verteilungsdatenbank und installiert das Verteilerschema. Die Verteilungsdatenbank speichert Prozeduren, Schemas und Metadaten, die bei der Replikation verwendet werden. Diese gespeicherte Prozedur wird auf dem Verteiler für die master-Datenbank ausgeführt, um die Verteilungsdatenbank zu erstellen und um die erforderlichen Tabellen und gespeicherten Prozeduren zu installieren, die für die Aktivierung der Replikationsverteilung erforderlich sind.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_adddistributiondb [ @database= ] 'database'   
    [ , [ @data_folder= ] 'data_folder' ]   
    [ , [ @data_file= ] 'data_file' ]   
    [ , [ @data_file_size= ] data_file_size ]   
    [ , [ @log_folder= ] 'log_folder' ]   
    [ , [ @log_file= ] 'log_file' ]   
    [ , [ @log_file_size= ] log_file_size ]   
    [ , [ @min_distretention= ] min_distretention ]   
    [ , [ @max_distretention= ] max_distretention ]   
    [ , [ @history_retention= ] history_retention ]   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @createmode= ] createmode ]  
    [ , [ @from_scripting = ] from_scripting ] 
    [ , [ @deletebatchsize_xact = ] deletebatchsize_xact ] 
    [ , [ @deletebatchsize_cmd = ] deletebatchsize_cmd ] 
```  
  
## <a name="arguments"></a>Argumente  
`[ @database = ] database'` Ist der Name der Verteilungsdatenbank erstellt werden. *Datenbank* ist **Sysname**, hat keinen Standardwert. Wenn die angegebene Datenbank bereits vorhanden und noch nicht als Verteilungsdatenbank gekennzeichnet ist, werden die zum Aktivieren der Verteilung erforderlichen Objekte installiert, und die Datenbank wird als Verteilungsdatenbank gekennzeichnet. Wenn die angegebene Datenbank bereits als Verteilungsdatenbank aktiviert wurde, wird ein Fehler zurückgegeben.  
  
`[ @data_folder = ] 'data_folder'_` Ist der Name des Verzeichnisses zum Speichern von Daten der Verteilungs-Datenbankdatei verwendet. *Data_folder* ist **nvarchar(255)** , hat den Standardwert NULL. Bei NULL wird das Datenverzeichnis für diese Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, beispielsweise `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`.  
  
`[ @data_file = ] 'data_file'` Ist der Name der Datenbankdatei. *Data_file* ist **nvarchar(255)** , hat den Standardwert **Datenbank**. Bei NULL erstellt die gespeicherte Prozedur einen Dateinamen mithilfe des Datenbanknamens.  
  
`[ @data_file_size = ] data_file_size` Ist die ursprüngliche Datendateigröße in Megabytes (MB) an. *Data_file_size ich*s **Int**, hat den Standardwert 5 MB.  
  
`[ @log_folder = ] 'log_folder'` Ist der Name des Verzeichnisses für die Datenbank-Protokolldatei. *Log_folder* ist **nvarchar(255)** , hat den Standardwert NULL. Bei NULL wird das Datenverzeichnis für diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet (beispielsweise `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`).  
  
`[ @log_file = ] 'log_file'` Ist der Name der Protokolldatei. *Log_file* ist **nvarchar(255)** , hat den Standardwert NULL. Bei NULL erstellt die gespeicherte Prozedur einen Dateinamen mithilfe des Datenbanknamens.  
  
`[ @log_file_size = ] log_file_size` Ist die ursprüngliche Protokolldateigröße in Megabyte (MB) an. *Log_file_size* ist **Int**, hat den Standardwert 0 MB, d. h. die Dateigröße erstellt wird, mit der kleinsten zugelassenen Protokolldateigröße von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
`[ @min_distretention = ] min_distretention` Ist die minimale Beibehaltungsdauer in Stunden, bevor Transaktionen aus der Verteilungsdatenbank gelöscht werden. *Min_distretention* ist **Int**, hat den Standardwert 0 Stunden.  
  
`[ @max_distretention = ] max_distretention` Ist die maximale Beibehaltungsdauer in Stunden, bevor Transaktionen gelöscht werden. *Max_distretention* ist **Int**, hat den Standardwert von 72 Stunden. Abonnements, die keine replizierten Befehle empfangen haben, die älter sind als die maximale Beibehaltungsdauer der Verteilung, werden als inaktiv markiert und müssen erneut initialisiert werden. RAISERROR 21011 wird für jedes inaktive Abonnement ausgegeben. Der Wert **0** bedeutet, die replizierte Transaktionen werden nicht in der Verteilungsdatenbank gespeichert.  
  
`[ @history_retention = ] history_retention` Ist die Anzahl der Stunden, für den Verlauf erhalten bleibt. *History_retention* ist **Int**, hat den Standardwert von 48 Stunden.  
  
`[ @security_mode = ] security_mode` Ist der Sicherheitsmodus, der beim Verbinden mit dem Verteiler verwenden. *Security_mode* ist **Int**, hat den Standardwert 1. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung; **1** gibt die integrierte Windows-Authentifizierung.  
  
`[ @login = ] 'login'` Der Anmeldename wird verwendet, wenn der verbindungsherstellung zum Verteiler die Verteilungsdatenbank zu erstellen. Dies ist erforderlich, wenn *Security_mode* nastaven NA hodnotu **0**. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
`[ @password = ] 'password'` Das Kennwort wird verwendet werden, wenn es sich bei der verbindungsherstellung zum Verteiler. Dies ist erforderlich, wenn *Security_mode* nastaven NA hodnotu **0**. *Kennwort* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @createmode = ] createmode` *Createmode* ist **Int**, hat den Standardwert 1, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**1** (Standard)|CREATE DATABASE oder Verwenden einer vorhandenen Datenbank und anschließendes Anwenden **instdist.sql** Datei, um Replikationsobjekte in der Verteilungsdatenbank zu erstellen.|  
|**2**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
 
`[ @deletebatchsize_xact = ] deletebatchsize_xact` Gibt die Batchgröße, die während der Bereinigung der abgelaufene Transaktionen aus der MSRepl_Transactions-Tabellen verwendet werden. *Deletebatchsize_xact* ist **Int**, hat den Standardwert von 5000. Dieser Parameter wurde erstmals in SQL Server 2017, gefolgt von Versionen in SQL Server 2012 SP4 und SQL Server 2016 SP2 eingeführt.  

`[ @deletebatchsize_cmd = ] deletebatchsize_cmd` Gibt die Batchgröße, die während der Bereinigung abgelaufener Befehle über die MSRepl_Commands-Tabellen verwendet werden. *Deletebatchsize_cmd* ist **Int**, hat den Standardwert 2000. Dieser Parameter wurde erstmals in SQL Server 2017, gefolgt von Versionen in SQL Server 2012 SP4 und SQL Server 2016 SP2 eingeführt. 
 
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_adddistributiondb** wird in allen Replikationstypen verwendet. Diese gespeicherte Prozedur kann jedoch nur auf einem Verteiler ausgeführt werden.  
  
 Sie müssen den Verteiler konfigurieren, indem Sie Ausführung [Sp_adddistributor](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) vor der Ausführung **Sp_adddistributiondb**.  
  
 Führen Sie **Sp_adddistributor** vor der Ausführung **Sp_adddistributiondb**.  
  
## <a name="example"></a>Beispiel  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
-- Specify the replication working directory.  
SET @directory = N'\\' + $(DistPubServer) + '\repldata';  
-- Specify the publication database.  
SET @publicationDB = N'AdventureWorks2012';   
  
-- Install the server MYDISTPUB as a Distributor using the defaults,  
-- including autogenerating the distributor password.  
USE master  
EXEC sp_adddistributor @distributor = @distributor;  
  
-- Create a new distribution database using the defaults, including  
-- using Windows Authentication.  
USE master  
EXEC sp_adddistributiondb @database = @distributionDB,   
    @security_mode = 1;  
GO  
  
-- Create a Publisher and enable AdventureWorks2012 for replication.  
-- Add MYDISTPUB as a publisher with MYDISTPUB as a local distributor  
-- and use Windows Authentication.  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
USE [distribution]  
EXEC sp_adddistpublisher @publisher=@publisher,   
    @distribution_db=@distributionDB,   
    @security_mode = 1;  
GO  
  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_adddistributiondb**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)  
  
  
