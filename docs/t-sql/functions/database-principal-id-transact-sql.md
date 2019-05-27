---
title: DATABASE_PRINCIPAL_ID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATABASE_PRINCIPAL_ID_TSQL
- DATABASE_PRINCIPAL_ID
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], principals
- principal ID numbers [SQL Server]
- DATABASE_PRINCIPAL_ID function
- IDs [SQL Server], principals
ms.assetid: 908c7dd8-c10b-4658-92f6-0224f9835dd9
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3b65c8f0ed4679bcbf35d1e61483346647130ff3
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65943809"
---
# <a name="databaseprincipalid-transact-sql"></a>DATABASE_PRINCIPAL_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt die ID-Nummer eines Prinzipals in der aktuellen Datenbank zurück. Weitere Informationen zu Prinzipalen finden Sie unter [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md).
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DATABASE_PRINCIPAL_ID ( 'principal_name' )  
```  
  
## <a name="arguments"></a>Argumente  
*principal_name*  
Ein Ausdruck vom Typ **sysname**, der den Prinzipal darstellt. Ist *principal_name* nicht angegeben, gibt `DATABASE_PRINCIPAL_ID` die ID des aktuellen Benutzers zurück. Für `DATABASE_PRINCIPAL_ID` sind die Klammern erforderlich.
  
## <a name="return-types"></a>Rückgabetypen
**ssNoversion**  
NULL, wenn der Datenbankprinzipal nicht vorhanden ist.
  
## <a name="remarks"></a>Remarks  
Verwenden Sie `DATABASE_PRINCIPAL_ID` in einer Auswahlliste, in einer WHERE-Klausel oder an einer beliebigen Stelle, an der ein Ausdruck zulässig ist. Weitere Informationen finden Sie unter [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-retrieving-the-id-of-the-current-user"></a>A. Abrufen der ID des aktuellen Benutzers  
In diesem Beispiel wird die Datenbankprinzipal-ID des aktuellen Benutzers zurückgegeben.
  
```sql
SELECT DATABASE_PRINCIPAL_ID();  
GO  
```  
  
### <a name="b-retrieving-the-id-of-a-specified-database-principal"></a>B. Abrufen der ID eines angegebenen Datenbankprinzipals  
In diesem Beispiel wird die Datenbankprinzipal-ID für die Datenbankrolle `db_owner` zurückgegeben.
  
```sql
SELECT DATABASE_PRINCIPAL_ID('db_owner');  
GO  
```  
  
## <a name="see-also"></a>Siehe auch
[Prinzipale &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
[Berechtigungshierarchie &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
[sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)
  
  
