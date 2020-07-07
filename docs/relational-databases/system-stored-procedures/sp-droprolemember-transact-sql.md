---
title: sp_droprolemember (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprolemember_TSQL
- sp_droprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprolemember
ms.assetid: c2f19ab1-e742-4d56-ba8e-8ffd40cf4925
ms.author: vanto
author: VanMSFT
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8be7e84ccd80d80c1345adec3450e5bc8e0f4da6
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012706"
---
# <a name="sp_droprolemember-transact-sql"></a>sp_droprolemember (Transact-SQL)

[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Entfernt ein Sicherheitskonto aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rolle in der aktuellen Datenbank.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Alter Role](../../t-sql/statements/alter-role-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  

### <a name="syntax-for-both-sql-server-and-azure-sql-database"></a>Syntax für SQL Server und Azure SQL-Datenbank

```  
sp_droprolemember [ @rolename = ] 'role' ,   
     [ @membername = ] 'security_account'  
```  

### <a name="syntax-for-both-azure-sql-data-warehouse-and-parallel-data-warehouse"></a>Syntax für Azure SQL Data Warehouse und parallele Data Warehouse

```  
sp_droprolemember 'role' ,  
     'security_account'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'`Der Name der Rolle, aus der das Mitglied entfernt wird. *Role* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. *role* muss in der aktuellen Datenbank vorhanden sein.  
  
`[ @membername = ] 'security_account'`Der Name des Sicherheits Kontos, das aus der Rolle entfernt wird. *security_account* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. *security_account* kann ein Datenbankbenutzer, eine andere Daten Bank Rolle, ein Windows-Anmelde Name oder eine Windows-Gruppe sein. *security_account* muss in der aktuellen Datenbank vorhanden sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 sp_droprolemember entfernt ein Mitglied aus einer Datenbankrolle, indem eine Zeile aus der sysmembers-Tabelle gelöscht wird. Wenn ein Mitglied aus einer Rolle entfernt wird, verliert das Mitglied alle Berechtigungen, die es aufgrund seiner Mitgliedschaft in dieser Rolle hat.  
  
 Mithilfe von sp_dropsrvrolemember entfernen Sie einen Benutzer aus einer festen Serverrolle. Es ist nicht möglich, Benutzer aus der public-Rolle zu entfernen, und dbo kann aus keiner Rolle entfernt werden.  
  
 Verwenden Sie sp_helpuser, um die Mitglieder einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Rolle anzuzeigen, und verwenden Sie Alter Role, um einer Rolle ein Mitglied hinzuzufügen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Benutzer `JonB` aus der `Sales`-Rolle entfernt.  
  
```sql
EXEC sp_droprolemember 'Sales', 'Jonb';  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird der Benutzer `JonB` aus der `Sales`-Rolle entfernt.  
  
```sql
EXEC sp_droprolemember 'Sales', 'JonB'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

