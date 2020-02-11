---
title: Emulieren von Datensätzen und Sammlungen über den CLR-UDT
description: Erläutert, wie die SQL Server Migration Assistant (SSMA) für Oracle die SQL Server benutzerdefinierten Datentypen (User-Defined Data Types, UDT) der Common Language Runtime (CLR) zum Emulieren von Oracle-Datensätzen und-Sammlungen verwendet
authors: nahk-ivanov
ms.service: ssma
ms.devlang: sql
ms.topic: article
ms.date: 1/22/2020
ms.author: alexiva
ms.openlocfilehash: 39a7e8d59425db7ce2d7e81083012321caac35ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "76762814"
---
# <a name="emulating-records-and-collections-via-clr-udt"></a>Emulieren von Datensätzen und Sammlungen über den CLR-UDT

In diesem Artikel wird beschrieben, wie die SQL Server Migration Assistant (SSMA) für Oracle die SQL Server CLR-benutzerdefinierten Datentypen (Common Language Runtime) verwendet, um Oracle-Einträge und-Sammlungen zu emulieren.

## <a name="declaring-record-or-collection-types-and-variables"></a>Deklarieren von Daten Satz-oder Sammlungs Typen und Variablen

SSMA erstellt drei CLR-basierte UDTs:

* `CollectionIndexInt`
* `CollectionIndexString`
* `Record`

Der `CollectionIndexInt` -Typ dient zum Emulieren von durch Integer indizierten Auflistungen, wie z. b. `VARRAY`en, Tabellen und ganzzahligen Schlüssel basierten assoziativen Arrays. Der `CollectionIndexString` -Typ wird für assoziative Arrays verwendet, die durch Zeichen Schlüssel indiziert werden. Die Oracle-Daten Satz Funktionalität wird durch den `Record` -Typ emuliert.

Alle Deklarationen der Daten Satz-oder Sammlungs Typen werden in diese Transact-SQL-Deklaration konvertiert:

```sql
declare @Collection$TYPE varchar(max) = '<type definition>'
```

`<type definition>` Im folgenden finden Sie einen beschreibenden Text, der den Typ der Quelle PL/SQL eindeutig identifiziert.

Betrachten Sie das folgenden Beispiel:

```sql
DECLARE
    TYPE Manager IS RECORD
    (
        mgrid integer,
        mgrname varchar2(40),
        hiredate date
    );

    TYPE Manager_table is TABLE OF Manager INDEX BY PLS_INTEGER;

    Mgr_rec Manager;
    Mgr_table_rec Manager_table;
BEGIN
    mgr_rec.mgrid := 1;
    mgr_rec.mgrname := 'Mike';
    mgr_rec.hiredate := sysdate;

    select
        empno,
        ename,
        hiredate
    BULK COLLECT INTO
        mgr_table_rec
    FROM
        emp;
END;
```

Bei der Konvertierung mithilfe von SSMA wird dieser zum folgenden Transact-SQL-Code:

```sql
BEGIN
    DECLARE
        @CollectionIndexInt$TYPE varchar(max) =
            ' TABLE INDEX BY INT OF ( RECORD ( MGRID INT , MGRNAME STRING , HIREDATE DATETIME ) )'

    DECLARE
        @Mgr_rec$mgrid int,
        @Mgr_rec$mgrname varchar(40),
        @Mgr_rec$hiredate datetime2(0),
        @Mgr_table_rec dbo.CollectionIndexInt =
            dbo.CollectionIndexInt::[Null].SetType(@CollectionIndexInt$TYPE)

    SET @mgr_rec$mgrid = 1
    SET @mgr_rec$mgrname = 'Mike'
    SET @mgr_rec$hiredate = sysdatetime()

    SET @mgr_table_rec = @mgr_table_rec.RemoveAll()
    SET @mgr_table_rec =
        @mgr_table_rec.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionComplex((
                SELECT
                    CAST(EMP.EMPNO AS int) AS mgrid,
                    EMP.ENAME AS mgrname,
                    EMP.HIREDATE AS hiredate
                FROM dbo.EMP
                FOR XML PATH
            ))
        )
END
```

