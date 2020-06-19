---
title: Sortierungen und Codepages | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c626dcac-0474-432d-acc0-cfa643345372
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96eea051fbf4a34257d61ff8eaf4f796debf49a6
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936011"
---
# <a name="collations-and-code-pages"></a>Sortierungen und Codepages
  [!INCLUDE[hek_2](../includes/hek-2-md.md)] weist Einschränkungen bei unterstützten Codepages für (var)char-Spalten in speicheroptimierten Tabellen und unterstützten Sortierungen auf, die in Indizes und in systemintern kompilierten gespeicherten Prozeduren verwendet werden.  
  
 Die Codepage für einen (var)char-Wert bestimmt die Zuordnung zwischen Zeichen und der Bytedarstellung, die in der Tabelle gespeichert ist. So entspricht z. B. bei der Windows Latin 1-Codepage (1252; der[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Standard) das Zeichen „a“ dem Byte 0x61.  
  
 Die Codepage eines (var)char-Werts wird durch die Sortierung bestimmt, die dem Wert zugeordnet ist. So hat die Sortierung SQL_Latin1_General_CP1_CI_AS beispielsweise die zugeordnete Codepage 1252.  
  
 Die Sortierung eines Werts wird entweder von der Datenbanksortierung geerbt oder kann mithilfe des COLLATE-Schlüsselworts explizit angegeben werden. Die Datenbanksortierung kann nicht geändert werden, wenn die Datenbank speicheroptimierte Tabellen oder systemintern kompilierte gespeicherte Prozeduren enthält. Im folgenden Beispiel wird die Datenbanksortierung festgelegt und eine Tabelle erstellt, die eine Spalte mit einer anderen Sortierung hat. Die Datenbank verwendet die Latin-Sortierung, bei der die Groß-/Kleinschreibung beachtet wird.  
  
 Indizes können nur für Zeichenfolgenspalten erstellt werden, wenn sie eine BIN2-Sortierung verwenden. Die LastName-Variable verwendet BIN2-Sortierung. FirstName verwendet den Datenbankstandardwert, der CI_AS (Unterscheidung nach Groß-/Kleinschreibung, Unterscheidung nach Akzent) ist.  
  
> [!IMPORTANT]  
>  ORDER BY oder GROUP BY kann nicht für Spalten mit Indexzeichenfolgen verwendet werden, die keine BIN2-Sortierung aufweisen.  
  
```sql  
CREATE DATABASE IMOLTP  
  
ALTER DATABASE IMOLTP ADD FILEGROUP IMOLTP_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP ADD FILE( NAME = 'IMOLTP_mod' , FILENAME = 'c:\data\IMOLTP_mod') TO FILEGROUP IMOLTP_mod;  
--GO  
  
--  set the database collations  
ALTER DATABASE IMOLTP COLLATE Latin1_General_100_CI_AS  
GO  
  
--  
USE IMOLTP   
GO  
  
-- create a table with collation  
CREATE TABLE Employees (  
  EmployeeID int NOT NULL ,   
  LastName nvarchar(20) COLLATE Latin1_General_100_BIN2 NOT NULL INDEX IX_LastName NONCLUSTERED,   
  FirstName nvarchar(10) NOT NULL ,  
  CONSTRAINT PK_Employees PRIMARY KEY NONCLUSTERED HASH(EmployeeID)  WITH (BUCKET_COUNT=1024)  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_AND_DATA)  
GO  
```  
  
 Die folgenden Einschränkungen gelten für speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren:  
  
-   (var)char-Spalten in speicheroptimierten Tabellen müssen die Sortierung der Codepage 1252 verwenden. Diese Einschränkung gilt nicht für n(var)char-Spalten. Der folgende Code ruft alle 1252-Sortierungen ab:  
  
    ```sql  
    -- all supported collations for (var)char columns in memory-optimized tables  
    select * from sys.fn_helpcollations()  
    where collationproperty(name, 'codepage') = 1252;  
    ```  
  
     Wenn Sie nicht-lateinischen Zeichen speichern müssen, verwenden Sie n(var)char-Spalten.  
  
-   Indizes für (n)(var)char-Spalten können nur mit BIN2-Sortierungen angegeben werden (siehe erstes Beispiel). Die folgende Abfrage ruft alle unterstützten BIN2-Sortierungen ab:  
  
    ```sql  
    -- all supported collations for indexes on memory-optimized tables and   
    -- comparison/sorting in natively compiled stored procedures  
    select * from sys.fn_helpcollations() where name like '%BIN2'  
    ```  
  
     Wenn Sie über interpretiertes [!INCLUDE[tsql](../includes/tsql-md.md)] auf die Tabelle zugreifen, können Sie das `COLLATE`-Schlüsselwort verwenden, um die Sortierung mit Ausdrücken oder Sortiervorgängen zu ändern. Siehe das letzte Beispiel.  
  
-   Systemintern kompilierte gespeicherte Prozeduren können Parameter, lokale Variablen oder Zeichenfolgenkonstanten vom Typ (var)char nicht verwenden, wenn die Datenbanksortierung keine Sortierung der Codepage 1252 ist.  
  
-   Alle Ausdrücke und Sortiervorgänge in systemintern kompilierten gespeicherten Prozeduren müssen BIN2-Sortierungen verwenden. Es wird impliziert, dass alle Vergleiche und Sortiervorgänge auf den Unicode-Codepunkten der Zeichen (binäre Darstellung) basieren. Beispielsweise wird bei allen Sortierungen nach Groß-/Kleinschreibung unterschieden ("Z" kommt vor "a"). Bei Bedarf kann für Sortierungen und Vergleiche ohne Beachtung der Groß-/Kleinschreibung interpretiertes [!INCLUDE[tsql](../includes/tsql-md.md)] verwendet werden.  
  
-   Abschneiden von UTF-16-Daten wird in systemintern kompilierten gespeicherten Prozeduren nicht unterstützt. Dies bedeutet, dass n (var) char (*n*)-Werte nicht in den Typ n (var) char (*i*) konvertiert werden können *, wenn*  <  *n*die Sortierung über _SC Eigenschaft verfügt. Beispielsweise wird Folgendes nicht unterstützt:  
  
    ```sql  
    -- column definition using an _SC collation  
     c2 nvarchar(200) collate Latin1_General_100_CS_AS_SC not null   
    -- assignment to a smaller variable, requiring truncation  
     declare @c2 nvarchar(100) = '';  
     select @c2 = c2  
    ```  
  
     Funktionen zur Zeichenfolgenmanipulation wie LEN, SUBSTRING, LTRIM und RTRIM mit UTF-16-Daten werden in systemintern kompilierten gespeicherten Prozeduren nicht unterstützt. Sie können diese Funktionen zur Zeichenfolgenmanipulation für n(var)char-Werte mit _SC-Sortierung nicht verwenden.  
  
     Deklarieren Sie Variablen mit Typen, die ausreichend groß sind, sodass ein Abschneiden vermieden wird.  
  
 Im folgenden Beispiel werden einige der Auswirkungen und Problemumgehungen zu Sortierungseinschränkungen in In-Memory OLTP gezeigt. Im Beispiel wird die oben angegebene Mitarbeitertabelle verwendet. In diesem Beispiel werden alle Mitarbeiter aufgeführt. Beachten Sie, dass aufgrund der binären Sortierung bei LastName die groß geschriebenen Namen vor die klein geschriebenen sortiert werden. Daher kommt "Thomas" vor "nolan", da Großbuchstaben niedrigere Codepunkte haben. FirstName hat eine Sortierung, bei der die Groß-/Kleinschreibung beachtet wird. Daher erfolgt die Sortierung nach Buchstabe des Alphabets, nicht nach Codepunkt der Zeichen.  
  
```sql  
-- insert a number of values  
INSERT Employees VALUES (1,'thomas', 'john')  
INSERT Employees VALUES (2,'Thomas', 'rupert')  
INSERT Employees VALUES (3,'Thomas', 'Jack')  
INSERT Employees VALUES (4,'Thomas', 'annie')  
INSERT Employees VALUES (5,'nolan', 'John')  
GO  
  
-- ===========  
SELECT EmployeeID, LastName, FirstName FROM Employees  
ORDER BY LastName, FirstName  
GO  
  
-- ===========  
-- specify collation: sorting uses case-insensitive collation, thus 'nolan' comes before 'Thomas'  
SELECT * FROM Employees  
ORDER BY LastName COLLATE Latin1_General_100_CI_AS, FirstName  
GO  
  
-- ===========  
-- retrieve employee by Name  
-- must use BIN2 collation for comparison in natively compiled stored procedures  
CREATE PROCEDURE usp_EmployeeByName @LastName nvarchar(20), @FirstName nvarchar(10)  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = N'us_english'  
)  
  SELECT EmployeeID, LastName, FirstName FROM dbo.Employees  
  WHERE   
    LastName = @LastName AND  
    FirstName COLLATE Latin1_General_100_BIN2 = @FirstName  
  
END  
GO  
  
-- this does not return any rows, as EmployeeID 1 has first name 'john', which is not equal to 'John' in a binary collation  
EXEC usp_EmployeeByName 'thomas', 'John'  
  
-- this retrieves EmployeeID 1  
EXEC usp_EmployeeByName 'thomas', 'john'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
