---
title: Sys.sp_rda_test_connection (Transact-SQL) | Microsoft-Dokumentation
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ef50b770019450f99ede55369c1bdaa654cd52b5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843728"
---
# <a name="syssprdatestconnection-transact-sql"></a>Sys.sp_rda_test_connection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Testet die Verbindung von SQL Server mit der Azure-Remoteserver, und meldet Probleme, die die Migration von Daten verhindern können.  
  
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
 @database_name = N'*Db_name*"  
 Der Name des Stretch-aktivierten SQL Server-Datenbank. Dieser Parameter ist optional.  
  
 @server_address = N'*Azure_server_fully_qualified_address*"  
 Die vollqualifizierte Adresse des Azure-Servers.  
  
-   Wenn Sie einen Wert für **@database_name**, aber die angegebene Datenbank ist nicht für die Stretch-fähigen, dann müssen Sie einen Wert für **@server_address**.  
  
-   Wenn Sie einen Wert für **@database_name**, die angegebene Datenbank ist Stretch-fähigen, und Sie müssen einen Wert für **@server_address**. Wenn Sie einen Wert für **@server_address**, die gespeicherte Prozedur ignoriert, und verwendet die Azure-Server bereits vorhandene, die mit der Stretch-aktivierten Datenbank verknüpft ist.  
  
 @azure_username = N'*Azure_username*  
 Der Benutzername für den Azure-Remoteserver.  
  
 @azure_password = N'*Azure_password*"  
 Das Kennwort für das Azure-Remoteserver.  
  
 @credential_name = N'*Credential_name*"  
 Statt einen Benutzernamen und ein Kennwort zu verwenden, können Sie den Namen des in der Stretch-aktivierten Datenbank gespeicherte Anmeldeinformationen bereitstellen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Im Fall von **Erfolg**Sp_rda_test_connection gibt Fehler 14855 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_SUCCEEDED) mit einem Schweregrad EX_INFO und einen erfolgreichen Rückgabecode.  
  
 Im Fall von **Fehler**Sp_rda_test_connection gibt Fehler 14856 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_FAILED) mit einem Schweregrad EX_USER und Code für ein Fehler zurück.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|LINK_STATE|ssNoversion|Eine der folgenden Werte, die die Werte für entsprechen **Link_state_desc**.<br /><br /> -   0<br />-   1<br />-   2<br />-   3<br />-   4|  
|link_state_desc|varchar(32)|Eine der folgenden Werte, die im vorhergehenden Abschnitt entsprechen die Werte für **Link_state**.<br /><br /> -FEHLERFREI<br />     Die zwischen SQL Server und das Azure-remote-Server fehlerfrei ist.<br />-ERROR_AZURE_FIREWALL<br />     Die Azure-Firewall verhindert, dass die Verbindung zwischen SQL Server und der Azure-Remoteserver.<br />-ERROR_NO_CONNECTION<br />     SQL Server kann nicht es sich um eine Verbindung mit der Azure-Remoteserver herzustellen.<br />-ERROR_AUTH_FAILURE<br />     Einem Authentifizierungsfehler führen kann, wird durch die Verknüpfung zwischen SQL Server und der Azure-Remoteserver verhindert.<br />-FEHLER<br />     Ein Fehler, der ein Authentifizierungsproblem, ein Verbindungsproblem oder ein Problem mit der Firewall ist nicht verhindert, dass die Verbindung zwischen SQL Server und der Azure-Remoteserver.|  
|error_number|ssNoversion|Die Nummer des Fehlers. Wenn kein Fehler vorliegt, ist dieses Feld NULL.|  
|error_message|nvarchar(1024)|Die Fehlermeldung. Wenn kein Fehler vorliegt, ist dieses Feld NULL.|  
  
## <a name="permissions"></a>Berechtigungen  
 Benötigen Sie Db_owner-Berechtigungen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="check-the-connection-from-sql-server-to-the-remote-azure-server"></a>Überprüfen Sie die Verbindung von SQL Server mit dem Azure-Remoteserver  
  
```sql  
EXECUTE sys.sp_rda_test_connection @database_name = N'<Stretch-enabled database>'  
GO  
  
```  
  
 Die Ergebnisse zeigen, dass SQL Server keine Verbindung mit dem Azure-Remoteserver herstellen kann.  
  
|LINK_STATE|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|2|ERROR_NO_CONNECTION|*\<verbindungsrelevante Fehlernummer >*|*\<Verbindung bezogene Fehlermeldung >*|  
  
### <a name="check-the-azure-firewall"></a>Überprüfen Sie die Azure-firewall  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 Die Ergebnisse zeigen, dass die Azure-Firewall die Verbindung zwischen SQL Server und der Azure-Remoteserver verhindert.  
  
|LINK_STATE|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|1|ERROR_AZURE_FIREWALL|*\<Firewall-bezogenen Fehlernummer >*|*\<Firewall-bezogene Fehlermeldung >*|  
  
### <a name="check-authentication-credentials"></a>Überprüfen Sie die Anmeldeinformationen für die Authentifizierung  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 Die Ergebnisse zeigen, dass es sich bei einem Authentifizierungsfehler führen kann, die Verknüpfung zwischen SQL Server und der Azure-Remoteserver verhindert wird.  
  
|LINK_STATE|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|3|ERROR_AUTH_FAILURE|*\<authentifizierungsbezogenen Fehlernummer >*|*\<Authentifizierung bezogene Fehlermeldung >*|  
  
### <a name="check-the-status-of-the-remote-azure-server"></a>Überprüfen des Status der Azure-Remoteserver  
  
```sql  
USE <SQL Server database>  
GO  
EXECUTE sys.sp_rda_test_connection   
    @server_address = N'<server name>.database.windows.net',   
    @azure_username = N'<user name>',   
    @azure_password = N'<password>'  
GO  
  
```  
  
 Die Ergebnisse zeigen, dass die Verbindung fehlerfrei ist und Sie Stretch Database für die angegebene Datenbank aktivieren können.  
  
|LINK_STATE|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|0|HEALTHY|NULL|NULL|  
  
  