Da die `Manager` Tabelle einem numerischen Index (`INDEX BY PLS_INTEGER`) zugeordnet ist, ist die entsprechende T-SQL-Deklaration, die verwendet wird `@CollectionIndexInt$TYPE`, vom Typ. Wenn die Tabelle mit einem Zeichensatz Index verknüpft ist, z `VARCHAR2`. b., ist die entsprechende T-SQL- `@CollectionIndexString$TYPE`Deklaration vom Typ:

```sql
-- Oracle
TYPE Manager_table is TABLE OF Manager INDEX BY VARCHAR2(40);

-- SQL Server
@CollectionIndexString$TYPE varchar(max) =
    ' TABLE INDEX BY STRING OF ( RECORD ( MGRID INT , MGRNAME STRING , HIREDATE DATETIME ) )'
```

Die Oracle-Daten Satz Funktionalität wird nur durch `Record` den-Typ emuliert.

Jeder `CollectionIndexInt`der Typen, `CollectionIndexString`, und `Record`verfügt über eine statische-Eigenschaft `[Null]` , die eine leere-Instanz zurückgibt. Die `SetType` -Methode wird aufgerufen, um ein leeres-Objekt eines bestimmten Typs zu erhalten (wie im obigen Beispiel gezeigt).

## <a name="constructor-call-conversions"></a>Konstruktoraufrufkonvertierungen

Die konstruktornotation kann nur für Tabellen und `VARRAY`e verwendet werden, sodass alle expliziten Konstruktoraufrufe mithilfe des `CollectionIndexInt` -Typs konvertiert werden. Leere Konstruktoraufrufe werden über `SetType` Aufrufe konvertiert, die für eine NULL `CollectionIndexInt`-Instanz von aufgerufen werden. Die `[Null]` -Eigenschaft gibt die NULL-Instanz zurück. Wenn der Konstruktor eine Liste von Elementen enthält, werden spezielle Methodenaufrufe nacheinander angewendet, um den Wert der Auflistung hinzuzufügen.

Beispiel:

```sql
-- Oracle

DECLARE
    TYPE nested_type IS TABLE OF VARCHAR2(20);
    TYPE varray_type IS VARRAY(5) OF INTEGER;

    v1 nested_type;
    v2 varray_type;
BEGIN
   v1 := nested_type('Arbitrary','number','of','strings');
   v2 := varray_type(10, 20, 40, 80, 160);
END;

-- SQL Server

BEGIN
    DECLARE
        @CollectionIndexInt$TYPE varchar(max) = ' VARRAY OF INT',
        @CollectionIndexInt$TYPE$2 varchar(max) = ' TABLE OF STRING',
        @v1 dbo.CollectionIndexInt,
        @v2 dbo.CollectionIndexInt

    SET @v1 =
        dbo.CollectionIndexInt::[Null]
            .SetType(@CollectionIndexInt$TYPE$2)
            .AddString('Arbitrary')
            .AddString('number')
            .AddString('of')
            .AddString('strings')

   SET @v2 =
       dbo.CollectionIndexInt::[Null]
            .SetType(@CollectionIndexInt$TYPE)
            .AddInt(10)
            .AddInt(20)
            .AddInt(40)
            .AddInt(80)
            .AddInt(160)
END
```

## <a name="referencing-and-assigning-record-and-collection-elements"></a>Verweisen auf und Zuweisen von Datensatz-und Sammlungs Elementen

Jede der UDTs verfügt über eine Reihe von Methoden, die mit Elementen der verschiedenen Datentypen arbeiten. Beispielsweise weist die `SetDouble` -Methode einen `float(53)` Wert dem Datensatz oder der Auflistung zu `GetDouble` und kann diesen Wert lesen. Im folgenden finden Sie eine komplette Liste der Methoden:

