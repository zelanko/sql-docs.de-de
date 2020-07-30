---
title: sp_refreshsqlmodule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refreshsqlmodule_TSQL
- sp_refreshsqlmodule
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server], stored procedures
- metadata [SQL Server], triggers
- metadata [SQL Server], views
- triggers [SQL Server], refreshing metadata
- views [SQL Server], refreshing metadata
- sp_refreshsqlmodule
- metadata [SQL Server], functions
- stored procedures [SQL Server], refreshing metadata
- user-defined functions [SQL Server], refreshing metadata
ms.assetid: f0022a05-50dd-4620-961d-361b1681d375
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 11b7ec3592e73d890a6abab1e0d5df39e53eef18
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396464"
---
# <a name="sp_refreshsqlmodule-transact-sql"></a>sp_refreshsqlmodule (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Aktualisiert die Metadaten für die angegebene nicht schemagebundene gespeicherte Prozedur, benutzerdefinierte Funktion oder Sicht, den DML-Trigger, DDL-Trigger auf Datenbankebene oder DDL-Trigger auf Serverebene in der aktuellen Datenbank. Persistente Metadaten für diese Objekte, z. B. Datentypen von Parametern, können aufgrund von Änderungen an den zugrunde liegenden Objekten veraltet sein.
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_refreshsqlmodule [ @name = ] 'module_name'   
    [ , [ @namespace = ] ' <class> ' ]  
  
<class> ::=  
{  
  | DATABASE_DDL_TRIGGER  
  | SERVER_DDL_TRIGGER  
}  
  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'module\_name'`Der Name der gespeicherten Prozedur, der benutzerdefinierten Funktion, der Sicht, des DML-Triggers, des DDL-Triggers auf Datenbankebene oder des DDL-Triggers auf Serverebene. *module_name* kann keine gespeicherte Prozedur Common Language Runtime (CLR) oder eine CLR-Funktion sein. *module_name* kann nicht Schema gebunden werden. *module_name* ist vom Datentyp **nvarchar**und hat keinen Standardwert. *module_name* kann ein mehrteilige Bezeichner sein, kann jedoch nur auf Objekte in der aktuellen Datenbank verweisen.  
  
`[ , @namespace = ] ' \<class> '`Die Klasse des angegebenen Moduls. Wenn *module_name* ein DDL-auslöst ist, \<class> ist erforderlich. *\<class>* ist vom Datentyp **nvarchar**(20). Gültige Eingaben sind:  

* DATABASE_DDL_TRIGGER

* SERVER_DDL_TRIGGER: **gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.

## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_refreshsqlmodule** sollte ausgeführt werden, wenn Änderungen an den Objekten vorgenommen werden, die dem Modul zugrunde liegen, das sich auf seine Definition auswirkt. Andernfalls kann das Modul bei einer Abfrage oder einem Aufruf unerwartete Ergebnisse generieren. Zum Aktualisieren einer Ansicht können Sie entweder **sp_refreshsqlmodule** oder **sp_refreshview** mit den gleichen Ergebnissen verwenden.  
  
 **sp_refreshsqlmodule** wirkt sich nicht auf Berechtigungen, erweiterte Eigenschaften oder SET-Optionen aus, die dem-Objekt zugeordnet sind.  
  
 Um einen DDL-Trigger auf Serverebene zu aktualisieren, führen Sie diese gespeicherte Prozedur aus dem Kontext einer beliebigen Datenbank aus.  
  
> [!NOTE]  
>  Alle Signaturen, die dem-Objekt zugeordnet sind, werden gelöscht, wenn Sie **sp_refreshsqlmodule**ausführen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER-Berechtigung für das Modul und die REFERENCES-Berechtigung für alle CLR-benutzerdefinierten Typen und XML-Schemaauflistungen, auf die durch das Objekt verwiesen wird. Erfordert eine ALTER ANY DATABASE DDL TRIGGER-Berechtigung in der aktuellen Datenbank, wenn es sich beim angegebenen Modul um einen DDL-Trigger auf Datenbankebene handelt. Erfordert eine CONTROL SERVER-Berechtigung, wenn es sich beim angegebenen Modul um einen DDL-Trigger auf Serverebene handelt.  
  
 Zusätzlich ist für Module, die mit der EXECUTE AS-Klausel definiert wurden, die IMPERSONATE-Berechtigung für den angegebenen Prinzipal erforderlich. Im Allgemeinen wird beim Aktualisieren eines Objekts dessen EXECUTE AS-Prinzipal nicht geändert, es sei denn, das Modul wurde mit EXECUTE AS USER definiert und der Benutzername des Prinzipals wird jetzt zu einem anderen Benutzer aufgelöst als zur Erstellungszeit des Moduls.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-refreshing-a-user-defined-function"></a>A. Aktualisieren einer benutzerdefinierten Funktion  
 Im folgenden Beispiel wird eine benutzerdefinierte Funktion aktualisiert. In dem Beispiel werden der Aliasdatentyp `mytype` und die benutzerdefinierte Funktion `to_upper`, die `mytype` verwendet, erstellt. Anschließend wird `mytype` in `myoldtype` umbenannt, und ein neuer `mytype` wird mit einer anderen Definition erstellt. Die `dbo.to_upper`-Funktion wird aktualisiert, sodass sie auf die neue Implementierung von `mytype` verweist und nicht auf die alte.  
  
```  
-- Create an alias type.  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT 'mytype' FROM sys.types WHERE name = 'mytype')  
DROP TYPE mytype;  
GO  
  
