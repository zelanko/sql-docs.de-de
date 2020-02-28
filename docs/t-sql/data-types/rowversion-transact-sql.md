---
title: rowversion (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- timestamp_TSQL
- timestamp
dev_langs:
- TSQL
helpviewer_keywords:
- rowversion data type
- size [SQL Server], rowversion
- row version-stamping [SQL Server]
- rowversion columns
- version-stamping table rows
- unique rowversion numbers
- unique timestamp numbers
- timestamp data type
- timestamp columns
- size [SQL Server], timestamp
ms.assetid: 65c9cf0e-3e8a-45f8-87b3-3460d96afb0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c79f2e87ccb6706eab6621cc72bb2fa45b7e9e6
ms.sourcegitcommit: 9bdecafd1aefd388137ff27dfef532a8cb0980be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2020
ms.locfileid: "77179281"
---
# <a name="rowversion-transact-sql"></a>rowversion (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Ein Datentyp, der automatisch generierte eindeutige, binäre Zahlen in einer Datenbank verfügbar macht. **rowversion** wird normalerweise als Mechanismus für die Erstellung einer Versionskennung von Tabellenzeilen verwendet. Die Speichergröße beträgt 8 Byte. Der **rowversion**-Datentyp ist nur eine inkrementelle Nummer und behält ein Datum oder eine Uhrzeit nicht bei. Zum Aufzeichnen eines Datums oder einer Uhrzeit verwenden Sie einen **datetime2**-Datentyp.
  
## <a name="remarks"></a>Bemerkungen  
Jede Datenbank weist einen Zähler auf, der für jeden Einfüge- oder Updatevorgang inkrementiert wird, der für eine Tabelle mit einer **rowversion**-Spalte in der Datenbank ausgeführt wird. Dieser Zähler ist die Datenbankzeilenversion. Hiermit wird ein relativer Zeitpunkt innerhalb einer Datenbank nachverfolgt, keine tatsächliche Zeit, die einer Uhr zugeordnet werden kann. Eine Tabelle kann nur eine **rowversion**-Spalte enthalten. Jedes Mal, wenn eine Zeile mit einer **rowversion**-Spalte geändert oder eingefügt wird, wird der inkrementierte rowversion-Wert der Datenbank in die **rowversion**-Spalte eingefügt. Daher sind **rowversion**-Spalten ungeeignete Kandidaten für Schlüssel, insbesondere für Primärschlüssel. Jedes Update der Zeile ändert den rowversion-Wert und somit auch den Wert des Schlüssels. Wenn die Spalte in einem Primärschlüssel verwendet wird, sind der alte Wert und somit auch alle Fremdschlüssel, die auf den alten Wert verweisen, nicht mehr gültig. Wenn in einem dynamischen Cursor auf die Tabelle verwiesen wird, ändern alle Updates die Position der Zeilen im Cursor. Falls die Spalte in einem Indexschlüssel verwendet wird, generieren alle Updates der Datenzeile auch Updates des Index.  Der **rowversion**-Wert kann mit jeder UPDATE-Anweisung inkrementiert werden, selbst wenn keine Zeilenwerte geändert werden. (Wenn ein Spaltenwert beispielsweise 5 beträgt und eine UPDATE-Anweisung diesen auf 5 festlegt, gilt diese Aktion als Update, obwohl keine Änderung durchgeführt wurde, und **rowversion** wird inkrementiert.)
  
**timestamp** ist das Synonym für den **rowversion**-Datentyp und unterliegt der Verhaltensweise von Datentypsynonymen. Verwenden Sie in DDL-Anweisungen nach Möglichkeit stets **rowversion** anstelle von **timestamp**. Weitere Informationen finden Sie unter [Data Type Synonyms &#40;Transact-SQL&#41; (Synonyme für Datentypen &#40;Transact-SQL&#41;)](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
Der **timestamp**-Datentyp von [!INCLUDE[tsql](../../includes/tsql-md.md)] unterscheidet sich vom **timestamp**-Datentyp, der im ISO-Standard definiert ist.
  
> [!NOTE]  
>  Die **timestamp**-Syntax ist veraltet. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
In einer CREATE TABLE- oder ALTER TABLE-Anweisung müssen Sie keinen Spaltennamen für den **timestamp**-Datentyp angeben:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, timestamp);  
```  
  
Wenn Sie keinen Spaltennamen angeben, generiert [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] den **timestamp**-Spaltennamen. Das **rowversion**-Synonym folgt diesem Verhalten jedoch nicht. Wenn Sie **rowversion** verwenden, müssen Sie einen Spaltennamen angeben:
  
```sql
CREATE TABLE ExampleTable2 (PriKey int PRIMARY KEY, VerCol rowversion) ;  
```  
  
> [!NOTE]  
>  Doppelte **rowversion**-Werte können mithilfe der SELECT INTO-Anweisung generiert werden, bei der eine **rowversion**-Spalte in der SELECT-Liste vorhanden ist. Es wird jedoch nicht empfohlen, **rowversion** auf diese Weise zu verwenden.  
  
Eine **rowversion**-Spalte, die keine NULL-Werte zulässt, ist semantisch gleichwertig mit einer **binary(8)** -Spalte. Eine **rowversion**-Spalte, die NULL-Werte zulässt, ist semantisch gleichwertig mit einer **varbinary(8)** -Spalte.
  
Sie können die **rowversion**-Spalte einer Zeile verwenden, um einfach zu bestimmen, ob für die Zeile seit dem letzten Lesevorgang eine UPDATE-Anweisung ausgeführt wurde. Wenn eine UPDATE-Anweisung für die Zeile ausgeführt wird, wird der rowversion-Wert aktualisiert. Falls keine UPDATE-Anweisung ausgeführt wurde, bleibt der rowversion-Wert wie beim letzten Lesevorgang. Verwenden Sie [@@DBTS](../../t-sql/functions/dbts-transact-sql.md), um den aktuellen rowversion-Wert für eine Datenbank zurückzugeben.
  
Sie können einer Tabelle eine **rowversion**-Spalte hinzufügen, um die Integrität der Datenbank sicherzustellen, wenn mehrere Benutzer gleichzeitig Zeilen aktualisieren. Außerdem können Sie feststellen, wie viele und welche Zeilen aktualisiert wurden, ohne die Tabelle erneut abzufragen.
  
Nehmen Sie z. B. an, Sie erstellen eine Tabelle mit dem Namen `MyTest`. Sie laden einige Daten in die Tabelle, indem Sie die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen ausführen.
  
```sql
CREATE TABLE MyTest (myKey int PRIMARY KEY  
    ,myValue int, RV rowversion);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (2, 0);  
GO  
```  
  
Anschließend können Sie die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Beispielanweisungen verwenden, um während des Updates eine Steuerung durch vollständige Parallelität in der `MyTest`-Tabelle zu implementieren. Das Skript nutzt `<myRv>`, um den **rowversion**-Wert darzustellen, zu dem Sie die Zeile zuletzt gelesen haben. Ersetzen Sie den Wert durch den tatsächlichen **rowversion**-Wert. `0x00000000000007D3` ist ein Beispiel für einen tatsächlichen **rowversion**-Wert.
  
```sql
DECLARE @t TABLE (myKey int);  
UPDATE MyTest  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND RV = <myRv>;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  


Sie können die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Beispielanweisungen auch in einer Transaktion ablegen. Indem Sie die `@t`-Variable im Gültigkeitsbereich der Transaktion abfragen, können Sie die aktualisierte `myKey`-Spalte der Tabelle abrufen, ohne die Tabelle `MyTest` erneut abzufragen.

Im Folgenden wird dasselbe Beispiel mit der **timestamp**-Syntax veranschaulicht. Ersetzen Sie `<myTS>` durch einen tatsächlichem **timestamp**-Wert.

```sql
CREATE TABLE MyTest2 (myKey int PRIMARY KEY  
    ,myValue int, TS timestamp);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (2, 0);  
GO  
DECLARE @t TABLE (myKey int);  
UPDATE MyTest2  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND TS = <myTS>;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
## <a name="see-also"></a>Weitere Informationen
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)  
[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40;Transact-SQL&#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)
  
  
