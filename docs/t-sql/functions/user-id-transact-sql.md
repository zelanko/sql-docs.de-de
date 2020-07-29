---
title: USER_ID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- USER_ID
- USER_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- USER_ID function
- identification numbers [SQL Server]
- IDs [SQL Server], databases
- users [SQL Server], database ID numbers
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
ms.assetid: 67fd29bc-eda9-4d4d-b148-5d3659181a43
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 646ed2166a7519c12fd7695ef49bfe3aca7c0738
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87113269"
---
# <a name="user_id-transact-sql"></a>USER_ID (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die ID eines Datenbankbenutzers zurück.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [DATABASE_PRINCIPAL_ID](../../t-sql/functions/database-principal-id-transact-sql.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
USER_ID ( [ 'user' ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *user*  
 Der zu verwendende Benutzername. *user* ist vom Datentyp **nchar**. Falls ein **char**-Wert angegeben wird, wird dieser implizit in **nchar** konvertiert. Die Klammern sind erforderlich.  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn *user* nicht angegeben ist, wird der aktuelle Benutzer verwendet. Wenn der Parameter das Wort NULL enthält, wird NULL zurückgegeben. Wird USER_ID nach der Ausführung von EXECUTE AS aufgerufen, gibt USER_ID die ID des Kontexts nach dem Identitätswechsel zurück.  
  
 Wenn ein Windows-Prinzipal, der keinem spezifischen Datenbankbenutzer zugeordnet ist, über die Mitgliedschaft in einer Gruppe auf eine Datenbank zugreift, gibt USER_ID den Wert 0 (die ID von public) zurück. Falls ein solcher Prinzipal ein Objekt ohne Angabe eines Schemas erstellt, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen impliziten Benutzer und ein Schema, das dem Windows-Prinzipal zugeordnet ist. Der in diesem Szenario erstellte Benutzer kann nicht zum Herstellen einer Verbindung mit der Datenbank verwendet werden. Bei Aufrufen von USER_ID durch einen Windows-Prinzipal, der einem impliziten Benutzer zugeordnet ist, wird die ID des impliziten Benutzers zurückgegeben.  
  
 USER_ID kann in einer Auswahlliste, in einer WHERE-Klausel und überall dort verwendet werden, wo ein Ausdruck zulässig ist. Weitere Informationen finden Sie unter [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die ID für den `AdventureWorks2012`-Benutzer `Harold` zurückgegeben.  
  
```  
USE AdventureWorks2012;  
SELECT USER_ID('Harold');  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [USER_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [DATABASE_PRINCIPAL_ID &#40;Transact-SQL&#41;](../../t-sql/functions/database-principal-id-transact-sql.md)   
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
