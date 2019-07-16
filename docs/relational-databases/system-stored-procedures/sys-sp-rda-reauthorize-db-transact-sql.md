---
title: Sys. sp_rda_reauthorize_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sp_rda_reauthorize_db
- sp_rda_reauthorize_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reauthorize_db stored procedure
ms.assetid: f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c5150cc40fa8d2cecee02a9d3339eea0c1bf740
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083713"
---
# <a name="syssprdareauthorizedb-transact-sql"></a>sys.sp_rda_reauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stellt die authentifizierte Verbindung zwischen einer lokalen Datenbank für Stretch und die remote-Datenbank aktiviert.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_reauthorize_db @credential = @credential, @with_copy = @with_copy [ , @azure_servername = @azure_servername, @azure_databasename = @azure_databasename ]  
```  
  
## <a name="arguments"></a>Argumente  
 @credential = *@credential*  
 Ist die datenbankweit gültigen Anmeldeinformationen der lokalen Stretch-aktivierten Datenbank zugeordnet.  
  
 @with_copy = *@with_copy*  
 Gibt an, ob eine Kopie der Remotedaten und eine Verbindung mit der Kopiervorgangs (empfohlen). *@with_copy* ist vom Datentyp bit.  
  
 @azure_servername = *@azure_servername*  
 Gibt den Namen des Azure-Servers, der die Remotedaten enthält. *@azure_servername* ist vom Datentyp Sysname.  
  
 @azure_databasename = *@azure_databasename*  
 Gibt den Namen der Azure-Datenbank, die die remote-Daten enthält. *@azure_databasename* ist vom Datentyp Sysname.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder > 0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Benötigen Sie Db_owner-Berechtigungen.  
  
## <a name="remarks"></a>Hinweise  
 Beim Ausführen von [Sys. sp_rda_reauthorize_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) um zum Azure-Remotedatenbank erneut eine Verbindung herstellen, dieser Vorgang automatisch den Abfragemodus auf zurückgesetzt LOCAL_AND_REMOTE, dies ist das Standardverhalten für Stretch Database. D.h., geben Abfragen Ergebnisse aus lokalen und Remotedaten zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die authentifizierte Verbindung zwischen einer lokalen Datenbank für Stretch und die remote-Datenbank aktiviert. Es wird eine Kopie der Remotedaten (empfohlen) und stellt eine Verbindung her, auf die neue Kopie.  
  
```sql  
DECLARE @credentialName nvarchar(128);   
SET @credentialName = N'<existing_database_scoped_credential_name>';   
EXEC sp_rda_reauthorize_db @credential = @credentialName, @with_copy = 1;  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.sp_rda_deauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
