---
title: sys. sp_rda_reauthorize_db (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 01809f0d4eb494d58f035d23846025578aada7c7
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251266"
---
# <a name="syssp_rda_reauthorize_db-transact-sql"></a>sys.sp_rda_reauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stellt die authentifizierte Verbindung zwischen einer lokalen Datenbank, die für Stretch aktiviert ist, und der Remote Datenbank wieder her.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_reauthorize_db @credential = @credential, @with_copy = @with_copy [ , @azure_servername = @azure_servername, @azure_databasename = @azure_databasename ]  
```  
  
## <a name="arguments"></a>Argumente  
 @credential = *\@* Anmelde Informationen  
 Die Daten Bank weit gültigen Anmelde Informationen, die der lokalen Stretch-aktivierten Datenbank zugeordnet sind.  
  
 @with_copy = *\@with_copy*  
 Gibt an, ob eine Kopie der Remote Daten erstellen und eine Verbindung mit der Kopie hergestellt werden soll (empfohlen). *\@with_copy* ist Bit.  
  
 @azure_servername = *\@azure_servername*  
 Gibt den Namen des Azure-Servers an, der die Remote Daten enthält. *\@azure_servername* ist vom Datentyp sysname.  
  
 @azure_databasename = *\@azure_databasename*  
 Gibt den Namen der Azure-Datenbank an, die die Remote Daten enthält. *\@azure_databasename* ist vom Datentyp sysname.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder > 0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert db_owner Berechtigungen.  
  
## <a name="remarks"></a>Remarks  
 Wenn Sie [sys. sp_rda_reauthorize_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) ausführen, um erneut eine Verbindung mit der Azure-Remote Datenbank herzustellen, setzt dieser Vorgang den Abfrage Modus automatisch auf LOCAL_AND_REMOTE zurück. Dies ist das Standardverhalten für Stretch Database. Das heißt, dass Abfragen Ergebnisse sowohl aus lokalen als auch aus Remote Daten zurückgeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die authentifizierte Verbindung zwischen einer lokalen-Datenbank, die für Stretch aktiviert ist, und der Remote Datenbank wieder hergestellt. Er erstellt eine Kopie der Remote Daten (empfohlen) und stellt eine Verbindung mit der neuen Kopie her.  
  
```sql  
DECLARE @credentialName nvarchar(128);   
SET @credentialName = N'<existing_database_scoped_credential_name>';   
EXEC sp_rda_reauthorize_db @credential = @credentialName, @with_copy = 1;  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.sp_rda_deauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch-Datenbank](../../sql-server/stretch-database/stretch-database.md)  
  
  
