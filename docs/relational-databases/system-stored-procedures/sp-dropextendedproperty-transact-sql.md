---
title: sp_dropextendedproperty (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropextendedproperty_TSQL
- sp_dropextendedproperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproperty
ms.assetid: 4851865a-86ca-4823-991a-182dd1934075
author: stevestein
ms.author: sstein
ms.openlocfilehash: 560cecf8b6cc0aff5b503602c521e503e7cc7fcf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67934014"
---
# <a name="sp_dropextendedproperty-transact-sql"></a>sp_dropextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht eine vorhandene erweiterte Eigenschaft.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropextendedproperty   
    [ @name = ] { 'property_name' }  
      [ , [ @level0type = ] { 'level0_object_type' }   
        , [ @level0name = ] { 'level0_object_name' }   
            [ , [ @level1type = ] { 'level1_object_type' }   
              , [ @level1name = ] { 'level1_object_name' }   
                [ , [ @level2type = ] { 'level2_object_type' }   
                  , [ @level2name = ] { 'level2_object_name' }   
                ]   
            ]   
        ]   
    ]   
```  
  
## <a name="arguments"></a>Argumente  
 [ @name= ] {'*property_name*'}  
 Der Name der zu löschenden Eigenschaft. *property_name* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
 [ @level0type= ] {'*level0_object_type*'}  
 Der Name des angegebenen Objekttyps der Ebene 0. *level0_object_type* ist vom Datentyp **varchar (128)** und hat den Standardwert NULL.  
  
 Gültige Eingabewerte sind ASSEMBLY, CONTRACT, EVENT NOTIFICATION, FILEGROUP, MESSAGE TYPE, PARTITION FUNCTION, PARTITION SCHEME, REMOTE SERVICE BINDING, ROUTE, SCHEMA, SERVICE, USER, TRIGGER, TYPE und NULL.  
  
> [!IMPORTANT]  
>  USER und TYPE als Typen der Ebene 0 werden in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht mehr unterstützt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktionen zurzeit verwenden. Verwenden Sie SCHEMA anstelle von USER als Typ der Ebene 0. Verwenden Sie für TYPE als Typ der Ebene 0 SCHEMA und TYPE als Typ der Ebene 1.  
  
 [ @level0name= ] {'*level0_object_name*'}  
 Der Name des angegebenen Objekttyps der Ebene 0. *level0_object_name* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL.  
  
 [ @level1type= ] {'*level1_object_type*'}  
 Der Typ des Objekts der Ebene 1. *level1_object_type* ist vom Datentyp **varchar (128)** und hat den Standardwert NULL. Gültige Eingabewerte sind AGGREGATE, DEFAULT, FUNCTION, LOGICAL FILE NAME, PROCEDURE, QUEUE, RULE, SYNONYM, TABLE, TABLE_TYPE, TYPE, VIEW, XML SCHEMA COLLECTION und NULL.  
  
 [ @level1name= ] {'*level1_object_name*'}  
 Der Name des angegebenen Objekttyps der Ebene 1. *level1_object_name* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL.  
  
 [ @level2type= ] {'*level2_object_type*'}  
 Der Typ des Objekts der Ebene 2. *level2_object_type* ist vom Datentyp **varchar (128)** und hat den Standardwert NULL. Gültige Eingabewerte sind COLUMN, CONSTRAINT, EVENT NOTIFICATION, INDEX, PARAMETER, TRIGGER und NULL.  
  
 [ @level2name= ] {'*level2_object_name*'}  
 Der Name des angegebenen Objekttyps der Ebene 2. *level2_object_name* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Zum Angeben erweiterter Eigenschaften werden die Objekte in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank in drei Ebenen unterteilt: 0, 1 und 2. Die Ebene 0 ist die höchste Ebene und ist definiert als Objekte, die im Datenbankbereich enthalten sind. Objekte der Ebene 1 sind in einem Schema- oder Benutzerbereich enthalten, und Objekte der Ebene 2 sind in Objekten der Ebene 1 enthalten. Erweiterte Eigenschaften können für Objekte auf einer dieser Ebenen definiert werden. Verweise auf ein Objekt einer Ebene müssen mit den Typen und Namen aller Objekte der höheren Ebenen gekennzeichnet werden.  
  
 Wenn alle Objekttypen und-Namen bei einem gültigen *property_name*NULL sind und eine Eigenschaft in der aktuellen Datenbank vorhanden ist, wird diese Eigenschaft gelöscht. Weitere Informationen finden Sie im Beispiel B, weiter unten in diesem Thema.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der festen Datenbankrollen db_owner und db_ddladmin können erweiterte Eigenschaften beliebiger Objekte mit folgender Ausnahme löschen: db_ddladmin kann weder der Datenbank noch Benutzern oder Rollen Eigenschaften hinzufügen.  
  
 Benutzer können erweiterte Eigenschaften von Objekten löschen, die sie besitzen, oder für die sie über die ALTER- oder CONTROL-Berechtigung verfügen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-dropping-an-extended-property-on-a-column"></a>A. Löschen der erweiterten Eigenschaft einer Spalte  
 Im folgenden Beispiel wird die `caption`-Eigenschaft aus der `id`-Spalte in der `T1`-Tabelle entfernt, die im `dbo`-Schema enthalten ist.  
  
```  
CREATE TABLE T1 (id int , name char (20));  
GO  
EXEC sp_addextendedproperty   
     @name = 'caption'   
    ,@value = 'Employee ID'   
    ,@level0type = 'schema'   
    ,@level0name = dbo  
    ,@level1type = 'table'  
    ,@level1name = 'T1'  
    ,@level2type = 'column'  
    ,@level2name = id;  
GO  
EXEC sp_dropextendedproperty   
     @name = 'caption'   
    ,@level0type = 'schema'   
    ,@level0name = dbo  
    ,@level1type = 'table'  
    ,@level1name = 'T1'  
    ,@level2type = 'column'  
    ,@level2name = id;  
GO  
DROP TABLE T1;  
GO  
```  
  
### <a name="b-dropping-an-extended-property-on-a-database"></a>B. Löschen der erweiterten Eigenschaft einer Datenbank  
 Im folgenden Beispiel wird die-Eigenschaft `MS_Description` aus der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank entfernt. Da die Eigenschaft zur Datenbank selbst gehört, werden keine Objekttypen und -namen angegeben.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_dropextendedproperty   
@name = N'MS_Description';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys. fn_listextendedproperty &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)   
 [sys.extended_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
