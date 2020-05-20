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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 68267f07c125e05f235c1a0bcb4c7f855274bc86
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82814746"
---
# <a name="syssp_rda_reauthorize_db-transact-sql"></a>Sys.sp_rda_reauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stellt die authentifizierte Verbindung zwischen einer lokalen Datenbank, die für Stretch aktiviert ist, und der Remote Datenbank wieder her.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_reauthorize_db @credential = @credential, @with_copy = @with_copy [ , @azure_servername = @azure_servername, @azure_databasename = @azure_databasename ]  
```  
  
## <a name="arguments"></a>Argumente  
 @credential= * \@ Anmelde* Informationen  
 Die Daten Bank weit gültigen Anmelde Informationen, die der lokalen Stretch-aktivierten Datenbank zugeordnet sind.  
  
 @with_copy= * \@ with_copy*  
 Gibt an, ob eine Kopie der Remote Daten erstellen und eine Verbindung mit der Kopie hergestellt werden soll (empfohlen). * \@ with_copy* ist Bit.  
  
 @azure_servername= * \@ azure_servername*  
 Gibt den Namen des Azure-Servers an, der die Remote Daten enthält. * \@ azure_servername* ist vom Datentyp sysname.  
  
 @azure_databasename= * \@ azure_databasename*  
 Gibt den Namen der Azure-Datenbank an, die die Remote Daten enthält. * \@ azure_databasename* ist vom Datentyp sysname.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder >0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert db_owner Berechtigungen.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie [sys. sp_rda_reauthorize_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) ausführen, um erneut eine Verbindung mit der Azure-Remote Datenbank herzustellen, setzt dieser Vorgang den Abfrage Modus automatisch auf LOCAL_AND_REMOTE zurück. Dies ist das Standardverhalten für Stretch Database. Das heißt, dass Abfragen Ergebnisse sowohl aus lokalen als auch aus Remote Daten zurückgeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die authentifizierte Verbindung zwischen einer lokalen-Datenbank, die für Stretch aktiviert ist, und der Remote Datenbank wieder hergestellt. Er erstellt eine Kopie der Remote Daten (empfohlen) und stellt eine Verbindung mit der neuen Kopie her.  
  
```sql  
DECLARE @credentialName nvarchar(128);   
SET @credentialName = N'<existing_database_scoped_credential_name>';   
EXEC sp_rda_reauthorize_db @credential = @credentialName, @with_copy = 1;  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. sp_rda_deauthorize_db &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
