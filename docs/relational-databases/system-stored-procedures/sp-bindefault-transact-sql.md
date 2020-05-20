---
title: sp_bindefault (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_bindefault
- sp_bindefault_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindefault
ms.assetid: 3da70c10-68d0-4c16-94a5-9e84c4a520f6
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b1552f566852f90b3526645313a160f2446b868e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828483"
---
# <a name="sp_bindefault-transact-sql"></a>sp_bindefault (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Bindet einen Standard an eine Spalte oder einen Aliasdatentyp.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Es wird empfohlen, stattdessen Standarddefinitionen zu erstellen, indem Sie das Default-Schlüsselwort der [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) -Anweisung oder der [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) -Anweisung verwenden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_bindefault [ @defname = ] 'default' ,   
    [ @objname = ] 'object_name'   
    [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @defname = ] 'default'`Der Name der Standardeinstellung, die von CREATE DEFAULT erstellt wird. der *Standard* Wert ist **nvarchar (776)** und hat keinen Standardwert.  
  
`[ @objname = ] 'object_name'`Der Name der Tabelle und Spalte oder der Alias Datentyp, an den der Standardwert gebunden werden soll. *object_name* ist vom Datentyp **nvarchar (776)** und hat keinen Standardwert. *object_name* kann nicht mit den benutzerdefinierten Typen " **varchar (max)**", " **nvarchar (max)**", " **varbinary (max)**", " **XML**" oder "CLR" definiert werden.  
  
 Wenn *object_name* ein einteilige Name ist, wird er als Alias Datentyp aufgelöst. Wenn es sich um einen zwei-oder dreiteiligen Namen handelt, wird er zuerst als Tabelle und Spalte aufgelöst. Wenn diese Auflösung fehlschlägt, wird Sie als Alias Datentyp aufgelöst. Standardmäßig erben vorhandene Spalten des Alias Datentyps *default*, es sei denn, ein Standardwert wurde direkt an die Spalte gebunden. Ein Standardwert kann nicht an eine Spalte vom Typ **Text**, **ntext**, **Image**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML**, **Zeitstempel**oder CLR User-Defined Type, eine Spalte mit der Identity-Eigenschaft, eine berechnete Spalte oder eine Spalte mit einer DEFAULT-Einschränkung gebunden werden.  
  
> [!NOTE]  
>  *object_name* können eckige Klammern **[]** als Begrenzungs Bezeichner enthalten. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
`[ @futureonly = ] 'futureonly_flag'`Wird nur verwendet, wenn ein Standard an einen Alias Datentyp gebunden wird. *futureonly_flag* ist vom Datentyp **varchar (15)** und hat den Standardwert NULL. Wenn dieser Parameter auf **futureonly**festgelegt ist, können vorhandene Spalten dieses Datentyps nicht den neuen Standardwert erben. Dieser Parameter wird nie beim Binden eines Standards an eine Spalte verwendet. Wenn *futureonly_flag* NULL ist, wird der neue Standard an alle Spalten des Alias Datentyps gebunden, die aktuell keinen Standard aufweisen oder die den vorhandenen Standardwert des Alias Datentyps verwenden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Mit **sp_bindefault** können Sie einen neuen Standardwert an eine Spalte binden, obwohl die DEFAULT-Einschränkung bevorzugt wird, oder auf einen Alias Datentyp, ohne die Bindung eines vorhandenen standardmäßigen aufzuheben. Der alte Standard wird überschrieben. Sie können einen Standard nicht an einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemdatentyp oder an einen CLR-benutzerdefinierten Typ binden. Ist der Standard nicht kompatibel mit der Spalte, an die er gebunden wurde, gibt [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] eine Fehlermeldung zurück, wenn der Standardwert eingefügt werden soll (nicht beim Binden).  
  
 Vorhandene Spalten des Alias Datentyps erben den neuen Standard, es sei denn, entweder ist ein Standard direkt an Sie gebunden, oder *futureonly_flag* als **futureonly**angegeben. Neue Spalten des Aliasdatentyps erben immer den Standard.  
  
 Wenn Sie einen Standardwert an eine Spalte binden, werden der **sys. Columns** -Katalog Sicht zugehörige Informationen hinzugefügt. Wenn Sie einen Standardwert an einen Alias Datentyp binden, werden der **sys. types** -Katalog Sicht zugehörige Informationen hinzugefügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss Besitzer der Tabelle sein oder ein Mitglied der festen Server Rolle **sysadmin** oder der festen Daten bankrollen **db_owner** und **db_ddladmin** sein.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-binding-a-default-to-a-column"></a>A. Bindet eines Standardwerts an eine Spalte  
 In der aktuellen Datenbank wurde mit CREATE DEFAULT ein Standard mit dem Namen `today` definiert. Im folgenden Beispiel wird der Standard an die `HireDate`-Spalte der `Employee`-Tabelle gebunden. Wird zur `Employee`-Tabelle eine Zeile hinzugefügt und werden für die `HireDate`-Spalte keine Daten angegeben, erhält die Spalte den Wert des Standards `today`.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-default-to-an-alias-data-type"></a>B. Binden eines Standards an einen Aliasdatentyp  
 Ein Standard namens `def_ssn` und ein Aliasdatentyp namens `ssn` sind bereits vorhanden. Im folgenden Beispiel wird der Standard `def_ssn` an den Typ `ssn` gebunden. Wenn eine Tabelle erstellt wird, wird der Standard von allen Spalten geerbt, denen der Aliasdatentyp `ssn` zugewiesen ist. Vorhandene Spalten vom Typ **SSN** Erben auch den Standard **def_ssn**, sofern nicht **futureonly** für *futureonly_flag* Wert angegeben ist, oder wenn für die Spalte kein Standardwert direkt an die Spalte gebunden ist. An Spalten gebundene Standards haben stets Vorrang vor den an Datentypen gebundenen Standards.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonly_flag"></a>C. Verwenden des futureonly_flag  
 Im folgenden Beispiel bindet der Standard `def_ssn` an den Aliasdatentyp `ssn`. Da **futureonly** angegeben ist, sind keine vorhandenen Spalten vom Typ `ssn` betroffen.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D: Verwenden von Begrenzungs Bezeichnerzeichen  
 Das folgende Beispiel zeigt die Verwendung von Begrenzungs bezeichnerbezeichern, `[t.1]` , in *object_name*.  
  
```  
USE master;  
GO  
CREATE TABLE [t.1] (c1 int);   
-- Notice the period as part of the table name.  
EXEC sp_bindefault 'default1', '[t.1].c1' ;  
-- The object contains two periods;   
-- the first is part of the table name,   
-- and the second distinguishes the table name from the column name.  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [Drop default &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-default-transact-sql.md)   
 [sp_unbindefault &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
