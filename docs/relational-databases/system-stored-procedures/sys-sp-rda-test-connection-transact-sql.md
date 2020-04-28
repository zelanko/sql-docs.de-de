---
title: sys. sp_rda_test_connection (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_test_connection
- sys.sp_rda_test_connection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_test_connection stored procedure
ms.assetid: e2ba050c-d7e3-4f33-8281-c9b525b4edb4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69b3b9eae6c292b9501dfbe74b84d7399304a291
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "72305151"
---
# <a name="syssp_rda_test_connection-transact-sql"></a>sys. sp_rda_test_connection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Testet die Verbindung von SQL Server mit dem Azure-Remote Server und meldet Probleme, die eine Datenmigration verhindern können.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EXECUTE sys.sp_rda_test_connection  
   @database_name = N'db_name',   
   @server_address = N'azure_server_fully_qualified_address',  
   @azure_username = N'azure_username',   
   @azure_password = N'azure_password',  
   @credential_name = N'credential_name'  
  
```  
  
## <a name="arguments"></a>Argumente  
 @database_name= N '*db_name*'  
 Der Name der SQL Server Datenbank, für die Stretch aktiviert ist. Dieser Parameter ist optional.  
  
 @server_address= N '*azure_server_fully_qualified_address*'  
 Die voll qualifizierte Adresse des Azure-Servers.  
  
-   Wenn Sie einen Wert für ** \@database_name**bereitstellen, die angegebene Datenbank jedoch nicht Stretch-aktiviert ist, müssen Sie für ** \@server_address**einen Wert angeben.  
  
-   Wenn Sie einen Wert für ** \@database_name**bereitstellen und die angegebene Datenbank Stretch-aktiviert ist, müssen Sie keinen Wert für ** \@server_address**angeben. Wenn Sie einen Wert für ** \@server_address**bereitstellen, wird dieser von der gespeicherten Prozedur ignoriert, und es wird ein vorhandener Azure-Server verwendet, der der Datenbank mit aktiviertem Stretch-  
  
 @azure_username= N '*azure_username*  
 Der Benutzername für den Azure-Remote Server.  
  
 @azure_password= N '*azure_password*'  
 Das Kennwort für den Azure-Remote Server.  
  
 @credential_name= N '*credential_name*'  
 Anstatt einen Benutzernamen und ein Kennwort anzugeben, können Sie den Namen von Anmelde Informationen angeben, die in der Stretch-aktivierten Datenbank gespeichert sind.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Im **Erfolgs**Fall gibt sp_rda_test_connection den Fehler 14855 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_SUCCEEDED) mit dem Schweregrad EX_INFO und einem Erfolgs Rückgabecode zurück.  
  
 Bei **einem Fehler gibt**sp_rda_test_connection den Fehler 14856 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_FAILED) mit dem Schweregrad EX_USER und einem Fehlerrückgabe Code zurück.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|link_state|INT|Einer der folgenden-Werte, die den Werten für **link_state_desc**entsprechen.<br /><br /> -0<br />-1<br />-2<br />-3<br />-4|  
|link_state_desc|varchar(32)|Einer der folgenden-Werte, die den vorangehenden Werten für **LINK_STATE**entsprechen.<br /><br /> -Fehlerfrei<br />     Der zwischen SQL Server und der Azure-Remote Server sind fehlerfrei.<br />-ERROR_AZURE_FIREWALL<br />     Die Verbindung zwischen SQL Server und dem Azure-Remote Server wird von der Azure-Firewall verhindert.<br />-ERROR_NO_CONNECTION<br />     SQL Server kann keine Verbindung mit dem Azure-Remote Server herstellen.<br />-ERROR_AUTH_FAILURE<br />     Ein Authentifizierungsfehler verhindert die Verknüpfung zwischen SQL Server und dem Azure-Remote Server.<br />-Fehler<br />     Ein Fehler, bei dem es sich nicht um ein Authentifizierungs Problem, ein Konnektivitätsproblem oder ein firewallproblem handelt, verhindert die Verknüpfung zwischen SQL Server und dem Azure-Remote Server.|  
|error_number|INT|Die Fehlernummer des Fehlers. Wenn kein Fehler vorliegt, ist dieses Feld NULL.|  
|error_message|nvarchar(1024)|Die Fehlermeldung. Wenn kein Fehler vorliegt, ist dieses Feld NULL.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert db_owner Berechtigungen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="check-the-connection-from-sql-server-to-the-remote-azure-server"></a>Überprüfen Sie die Verbindung zwischen SQL Server und dem Azure-Remote Server.  
  
```sql  
EXECUTE sys.sp_rda_test_connection @database_name = N'<Stretch-enabled database>'  
GO  
  
```  
  
 Die Ergebnisse zeigen, dass SQL Server keine Verbindung mit dem Azure-Remote Server herstellen können.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|2|ERROR_NO_CONNECTION|*\<verbindungsbezogene Fehlernummer>*|*\<verbindungsbezogene Fehlermeldung>*|  
  
### <a name="check-the-azure-firewall"></a>Überprüfen der Azure-Firewall  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 Die Ergebnisse zeigen, dass die Azure-Firewall den Link zwischen SQL Server und dem Azure-Remote Server verhindert.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|1|ERROR_AZURE_FIREWALL|*\<firewallbezogene Fehlernummer>*|*\<>der firewallbezogenen Fehlermeldung*|  
  
### <a name="check-authentication-credentials"></a>Authentifizierungs Anmelde Informationen überprüfen  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 Die Ergebnisse zeigen, dass ein Authentifizierungsfehler die Verknüpfung zwischen SQL Server und dem Azure-Remote Server verhindert.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|3|ERROR_AUTH_FAILURE|*\<Authentifizierungs bezogene Fehlernummer>*|*\<Authentifizierungs bezogene Fehlermeldung>*|  
  
### <a name="check-the-status-of-the-remote-azure-server"></a>Überprüfen des Status des Azure-Remote Servers  
  
```sql  
USE <SQL Server database>  
GO  
EXECUTE sys.sp_rda_test_connection   
    @server_address = N'<server name>.database.windows.net',   
    @azure_username = N'<user name>',   
    @azure_password = N'<password>'  
GO  
  
```  
  
 Die Ergebnisse zeigen, dass die Verbindung fehlerfrei ist und dass Sie Stretch Database für die angegebene Datenbank aktivieren können.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|0|HEALTHY|NULL|NULL|  
  
  
