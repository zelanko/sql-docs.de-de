---
title: ADD SENSITIVITY CLASSIFICATION (Transact-SQL) | Microsoft-Dokumentation
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- ADD SENSITIVITY CLASSIFICATION
- ADD_SENSITIVITY_CLASSIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- ADD SENSITIVITY CLASSIFICATION statement
- add labels
- adding labels
- adding labels
- classification [SQL]
- labels [SQL]
- information types
- data classification
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 4296a2b56f5c347a26435a4c192c6dfac7f16538
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018282"
---
# <a name="add-sensitivity-classification-transact-sql"></a>ADD SENSITIVITY CLASSIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Diese Anweisung fügt einer oder mehreren Datenbankspalten Metadaten zur Vertraulichkeitsklassifizierung hinzu. Die Klassifizierung kann eine Vertraulichkeitsbezeichnung und einen Informationstyp umfassen.  

Die Klassifizierung sensibler Daten in Ihrer Datenbankumgebung ermöglicht größere Transparenz und besseren Schutz. Weitere Informationen finden Sie unter [Azure SQL-Datenbank – Datenermittlung und -klassifizierung](https://aka.ms/sqlip).

## <a name="syntax"></a>Syntax  

```sql
ADD SENSITIVITY CLASSIFICATION TO
    <object_name> [, ...n ]
    WITH ( <sensitivity_label_option> [, ...n ] )     

<object_name> ::=
{
    [schema_name.]table_name.column_name
}

<sensitivity_label_option> ::=  
{   
    LABEL = string |
    LABEL_ID = guidOrString |
    INFORMATION_TYPE = string |
    INFORMATION_TYPE_ID = guidOrString  
}
```  

## <a name="arguments"></a>Argumente  

*object_name* ([schema_name.]table_name.column_name)

Der Name der Datenbankspalte, die klassifiziert werden soll. Derzeit wird ausschließlich die Spaltenklassifizierung unterstützt.
    - *schema_name* (optional): Der Name des Schemas, zu dem die klassifizierte Spalte gehört.
    - *table_name* (optional): Der Name der Tabelle, zu der die klassifizierte Spalte gehört.
    - *column_name*: Der Name der Spalte, die klassifiziert wird.

*LABEL*

Der lesbare Name der Vertraulichkeitsbezeichnung. Vertraulichkeitsbezeichnungen stellen die Vertraulichkeit der in der Datenbankspalte gespeicherten Daten dar.

*LABEL_ID*

Ein Bezeichner, dem die Vertraulichkeitsbezeichnung zugeordnet ist. Dieser wird häufig von zentralen Plattformen zum Schutz von Informationen verwendet, um Bezeichnungen im System eindeutig zu identifizieren.

*INFORMATION_TYPE*

Der lesbare Name des Informationstyps. Informationstypen werden verwendet, um den Typ der in der Datenbankspalte gespeicherten Daten zu beschreiben.

*INFORMATION_TYPE_ID*

Ein Bezeichner, dem der Informationstyp zugeordnet ist. Dieser wird häufig von zentralen Plattformen zum Schutz von Informationen verwendet, um Informationstypen im System eindeutig zu identifizieren.


## <a name="remarks"></a>Remarks  

- Einem einzelnen Objekt kann nur eine Klassifizierung hinzugefügt werden. Wird einem bereits klassifizierten Objekt eine Klassifizierung hinzugefügt, überschreibt diese die vorhandene Klassifizierung.
- Mehrere Objekte können mit einer einzigen `ADD SENSITIVITY CLASSIFICATION`-Anweisung klassifiziert werden.
- Über die Systemsicht [sys.sensitivity_classifications](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md) können Informationen zur Vertraulichkeitsklassifizierung für eine Datenbank abgerufen werden.


## <a name="permissions"></a>Berechtigungen

Erfordert die Berechtigung ALTER ANY SENSITIVITY CLASSIFICATION. Die Berechtigung ALTER ANY SENSITIVITY CLASSIFICATION wird von der Datenbankberechtigung ALTER oder der Serverberechtigung CONTROL SERVER impliziert.


## <a name="examples"></a>Beispiele  

### <a name="a-classifying-two-columns"></a>A. Klassifizieren von zwei Spalten

Im folgenden Beispiel werden die Spalten **dbo.sales.price** und **dbo.sales.discount** mit der Vertraulichkeitsbezeichnung **Streng vertraulich** und dem Informationstyp **Finanzen** klassifiziert.

```sql
ADD SENSITIVITY CLASSIFICATION TO
    dbo.sales.price, dbo.sales.discount
    WITH ( LABEL='Highly Confidential', INFORMATION_TYPE='Financial' )
```  

### <a name="b-classifying-only-a-label"></a>B. Klassifizieren von nur einer Bezeichnung
Im folgenden Beispiel wird die Spalte **dbo.customer.comments** mit der Bezeichnung **Vertraulich** und der Bezeichnungs-ID **643f7acd-776a-438d-890c-79c3f2a520d6** klassifiziert. Der Informationstyp wird für diese Spalte nicht klassifiziert.

```sql
ADD SENSITIVITY CLASSIFICATION TO
    dbo.customer.comments
    WITH ( LABEL='Confidential', LABEL_ID='643f7acd-776a-438d-890c-79c3f2a520d6' )
```  

## <a name="see-also"></a>Weitere Informationen  

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[sys.sensitivity_classifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md)

[Berechtigungen (Datenbank-Engine)](https://docs.microsoft.com/sql/relational-databases/security/permissions-database-engine)

[Azure SQL-Datenbank – Datenermittlung und -klassifizierung](https://aka.ms/sqlip)