CREATE TYPE mytype FROM nvarchar(5);  
GO  
  
IF OBJECT_ID ('dbo.to_upper', 'FN') IS NOT NULL  
DROP FUNCTION dbo.to_upper;  
GO  
  
CREATE FUNCTION dbo.to_upper (@a mytype)  
RETURNS mytype  
WITH ENCRYPTION  
AS  
BEGIN  
RETURN upper(@a)  
END;  
GO  
  
SELECT dbo.to_upper('abcde');  
GO  
  
-- Increase the length of the alias type.  
sp_rename 'mytype', 'myoldtype', 'userdatatype';  
GO  
  
CREATE TYPE mytype FROM nvarchar(10);  
GO  
  
-- The function parameter still uses the old type.  
SELECT name, type_name(user_type_id)   
FROM sys.parameters   
WHERE object_id = OBJECT_ID('dbo.to_upper');  
GO  
  
SELECT dbo.to_upper('abcdefgh'); -- Fails because of truncation  
GO  
  
-- Refresh the function to bind to the renamed type.  
EXEC sys.sp_refreshsqlmodule 'dbo.to_upper';  
  
-- The function parameters are now bound to the correct type and the statement works correctly.  
SELECT name, type_name(user_type_id) FROM sys.parameters  
WHERE object_id = OBJECT_ID('dbo.to_upper');  
GO  
  
SELECT dbo.to_upper('abcdefgh');  
GO  
```  
  
### <a name="b-refreshing-a-database-level-ddl-trigger"></a>B. Aktualisieren eines DDL-Triggers auf Datenbankebene  
 Im folgenden Beispiel wird ein DDL-Trigger auf Datenbankebene aktualisiert.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_refreshsqlmodule @name = 'ddlDatabaseTriggerLog' , @namespace = 'DATABASE_DDL_TRIGGER';  
GO  
```  
  
### <a name="c-refreshing-a-server-level-ddl-trigger"></a>C. Aktualisieren eines DDL-Triggers auf Serverebene  
 Im folgenden Beispiel wird ein DDL-Trigger auf Serverebene aktualisiert.  
  
||  
|-|  
|**Gilt für**:  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.|  
  
```  
USE master;  
GO  
EXEC sys.sp_refreshsqlmodule @name = 'ddl_trig_database' , @namespace = 'SERVER_DDL_TRIGGER';  
GO  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_refreshview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refreshview-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
