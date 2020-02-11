---
title: sp_adddistributiondb (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: ef595adcf3772dcac92c58764d99bca4374aeb0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771355"
---
# <a name="sp_adddistributiondb-transact-sql"></a>sp_adddistributiondb (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt eine neue Verteilungsdatenbank und installiert das Verteilerschema. Die Verteilungsdatenbank speichert Prozeduren, Schemas und Metadaten, die bei der Replikation verwendet werden. Diese gespeicherte Prozedur wird auf dem Verteiler für die master-Datenbank ausgeführt, um die Verteilungsdatenbank zu erstellen und um die erforderlichen Tabellen und gespeicherten Prozeduren zu installieren, die für die Aktivierung der Replikationsverteilung erforderlich sind.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @database = ] database'`Der Name der zu erstellenden Verteilungs Datenbank. *Database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn die angegebene Datenbank bereits vorhanden und noch nicht als Verteilungsdatenbank gekennzeichnet ist, werden die zum Aktivieren der Verteilung erforderlichen Objekte installiert, und die Datenbank wird als Verteilungsdatenbank gekennzeichnet. Wenn die angegebene Datenbank bereits als Verteilungsdatenbank aktiviert wurde, wird ein Fehler zurückgegeben.  
  
`[ @data_folder = ] 'data_folder'_`Der Name des Verzeichnisses, in dem die Datendatei der Verteilungs Datenbank gespeichert wird. *data_folder* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Wenn der Wert NULL ist, wird das Datenverzeichnis [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für diese Instanz von verwendet, `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`z. b..  
  
`[ @data_file = ] 'data_file'`Der Name der Datenbankdatei. *data_file* ist vom Datentyp **nvarchar (255)** und hat den Standardwert **Database**. Bei NULL erstellt die gespeicherte Prozedur einen Dateinamen mithilfe des Datenbanknamens.  
  
`[ @data_file_size = ] data_file_size`Die anfängliche Datendatei Größe in Megabyte (MB). *data_file_size i*s **int**, der Standardwert ist 5 MB.  
  
`[ @log_folder = ] 'log_folder'`Der Name des Verzeichnisses für die Daten Bank Protokolldatei. *log_folder* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Bei NULL wird das Datenverzeichnis für diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet (beispielsweise `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`).  
  
`[ @log_file = ] 'log_file'`Der Name der Protokolldatei. *log_file* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Bei NULL erstellt die gespeicherte Prozedur einen Dateinamen mithilfe des Datenbanknamens.  
  
`[ @log_file_size = ] log_file_size`Die anfängliche Protokolldatei Größe in Megabyte (MB). *log_file_size* ist vom Datentyp **int**. der Standardwert ist 0 MB. Dies bedeutet, dass die Dateigröße mit der kleinsten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zulässigen Protokolldatei Größe erstellt wird.  
  
`[ @min_distretention = ] min_distretention`Die minimale Beibehaltungs Dauer in Stunden, bevor Transaktionen aus der Verteilungs Datenbank gelöscht werden. *min_distretention* ist vom Datentyp **int**und hat den Standardwert 0 Stunden.  
  
`[ @max_distretention = ] max_distretention`Die maximale Beibehaltungs Dauer in Stunden, bevor Transaktionen gelöscht werden. *max_distretention* ist vom Datentyp **int**und hat den Standardwert 72 Stunden. Abonnements, die keine replizierten Befehle empfangen haben, die älter sind als die maximale Beibehaltungsdauer der Verteilung, werden als inaktiv markiert und müssen erneut initialisiert werden. RAISERROR 21011 wird für jedes inaktive Abonnement ausgegeben. Der Wert **0** bedeutet, dass replizierte Transaktionen nicht in der Verteilungs Datenbank gespeichert werden.  
  
`[ @history_retention = ] history_retention`Die Anzahl der Stunden, für die der Verlauf beibehalten werden soll. *history_retention* ist vom Datentyp **int**und hat den Standardwert 48 Stunden.  
  
`[ @security_mode = ] security_mode`Der Sicherheitsmodus, der beim Herstellen einer Verbindung mit dem Verteiler verwendet werden soll. *security_mode* ist vom Datentyp **int**und hat den Standardwert 1. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Authentifizierung an. **1** gibt die integrierte Windows-Authentifizierung an.  
  
`[ @login = ] 'login'`Der Anmelde Name, der beim Herstellen einer Verbindung mit dem Verteiler verwendet wird, um die Verteilungs Datenbank zu erstellen. Dies ist erforderlich, wenn *security_mode* auf **0**festgelegt ist. *Login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @password = ] 'password'`Das Kennwort, das beim Herstellen einer Verbindung mit dem Verteiler verwendet wird. Dies ist erforderlich, wenn *security_mode* auf **0**festgelegt ist. *Password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @createmode = ] createmode`" *kreatemode* " ist vom Datentyp **int**. der Standardwert ist 1. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**1** (Standard)|Erstellen Sie eine Datenbank, oder verwenden Sie die vorhandene Datenbank, und wenden Sie dann die Datei **instdist. SQL** an, um Replikations Objekte in der Verteilungs|  
|**2**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
 
`[ @deletebatchsize_xact = ] deletebatchsize_xact`Gibt die Batch Größe an, die während der Bereinigung abgelaufener Transaktionen aus den MSRepl_Transactions Tabellen verwendet werden soll. *deletebatchsize_xact* ist vom Datentyp **int**und hat den Standardwert 5000. Dieser Parameter wurde erstmals in SQL Server 2017 eingeführt, gefolgt von Releases in SQL Server 2012 SP4 und SQL Server 2016 SP2.  

`[ @deletebatchsize_cmd = ] deletebatchsize_cmd`Gibt die Batch Größe an, die während der Bereinigung abgelaufener Befehle aus den MSRepl_Commands Tabellen verwendet werden soll. *deletebatchsize_cmd* ist vom Datentyp **int**und hat den Standardwert 2000. Dieser Parameter wurde erstmals in SQL Server 2017 eingeführt, gefolgt von Releases in SQL Server 2012 SP4 und SQL Server 2016 SP2. 
 
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_adddistributiondb** wird bei allen Replikations Typen verwendet. Diese gespeicherte Prozedur kann jedoch nur auf einem Verteiler ausgeführt werden.  
  
 Sie müssen den Verteiler konfigurieren, indem Sie [sp_adddistributor](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) vor dem Ausführen **sp_adddistributiondb**ausführen.  
  
 Führen Sie **sp_adddistributor** aus, bevor Sie **sp_adddistributiondb**ausführen.  
  
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
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_adddistributiondb**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributiondb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)  
  
  