```sql
GetCollectionIndexInt(@key <KeyType>) returns CollectionIndexInt;
SetCollectionIndexInt(@key <KeyType>, @value CollectionIndexInt) returns <UDT_type>;
GetCollectionIndexString(@key <KeyType>) returns CollectionIndexString;
SetCollectionIndexString(@key <KeyType>, @value CollectionIndexString) returns <UDT_type>;
Record GetRecord(@key <KeyType>) returns Record;
SetRecord(@key <KeyType>, @value Record) returns <UDT_type>;
GetString(@key <KeyType>) returns nvarchar(max);
SetString(@key <KeyType>, @value nvarchar(max)) returns nvarchar(max);
GetDouble(@key <KeyType>) returns float(53);
SetDouble(@key <KeyType>, @value float(53)) returns <UDT_type>;
GetDatetime(@key <KeyType>) returns datetime;
SetDatetime(@key <KeyType>, @value datetime) returns <UDT_type>;
GetVarbinary(@key <KeyType>) returns varbinary(max);
SetVarbinary(@key <KeyType>, @value varbinary(max)) returns <UDT_type>;
SqlDecimal GetDecimal(@key <KeyType>);
SetDecimal(@key <KeyType>, @value numeric) returns <UDT_type>;
GetXml(@key <KeyType>) returns xml;
SetXml(@key <KeyType>, @value xml) returns <UDT_type>;
GetInt(@key <KeyType>) returns bigint;
SetInt(@key <KeyType>, @value bigint) returns <UDT_type>;
```

Diese Methoden werden beim Verweisen auf oder Zuweisen eines Werts zu einem Element einer Sammlung/eines Datensatzes verwendet.

```sql
-- Oracle
a_collection(i) := 'VALUE';

-- SQL Server
SET @a_collection = @a_collection.SetString(@i, 'VALUE');
```

Beim Umrechnen von Zuweisungs Anweisungen für mehrdimensionale Auflistungen oder Auflistungen mit Datensatz-Elementen fügt SSMA die folgenden Methoden hinzu, um auf ein übergeordnetes Element innerhalb der Set-Methode

```sql
GetOrCreateCollectionIndexInt(@key <KeyType>) returns CollectionIndexInt;
GetOrCreateCollectionIndexString(@key <KeyType>) returns CollectionIndexString;
GetOrCreateRecord(@key <KeyType>) returns Record;
```

Beispielsweise wird eine Auflistung der Datensatz-Elemente auf diese Weise erstellt:

```sql
-- Oracle
DECLARE
    TYPE rec_details IS RECORD (id int, name varchar2(20));
    TYPE ntb1 IS TABLE of rec_details index BY binary_integer;
    c ntb1;
BEGIN
    c(1).id := 1;
END;

-- SQL Server
DECLARE
   @CollectionIndexInt$TYPE varchar(max) =
       ' TABLE INDEX BY INT OF ( RECORD ( ID INT , NAME STRING ) )',
   @c dbo.CollectionIndexInt =
       dbo.CollectionIndexInt::[Null].SetType(@CollectionIndexInt$TYPE)

SET @c = @c.SetRecord(1, @c.GetOrCreateRecord(1).SetInt(N'ID', 1))
```

## <a name="collection-built-in-methods"></a>Integrierte Methoden für Sammlungen

SSMA verwendet die folgenden UDT-Methoden zum emulieren integrierter Methoden von PL/SQL-Auflistungen.

Oracle-Sammlungs Methoden | `CollectionIndexInt`und `CollectionIndexString` gleichwertig
--- | ---
COUNT | `Count returns int`
Delete | `RemoveAll() returns <UDT_type>`
Löschen (n) | `Remove(@index int) returns <UDT_type>`
Löschen (m, n) | `RemoveRange(@indexFrom int, @indexTo int) returns <UDT_type>`
EXISTS | `ContainsElement(@index int) returns bit`
Gewähren | `Extend() returns <UDT_type>`
Erweitern (n) | `Extend() returns <UDT_type>`
Erweitern (n, i) | `ExtendDefault(@count int, @def int) returns <UDT_type>`
FIRST | `First() returns int`
LAST | `Last() returns int`
LIMIT | –
PRIOR | `Prior(@current int) returns int`
NEXT | `Next(@current int) returns int`
TRIM | `Trim() returns <UDT_type>`
Trim (n) | `TrimN(@count int) returns <UDT_type>`

## <a name="bulk-collect-operation"></a>Massen Sammel Vorgang

