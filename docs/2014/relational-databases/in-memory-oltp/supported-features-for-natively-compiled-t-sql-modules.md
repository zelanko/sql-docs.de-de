---
title: Unterstützte Konstrukte in systemintern kompilierten gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91434af003bdf783ee4f2bd2c946e4a871eac44d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240851"
---
# <a name="supported-constructs-in-natively-compiled-stored-procedures"></a>Unterstützte Konstrukte in systemintern kompilierten gespeicherten Prozeduren
  Dieses Thema enthält eine Liste der unterstützten Funktionen für systemintern kompilierte gespeicherte Prozeduren ([CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)):  
  
-   [Programmierbarkeit in systemintern kompilierten gespeicherten Prozeduren](#pncsp)  
  
-   [Unterstützte Operatoren](#so)  
  
-   [Integrierte Funktionen in systemintern kompilierten gespeicherten Prozeduren](#bfncsp)  
  
-   [Abfrageoberfläche in systemintern kompilierten gespeicherten Prozeduren](#qsancsp)  
  
-   [Überwachen](#auditing)  
  
-   [Tabelle, Abfrage und Joinhinweise](#tqh)  
  
-   [Einschränkungen bei der Sortierung](#los)  
  
 Informationen über unterstützte Datentypen in systemintern kompilierten gespeicherte Prozeduren, finden Sie unter [Supported Data Types](supported-data-types-for-in-memory-oltp.md).  
  
 Vollständige Informationen zu nicht unterstützten Konstrukten sowie Informationen zu umgehungslösungen zu einigen der nicht unterstützten Funktionen in systemintern kompilierten gespeicherten Prozeduren finden Sie unter [Migrationsprobleme bei systemintern kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md). Weitere Informationen zu nicht unterstützten Funktionen finden Sie unter [Von In-Memory-OLTP nicht unterstützte Transact-SQL-Konstrukte](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
##  <a name="pncsp"></a> Programmierbarkeit in systemintern kompilierten gespeicherten Prozeduren  
 Folgende werden unterstützt:  
  
-   BEGIN ATOMIC (auf der äußeren Ebene der gespeicherten Prozedur), LANGUAGE, ISOLATION LEVEL, DATEFORMAT und DATEFIRST  
  
-   Deklarieren von Variablen als NULL oder NOT NULL Wenn eine Variable als NOT NULL deklariert wird, muss die Deklaration einen Initialisierer haben. Wenn eine Variable nicht als NOT NULL deklariert wird, ist ein Initialisierer optional.  
  
-   IF und WHILE  
  
-   INSERT/UPDATE/DELETE  
  
     Unterabfragen werden nicht unterstützt. In einer WHERE- oder HAVING-Klausel werden AND und BETWEEN unterstützt; OR, NOT und IN werden nicht unterstützt.  
  
-   Speicheroptimierte Tabellentypen und Tabellenvariablen.  
  
-   RETURN  
  
-   SELECT  
  
-   SET  
  
-   TRY/CATCH/THROW  
  
     Um die Leistung zu verbessern, können Sie einen einzelnen TRY/CATCH-Block für eine gesamte systemintern kompilierte gespeicherte Prozedur verwenden.  
  
##  <a name="so"></a> Unterstützte Operatoren  
 Die folgenden Operatoren werden unterstützt.  
  
-   [Vergleichsoperatoren &#40;Transact-SQL&#41; ](/sql/t-sql/language-elements/comparison-operators-transact-sql) (z. B. >, \<, > = und < =) werden in Bedingungen unterstützt (IF, während).  
  
-   Unäre Operatoren (+, -)  
  
-   Binäre Operatoren (*, /, +, -, % (Modulo)).  
  
     Der Plusoperator (+) wird in Zahlen und Zeichenfolgen unterstützt.  
  
-   Logische Operatoren (AND, OR, NOT). OR und NOT werden in IF- und WHILE-Anweisungen, aber nicht in WHERE- oder HAVING-Klauseln unterstützt.  
  
-   Bitweise Operatoren ~, &, |, und ^  
  
##  <a name="bfncsp"></a> Integrierte Funktionen in systemintern kompilierten gespeicherten Prozeduren  
 Die folgenden Funktionen werden in Standardeinschränkungen in speicheroptimierten Tabellen und in systemintern kompilierten gespeicherte Prozeduren unterstützt.  
  
-   Mathematische Funktionen: ARCCOS, ARCSIN, ARCTAN, ATN2, COS, COT, GRAD, EXP, LOG, LOG10, PI, POTENZ, BOGENMASS, ZUFALLSZAHL, SIN, WURZEL, QUADRAT und TAN  
  
-   Datumsfunktionen: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME und YEAR.  
  
-   Zeichenfolgenfunktionen: LEN, LTRIM, RTRIM und SUBSTRING  
  
-   Identitätsfunktionen: SCOPE_IDENTITY  
  
-   NULL-Funktionen: ISNULL  
  
-   Uniqueidentifier-Funktionen: NEWID und NEWSEQUENTIALID  
  
-   Fehlerfunktionen: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY und ERROR_STATE  
  
-   Konvertierungen: CAST und CONVERT. Konvertierungen zwischen Unicode- und Nicht-Unicode-Zeichenfolgen (n(var)char und (var)char) werden nicht unterstützt.  
  
-   Systemfunktionen: @@rowcount. Durch Anweisungen in nativ kompilierten gespeicherten Prozeduren wird @@rowcount aktualisiert, und Sie können @@rowcount in einer nativ kompilierten gespeicherten Prozedur verwenden, um die Anzahl der Zeilen zu bestimmen, die von der letzten Anweisung betroffen sind, die innerhalb der nativ kompilierten gespeicherten Prozedur ausgeführt wurde. Allerdings wird @@rowcount am Anfang und am Ende der Ausführung einer nativ kompilierten gespeicherten Prozedur auf 0 zurückgesetzt.  
  
##  <a name="qsancsp"></a> Abfrageoberfläche in systemintern kompilierten gespeicherten Prozeduren  
 Folgende werden unterstützt:  
  
-   BETWEEN  
  
-   Aliase für Spaltennamen (entweder mithilfe von AS oder = Syntax)  
  
-   CROSS JOIN und INNER JOIN werden nur bei SELECT-Abfragen unterstützt.  
  
-   Ausdrücke werden in SELECT-Liste unterstützt und [, in denen &#40;Transact-SQL&#41; ](/sql/t-sql/queries/where-transact-sql) -Klausel, wenn sie einen unterstützten Operatoren verwenden. Unter [Unterstützte Operatoren](#so) finden Sie eine Liste der zurzeit unterstützten Operatoren.  
  
-   Filterprädikat IS [NOT] NULL  
  
-   VON \<Speicheroptimierte Tabelle >  
  
-   [GROUP BY &#40;Transact-SQL&#41; ](/sql/t-sql/queries/select-group-by-transact-sql) wird unterstützt, sowie die Aggregatfunktionen AVG, COUNT, COUNT_BIG, MIN, MAX und SUM. MIN und MAX werden für die Typen nvarchar, char, varchar, varchar, vabinary und binary nicht unterstützt. [ORDER BY-Klausel &#40;Transact-SQL&#41; ](/sql/t-sql/queries/select-order-by-clause-transact-sql) unterstützt, auf denen [GROUP BY &#40;Transact-SQL&#41; ](/sql/t-sql/queries/select-group-by-transact-sql) , wenn ein Ausdruck in der ORDER BY-Liste wörtlich in der GROUP BY-Liste angezeigt wird. Beispielsweise wird GROUP BY a + b ORDER BY a + b unterstützt, aber GROUP BY a, b ORDER BY a + b nicht.  
  
-   HAVING unterliegt den gleichen Ausdruckseinschränkungen wie die WHERE-Klausel.  
  
-   INSERT VALUES (eine Zeile pro Anweisung) und INSERT SELECT  
  
-   SORTIERT NACH DEM <sup>1</sup>  
  
-   Prädikate, die nicht auf eine Spalte verweisen.  
  
-   SELECT, UPDATE und DELETE  
  
-   TOP <sup>1</sup>  
  
-   Variablenzuweisung in der SELECT-Liste  
  
-   WHERE... AND  
  
 <sup>1</sup> ORDER BY und TOP werden in systemintern kompilierten gespeicherten Prozeduren mit einigen Einschränkungen unterstützt:  
  
-   Es gibt keine Unterstützung für `DISTINCT` in die `SELECT` oder `ORDER BY` Klausel.  
  
-   Die `WITH TIES`-Klausel bietet keine Unterstützung für `PERCENT` oder `TOP`.  
  
-   `TOP` in Kombination mit `ORDER BY` unterstützt höchstens den Wert 8.192 bei Verwendung einer Konstante in der `TOP` Klausel. Dieser Grenzwert kann herabgesetzt werden, wenn die Abfrage Joins oder Aggregatfunktionen enthält. (Beispielsweise liegt die Beschränkung bei einem Join mit zwei Tabellen bei 4.096 Zeilen. Bei zwei Joins mit drei Tabellen lautet der Grenzwert 2.730 Zeilen).  
  
     Sie können Ergebnisse erhalten, die größer als 8.192 sind, indem Sie die Anzahl von Zeilen in einer Variablen speichern:  
  
    ```tsql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) … FROM … ORDER BY …  
    ```  
  
 Eine Konstante in der `TOP`-Klausel führt jedoch im Vergleich zur Verwendung einer Variablen zu einer besseren Leistung.  
  
 Diese Einschränkungen gelten nicht für den interpretierten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Zugriff auf Speicheroptimierte Tabellen.  
  
##  <a name="auditing"></a> Überwachen  
 Überwachung auf Prozedurebene wird für systemintern kompilierte gespeicherte Prozeduren unterstützt. Überwachung auf Anweisungsebene wird nicht unterstützt.  
  
 Weitere Informationen zur Überwachung finden Sie unter [Create a Server Audit and Database Audit Specification](../security/auditing/create-a-server-audit-and-database-audit-specification.md).  
  
##  <a name="tqh"></a> Tabelle, Abfrage und Joinhinweise  
 Folgende werden unterstützt:  
  
-   INDEX-, FORCESCAN- und FORCESEEK-Hinweise, entweder in der Tabellenhinweissyntax oder in der [OPTION-Klausel &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) der Abfrage.  
  
-   FORCE ORDER  
  
-   INNER LOOP JOIN  
  
-   OPTIMIZE FOR  
  
 Weitere Informationen finden Sie unter [Hinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql).  
  
##  <a name="los"></a> Einschränkungen bei der Sortierung  
 Sie können mehr als 8.000 Zeilen in einer Abfrage sortieren, die [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) und eine [ORDER BY-Klausel &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) verwendet. Ohne die [ORDER BY-Klausel &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) kann [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) eine Sortierung von bis zu 8.000 Zeilen durchführen (weniger Zeilen, falls es Verknüpfungen gibt).  
  
 Wenn die Abfrage jeweils den Operator [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) und eine [ORDER BY-Klausel &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) verwendet, können Sie bis zu 8192 Zeilen für den TOP-Operator angeben. Wenn Sie mehr als 8192 Zeilen angeben, wird die Fehlermeldung angezeigt: **Msg 41398, Level 16, State 1, Procedure *\<ProzedurName>*, Line *\<ZeilenNummer>* Der Operator TOP kann maximal 8192 Zeilen zurückgeben; *\<Zahl>* wurde angefordert.**  
  
 Wenn keine TOP-Klausel vorhanden ist, kann eine beliebige Anzahl von Zeilen mit ORDER BY sortiert werden.  
  
 Wenn keine ORDER BY-Klausel verwendet wird, können Sie jeden ganzzahligen Wert mit dem TOP-Operator verwenden.  
  
 Beispiel mit TOP N = 8192: Wird kompiliert  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 Beispiel mit TOP N > 8192: Kann nicht kompiliert werden  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 Die Einschränkung auf 8192 Zeilen gilt nur für `TOP N` , wobei `N` wie in den Beispielen oben eine Konstante ist.  Wenn `N` größer als 8192 sein muss, können Sie den Wert einer Variablen zuweisen und die Variable mit `TOP`verwenden.  
  
 Beispiel mit einer Variablen: Wird kompiliert  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 **Einschränkungen für zurückgegebene Zeilen:** Es gibt zwei Fälle, in denen sich die Anzahl der Zeilen, die vom TOP-Operator zurückgegeben werden können, u. U. verringert:  
  
-   Verwenden von JOINs in der Abfrage  Die Auswirkungen von JOINs auf die Einschränkung sind vom Abfrageplan abhängig.  
  
-   Verwenden von Aggregatfunktionen oder Verweisen auf Aggregatfunktionen in der ORDER BY-Klausel  
  
 Die Formel zum Berechnen eines im ungünstigsten Fall unterstützten Maximalwerts für N in TOP N lautet wie folgt: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.  
  
## <a name="see-also"></a>Siehe auch  
 [Nativ kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)   
 [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
