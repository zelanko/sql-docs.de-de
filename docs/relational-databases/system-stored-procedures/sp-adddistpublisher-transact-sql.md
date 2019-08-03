---
title: sp_adddistpublisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistpublisher
- sp_adddistpublisher_TSQL
helpviewer_keywords:
- sp_adddistpublisher
ms.assetid: 04e15011-a902-4074-b38c-3ec2fc73b838
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2190e31245cde19eca4c5a47f21ac48e12f57f53
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771386"
---
# <a name="spadddistpublisher-transact-sql"></a>sp_adddistpublisher (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Konfiguriert einen Verleger so, dass er eine angegebene Verteilungsdatenbank verwendet. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt. Beachten Sie, dass die gespeicherten Prozeduren [ &#40;sp_adddistributor&#41; Transact-SQL](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) und [ &#40;sp_adddistributiondb&#41; Transact-SQL](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) vor der Verwendung dieser gespeicherten Prozedur ausgeführt werden müssen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_adddistpublisher [ @publisher= ] 'publisher'   
        , [ @distribution_db= ] 'distribution_db'   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @working_directory= ] 'working_directory' ]   
    [ , [ @storage_connection_string= ] 'storage_connection_string']
    [ , [ @trusted= ] 'trusted' ]   
    [ , [ @encrypted_password= ] encrypted_password ]   
    [ , [ @thirdparty_flag = ] thirdparty_flag ]  
    [ , [ @publisher_type = ] 'publisher_type' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @distribution_db = ] 'distribution_db'`Der Name der Verteilungs Datenbank. *distributor_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Dieser Parameter wird von Replikations-Agents zum Herstellen einer Verbindung zum Verleger verwendet.  
  
`[ @security_mode = ] security_mode`Der implementierte Sicherheitsmodus. Dieser Parameter wird nur von Replikations-Agents verwendet, um eine Verbindung mit dem Verleger für Abonnements mit verzögertem Update oder mit einem nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger herzustellen. *security_mode* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Replikations-Agents auf dem Verteiler verwenden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung zum Herstellen einer Verbindung mit dem Verleger.|  
|**1** (Standard)|Replikations-Agents auf dem Verteiler verwenden die Windows-Authentifizierung beim Herstellen einer Verbindung zum Verleger.|  
  
`[ @login = ] 'login'`Der Anmelde Name. Dieser Parameter ist erforderlich, wenn *security_mode* den Wert **0**hat. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL. Dieser Parameter wird von Replikations-Agents zum Herstellen einer Verbindung zum Verleger verwendet.  
  
`[ @password = ] 'password']`Das Kennwort. *Password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter wird von Replikations-Agents zum Herstellen einer Verbindung zum Verleger verwendet.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort.  
  
`[ @working_directory = ] 'working_directory'`Der Name des Arbeitsverzeichnisses, das zum Speichern von Daten-und Schema Dateien für die Veröffentlichung verwendet wird. *working_directory* ist vom Datentyp **nvarchar (255)** . der Standardwert ist beispielsweise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `C:\Program Files\Microsoft SQL Server\MSSQL\MSSQ.1\ReplData`der Ordner repldata für diese Instanz von. Dieser Name sollte im UNC-Format angegeben werden.  

 Verwenden `\\<storage_account>.file.core.windows.net\<share>`Sie für Azure SQL-Datenbank.

`[ @storage_connection_string = ] 'storage_connection_string'`Ist für die SQL-Datenbank erforderlich. Verwenden Sie den Zugriffsschlüssel aus dem Azure-Portal unter Speicher > Einstellungen.

 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]

`[ @trusted = ] 'trusted'`Dieser Parameter wurde als veraltet markiert und wird nur aus Gründen der Abwärtskompatibilität bereitgestellt. *Trusted* ist vom Datentyp **nvarchar (5)** , und das Festlegen auf alles, aber **false** führt zu einem Fehler.  
  
`[ @encrypted_password = ] encrypted_password`Das Festlegen von *encrypted_password* wird nicht mehr unterstützt. Der Versuch, diesen **Bit** -Parameter auf **1** festzulegen, führt zu einem Fehler.  
  
`[ @thirdparty_flag = ] thirdparty_flag`Ist, wenn der Verleger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist. *thirdparty_flag* ist vom **Bit**-Wert und kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**0** (Standardwert)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**1**|Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
  
`[ @publisher_type = ] 'publisher_type'`Gibt den Verlegertyp an, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Verleger nicht ist. *publisher_type* ist vom Datentyp sysname. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**MSSQLSERVER**<br /><br /> (Standard)|Gibt einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger an.|  
|**ORAKEL**|Gibt einen standardmäßigen Oracle-Verleger an.|  
|**ORACLE-GATEWAY**|Gibt einen Oracle Gateway-Verleger an.|  
  
 Weitere Informationen zu den Unterschieden zwischen einem Oracle-Verleger und einem Oracle-Gatewayverleger finden Sie unter [Konfigurieren eines Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)-Verlegers.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_adddistpublisher** wird von der Momentaufnahme Replikation, Transaktions Replikation und Mergereplikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistpublisher-tran_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_adddistpublisher**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)  
  
  
