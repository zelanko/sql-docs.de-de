---
title: sp_addtype (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addtype
- sp_addtype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addtype
ms.assetid: ed72cd8e-5ff7-4084-8458-2d8ed279d817
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab825ce5eb1310f3ff502965e409731b8741932e
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305135"
---
# <a name="sp_addtype-transact-sql"></a>sp_addtype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Aliasdatentyp.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] verwenden Sie stattdessen [Create Type](../../t-sql/statements/create-type-transact-sql.md) .  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addtype [ @typename = ] type,   
    [ @phystype = ] system_data_type   
    [ , [ @nulltype = ] 'null_type' ] ;  
```  
  
## <a name="arguments"></a>Argumente  
`[ @typename = ] type` ist der Name des Alias Datentyps. Alias Datentyp Namen müssen den Regeln für Bezeichner [entsprechen und in](../../relational-databases/databases/database-identifiers.md) jeder Datenbank eindeutig sein. *Type ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @phystype = ] system_data_type` ist der physische oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellte Datentyp, auf dem der Alias Datentyp basiert. *system_data_type* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
||||  
|-|-|-|  
|**bigint**|**binary(n)**|**bit**|  
|**char(n)**|**datetime**|**decimal**|  
|**float**|**image**|**int**|  
|**money**|**nchar(n)**|**ntext**|  
|**numeric**|**nvarchar(n)**|**real**|  
|**smalldatetime**|**smallint**|**smallmoney**|  
|**sql_variant**|**text**|**tinyint**|  
|**uniqueidentifier**|**varbinary(n)**|**varchar(n)**|  
  
 Alle Parameter, die Leerzeichen oder Satzzeichen enthalten, müssen in einfachen Anführungszeichen stehen. Weitere Informationen zu den verfügbaren Datentypen finden Sie unter [Datentypen &#40;Transact&#41;-SQL](../../t-sql/data-types/data-types-transact-sql.md).  
  
 *n*  
 Eine nicht negative ganze Zahl, die die Länge für den ausgewählten Datentyp angibt.  
  
 *P*  
 Eine nicht negative ganze Zahl, die die maximale Anzahl der Dezimalstellen angibt, die vor und nach dem Dezimalzeichen gespeichert werden können. Weitere Informationen finden Sie unter [decimal und numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *s*  
 Eine nicht negative ganze Zahl, die die maximale Anzahl der Dezimalstellen angibt, die nach dem Dezimalzeichen gespeichert werden können. Diese Zahl muss kleiner oder gleich der Gesamtzahl der Stellen sein. Weitere Informationen finden Sie unter [decimal und numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
`[ @nulltype = ] 'null_type'` gibt an, wie der Alias Datentyp NULL-Werte behandelt. *null_type* ist vom Datentyp **varchar (** 8 **)** und hat den Standardwert NULL und muss in einfache Anführungszeichen (' NULL ', ' not NULL ' oder ' nonull ') eingeschlossen werden. Wenn *null_type* nicht explizit durch **sp_addtype**definiert ist, wird es auf die aktuelle standardmäßige NULL-Zulässigkeit festgelegt. Verwenden Sie die GETANSINULL-Systemfunktion, um die aktuelle Standard-NULL-Zulässigkeit zu ermitteln. Diese kann mithilfe der SET-Anweisung oder ALTER DATABASE angepasst werden. Die NULL-Zulässigkeit sollte explizit definiert werden. Wenn **\@phystype** den Wert **Bit**hat und **\@nulltype** nicht angegeben wird, ist der Standardwert not NULL.  
  
> [!NOTE]  
>  Der *null_type* -Parameter definiert nur die standardmäßige NULL-Zulässigkeit für diesen Datentyp. Wenn der Aliasdatentyp beim Erstellen der Tabelle verwendet und die NULL-Zulässigkeit explizit definiert wurde, hat diese Vorrang vor der definierten NULL-Zulässigkeit. Weitere Informationen finden Sie unter [alter Table &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-table-transact-sql.md) und [Create Table &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Der Name eines Aliasdatentyps muss in der Datenbank eindeutig sein, aber Aliasdatentypen mit unterschiedlichen Namen können dieselbe Definition aufweisen.  
  
 Beim Ausführen von **sp_addtype** wird ein Alias Datentyp erstellt, der in der **sys. types** -Katalog Sicht für eine bestimmte Datenbank angezeigt wird. Wenn der Alias Datentyp in allen neuen benutzerdefinierten Datenbanken verfügbar sein muss, fügen Sie ihn dem **Modell**hinzu. Nach der Erstellung eines Aliasdatentyps können Sie diesen mit CREATE TABLE oder ALTER TABLE verwenden sowie Standards und Regeln an den Aliasdatentyp binden. Alle skalaren Alias Datentypen, die mit **sp_addtype** erstellt werden, sind im **dbo** -Schema enthalten.  
  
 Aliasdatentypen erben die Standardsortierung der Datenbank. Die Sortierungen von Spalten und Variablen von Alias Typen werden in den Anweisungen [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE, ALTER TABLE und DECLARE @*local_variable* definiert. Eine Änderung der Standardsortierung der Datenbank gilt nur für neue Spalten und Variablen des Typs; sie wirkt sich nicht auf die Sortierung bereits vorhandener Spalten und Variablen aus.  
  
> [!IMPORTANT]  
>  Aus Gründen der Abwärtskompatibilität wird der **Public** -Daten Bank Rolle automatisch die REFERENCES-Berechtigung für Alias Datentypen erteilt, die mit **sp_addtype**erstellt werden. Hinweis Wenn Alias Datentypen mithilfe der CREATE TYPE-Anweisung anstelle von **sp_addtype**erstellt werden, erfolgt keine automatische Erteilung.  
  
 Alias Datentypen können nicht mit den Datentypen "@no__t **-0"** , " **Table**", " **XML**", " **varchar (max)** ", " **nvarchar (max)** " oder " **varbinary (max)** " definiert werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Daten Bank Rolle " **db_owner** " oder " **db_ddladmin** ".  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-an-alias-data-type-that-does-not-allow-for-null-values"></a>A. Erstellen eines Aliasdatentyps, der keine NULL-Werte zulässt  
 Im folgenden Beispiel wird ein Alias Datentyp mit dem Namen `ssn` (Sozialversicherungsnummer) erstellt, der auf dem von @no__t -1 angegebenen **varchar** -Datentyp basiert. Der `ssn`-Datentyp wird für Spalten mit 11-stelligen Sozialversicherungsnummern verwendet (999-99-9999). Diese Spalte darf nicht den Wert NULL aufweisen.  
  
 Beachten Sie, dass `varchar(11)` in einfachen Anführungszeichen steht, da es Satzzeichen (Klammern) enthält.  
  
```  
USE master;  
GO  
EXEC sp_addtype ssn, 'varchar(11)', 'NOT NULL';  
GO  
```  
  
### <a name="b-creating-an-alias-data-type-that-allows-for-null-values"></a>B. Erstellen eines Aliasdatentyps, der NULL-Werte zulässt  
 Im folgenden Beispiel wird ein Aliasdatentyp (basierend auf `datetime`) namens `birthday` erstellt, der NULL-Werte zulässt.  
  
```  
USE master;  
GO  
EXEC sp_addtype birthday, datetime, 'NULL';  
```  
  
### <a name="c-creating-additional-alias-data-types"></a>C. Erstellen von zusätzlichen Aliasdatentypen  
 Im folgenden Beispiel werden zwei zusätzliche Aliasdatentypen, `telephone` und `fax`, für nationale und internationale Telefon- und Faxnummern erstellt.  
  
```  
USE master;  
GO  
EXEC sp_addtype telephone, 'varchar(24)', 'NOT NULL';  
GO  
EXEC sp_addtype fax, 'varchar(24)', 'NULL';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherter &#40;Prozeduren Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [sp_bindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_bindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_droptype &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [sp_unbindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