SSMA konvertiert `BULK COLLECT INTO` -Anweisungen in `SELECT ... FOR XML PATH` SQL Server-Anweisung, deren Ergebnis in eine der folgenden Funktionen umschließt:

* `ssma_oracle.fn_bulk_collect2CollectionSimple`
* `ssma_oracle.fn_bulk_collect2CollectionComplex`

Die Auswahl hängt vom Typ des Zielobjekts ab. Diese Funktionen geben XML-Werte zurück, die von `CollectionIndexInt`den Typen `CollectionIndexString` , `Record` und analysiert werden können. Eine spezielle `AssignData` Funktion weist dem UDT eine XML-basierte Auflistung zu.

SSMA erkennt drei Arten von `BULK COLLECT INTO` Anweisungen.

### <a name="the-collection-contains-elements-with-scalar-types-and-the-select-list-contains-one-column"></a>Die Auflistung enthält Elemente mit skalaren Typen, und die `SELECT` Liste enthält eine Spalte.

```sql
-- Oracle
SELECT column_name_1
BULK COLLECT INTO <collection_name_1>
FROM <data_source>

-- SQL Server
SET @<collection_name_1> =
    @<collection_name_1>.AssignData(
        ssma_oracle.fn_bulk_collect2CollectionSimple(
            (SELECT column_name_1 FROM <data_source> FOR XML PATH)))
```

### <a name="the-collection-contains-elements-with-record-types-and-the-select-list-contains-one-column"></a>Die Auflistung enthält Elemente mit Daten Satz Typen, und `SELECT` die Liste enthält eine Spalte.

```sql
-- Oracle
SELECT
    column_name_1[, column_name_2...]
BULK COLLECT INTO
    <collection_name_1>
FROM
    <data_source>

-- SQL Server
SET @<collection_name_1> =
    @<collection_name_1>.AssignData(
        ssma_oracle.fn_bulk_collect2CollectionComplex(
            (SELECT
                column_name_1 as [collection_name_1_element_field_name_1],
                column_name_2 as [collection_name_1_element_field_name_2]
            FROM <data_source>
            FOR XML PATH)))
```

### <a name="the-collection-contains-elements-with-scalar-type-and-the-select-list-contains-multiple-columns"></a>Die Auflistung enthält Elemente mit einem skalaren Typ, und `SELECT` die Liste enthält mehrere Spalten.

```sql
-- Oracle
SELECT
    column_name_1[, column_name_2 ...]
BULK COLLECT INTO
    <collection_name_1>[, <collection_name_2> ...]
FROM
    <data_source>

-- SQL Server
;WITH bulkC AS (
    SELECT
        column_name_1 [collection_name_1_element_field_name_1],
        column_name_2 [collection_name_1_element_field_name_2]
    FROM
        <data_source>
)
SELECT
    @<collection_name_1> =
        @<collection_name_1>.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionSimple(
                (SELECT
                    [collection_name_1_element_field_name_1]
                FROM
                    bulkC
                FOR XML PATH))),
    @<collection_name_2> =
        @<collection_name_2>.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionSimple(
                (SELECT
                    [collection_name_1_element_field_name_2]
                FROM bulkC
                FOR XML PATH)))
```

## <a name="select-into-record"></a>In Datensatz auswählen

Wenn das Ergebnis der Oracle-Abfrage in einer PL/SQL-Daten Satz Variablen gespeichert ist, haben Sie zwei Möglichkeiten, abhängig von der SSMA-Einstellung für **Datensatz konvertieren als Liste getrennter Variablen** (verfügbar **im Menü Extras** , **Projekteinstellungen**und dann **Allgemeine** -> **Konvertierung**). Wenn der Wert dieser Einstellung auf **Ja** (Standardeinstellung) festgelegt ist, wird von SSMA keine Instanz des Daten Satz Typs erstellt. Stattdessen wird der Datensatz in die konstituierenden Felder aufgeteilt, indem eine separate Transact-SQL-Variable pro Datensatz-Feld erstellt wird. Wenn die Einstellung auf **Nein**festgelegt ist, wird der Datensatz instanziiert, und jedem Feld wird `Set` mithilfe von Methoden ein Wert zugewiesen.
