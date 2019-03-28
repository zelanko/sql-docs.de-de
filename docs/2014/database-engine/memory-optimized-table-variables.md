---
title: Speicheroptimierte Tabellenvariablen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: bd102e95-53e2-4da6-9b8b-0e4f02d286d3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 485f481819a9712f822f969c04d8e7050ad43bae
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530742"
---
# <a name="memory-optimized-table-variables"></a>Speicheroptimierte Tabellenvariablen
  Zusätzlich zu speicheroptimierten Tabellen (für den effizienten Datenzugriff) und nativ kompilierten gespeicherten Prozeduren (für effiziente Abfrageverarbeitung und Ausführung von Geschäftslogik) wird mit [!INCLUDE[hek_2](../includes/hek-2-md.md)] eine dritte Objektart eingeführt: speicheroptimierte Tabellentypen. Eine Tabellenvariable, die mithilfe eines speicheroptimierten Tabellentyps erstellt wird, ist eine speicheroptimierte Tabellenvariable.  
  
 Speicheroptimierte Tabellenvariablen bieten im Vergleich zu datenträgerbasierten Tabellenvariablen die folgenden Vorteile:  
  
-   Die Variablen werden nur im Arbeitsspeicher gespeichert. Die Datenzugriffe sind effizienter, da für speicheroptimierte Tabellentypen derselbe speicheroptimierte Algorithmus und dieselben Datenstrukturen verwendet werden wie für speicheroptimierte Tabellen, insbesondere wenn die Variablen in systemintern kompilierten gespeicherten Prozeduren verwendet werden.  
  
-   Bei speicheroptimierten Tabellenvariablen findet keine tempdb-Nutzung statt. Tabellenvariablen werden nicht in tempdb gespeichert und verwenden keine Ressourcen in tempdb.  
  
 Typische Verwendungsszenarien für speicheroptimierte Tabellenvariablen sind:  
  
-   Speichern von Zwischenergebnissen und Erstellen von einzelnen Resultsets, die auf mehreren Abfragen basieren, in systemintern kompilierten gespeicherten Prozeduren.  
  
-   Übergeben von Tabellenwertparametern an systemintern kompilierte gespeicherte Prozeduren und an interpretierte gespeicherte Prozeduren.  
  
-   Ersetzen datenträgerbasierter Tabellenvariablen und in einigen Fällen von lokalen #temp-Tabellen einer gespeicherten Prozedur. Dies ist besonders dann nützlich, wenn im System viele tempdb-Konflikte auftreten.  
  
-   Tabellenvariablen können zum Simulieren von Cursorn in systemintern kompilierten gespeicherten Prozeduren verwendet werden, um Einschränkungen der Oberfläche in systemintern kompilierten gespeicherten Prozeduren zu umgehen.  
  
 Wie bei speicheroptimierten Tabellen erstellt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine DLL für jeden speicheroptimierten Tabellentyp. (Die Kompilierung wird aufgerufen, wenn der speicheroptimierte Tabellentyp erstellt wird und nicht, wenn er zum Erstellen von speicheroptimierten Tabellenvariablen verwendet wird.) Diese DLL beinhaltet die Funktionen für den Zugriff auf Indizes und das Abrufen von Daten aus den Tabellenvariablen. Wenn eine speicheroptimierte Tabellenvariable basierend auf dem Tabellentyp deklariert wird, wird in der Benutzersitzung eine Instanz der Tabelle und der Indexstrukturen entsprechend dem Tabellentyp erstellt. Die Tabellenvariable kann anschließend auf dieselbe Weise wie datenträgerbasierte Tabellenvariablen verwendet werden. Sie können in der Tabellenvariablen Zeilen einfügen, aktualisieren und löschen, und Sie können die Variablen in [!INCLUDE[tsql](../includes/tsql-md.md)] -Abfragen verwenden. Sie können die Variablen auch als Tabellenwertparameter (TVPs) an systemintern kompilierte und interpretierte gespeicherte Prozeduren übergeben.  
  
 Das folgende Beispiel zeigt einen speicheroptimierten Tabellentyp aus dem AdventureWorks-basierten In-Memory-OLTP-Beispiel ([Beispiel zu SQL Server 2014 In-Memory OLTP](https://msftdbprodsamples.codeplex.com/releases/view/114491)).  
  
```sql
CREATE TYPE Sales.SalesOrderDetailType_inmem
   AS TABLE
(
   OrderQty         smallint   NOT NULL,
   ProductID        int        NOT NULL,

   SpecialOfferID   int        NOT NULL
      INDEX  IX_SpecialOfferID  NONCLUSTERED,

   LocalID          int        NOT NULL,

   INDEX IX_ProductID HASH (ProductID)
      WITH ( BUCKET_COUNT = 8 )
)
WITH ( MEMORY_OPTIMIZED = ON );
```  
  
 Das Beispiel zeigt, dass die Syntax von speicheroptimierten Tabellentypen der von datenträgerbasierten Tabellentypen ähnelt, mit folgenden Ausnahmen:  
  
-   `MEMORY_OPTIMIZED=ON` gibt an, dass der Tabellentyp speicheroptimiert ist.  
  
-   Der Typ muss mindestens einen Index aufweisen. Wie bei speicheroptimierten Tabellen können Sie nicht gruppierte und Hashindizes verwenden.  
  
     Für einen Hashindex sollte die Bucketanzahl etwa einmal bis zweimal so groß sein wie die Anzahl der erwarteten eindeutigen Indexschlüssel. Weitere Informationen finden Sie unter [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).  
  
-   Der Datentypbeschränkungen und die Einschränkungen für speicheroptimierte Tabellen gelten auch für speicheroptimierte Tabellentypen. Beispielsweise werden Standardeinschränkungen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] unterstützt, Check-Einschränkungen jedoch nicht.  
  
 Speicheroptimierte Tabellenvariablen verhalten sich in folgenden Fällen wie speicheroptimierte Tabellen:  
  
-   Sie unterstützen keine parallelen Pläne.  
  
-   Sie müssen in den Arbeitsspeicher passen und nutzen keine Datenträgerressourcen.  
  
 Datenträgerbasierte Tabellenvariablen werden in tempdb gespeichert. Speicheroptimierte Tabellenvariablen werden in der Benutzerdatenbank gespeichert. (Sie belegen aber keinen Speicherplatz und werden nicht wiederhergestellt.)  
  
 Eine speicheroptimierte Tabellenvariable kann nicht mithilfe von Inlinesyntax erstellt werden. Im Gegensatz zu datenträgerbasierten Tabellenvariablen müssen Sie zuerst einen Typ erstellen.  
  
## <a name="table-valued-parameters"></a>Tabellenwertparameter  
 Im folgenden Beispielskript wird die Deklaration einer Tabellenvariablen als speicheroptimierter Tabellentyp `Sales.SalesOrderDetailType_inmem`, das Einfügen von drei Zeilen in die Variable und das Übergeben der Variablen als TVP an `Sales.usp_InsertSalesOrder_inmem` gezeigt.  
  
```sql  
DECLARE @od Sales.SalesOrderDetailType_inmem,  
  @SalesOrderID uniqueidentifier,  
  @DueDate datetime2 = SYSDATETIME()  
  
INSERT @od (LocalID, ProductID, OrderQty, SpecialOfferID) VALUES  
  (1, 888, 2, 1),  
  (2, 450, 13, 1),  
  (3, 841, 1, 1)  
  
EXEC Sales.usp_InsertSalesOrder_inmem  
  @SalesOrderID = @SalesOrderID,  
  @DueDate = @DueDate,  
 @OnlineOrderFlag = 1,  
  @SalesOrderDetails = @od  
```  
  
 Speicheroptimierte Tabellentypen können als Typ für Tabellenwertparameter (TVPs) von gespeicherten Prozeduren verwendet werden. Clients können genauso darauf verweisen wie auf datenträgerbasierte Tabellentypen und TVPs. Daher funktioniert der Aufruf gespeicherter Prozeduren mit speicheroptimierten TVPs und systemintern kompilierter gespeicherter Prozeduren genauso wie der Aufruf interpretierter gespeicherter Prozeduren mit datenträgerbasierten TVPs.  
  
## <a name="temp-table-replacement"></a>Ersatz für #temp-Tabellen  
 Im folgenden Beispiel werden speicheroptimierte Tabellentypen und Tabellenvariablen als Ersatz für lokale #temp-Tabellen einer gespeicherten Prozedur verwendet.  
  
```sql  
-- Using SQL procedure and temp table  
CREATE TABLE #tempTable (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
  
CREATE PROCEDURE sqlProc  
AS  
BEGIN  
  TRUNCATE TABLE #tempTable  
  
  INSERT #tempTable VALUES (1)  
  INSERT #tempTable VALUES (2)  
  INSERT #tempTable VALUES (3)  
  SELECT * FROM #tempTable  
END  
GO  
  
-- Using natively compiled stored procedure and table variable  
CREATE TYPE TT AS TABLE (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
GO  
  
CREATE PROCEDURE NCSPProc  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @tableVariable TT  
  INSERT @tableVariable VALUES (1)  
  INSERT @tableVariable VALUES (2)  
  INSERT @tableVariable VALUES (3)  
  SELECT c FROM @tableVariable  
END  
GO  
```  
  
## <a name="creating-a-single-result-set"></a>Erstellen eines einzelnen Resultsets  
 Im folgenden Beispiel wird gezeigt, wie Zwischenergebnisse gespeichert und einzelne Resultsets basierend auf mehreren Abfragen in systemintern kompilierten gespeicherten Prozeduren erstellt werden. Im Beispiel wird die Vereinigung `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2` berechnet.  
  
```sql  
CREATE DATABASE hk  
GO  
ALTER DATABASE hk ADD FILEGROUP hk_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE hk ADD FILE( NAME = 'hk_mod' , FILENAME = 'c:\data\hk_mod') TO FILEGROUP hk_mod;  
  
USE hk  
GO  
  
CREATE TYPE tab1 AS TABLE (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON)  
  
CREATE TABLE dbo.t1 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
CREATE TABLE dbo.t2 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
  
INSERT INTO dbo.t1 VALUES (1), (2)  
INSERT INTO dbo.t2 VALUES (3), (4)  
GO  
  
CREATE PROCEDURE dbo.p1  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS  
  BEGIN ATOMIC WITH ( TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english' )  
  
    DECLARE @t dbo.tab1  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t1;  
  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t2;  
  
    SELECT c1 FROM @t;  
  END  
GO  
  
EXEC dbo.p1  
GO  
```  
  
## <a name="memory-consumption-for-table-variables"></a>Arbeitsspeichernutzung für Tabellenvariablen  
 Die Arbeitsspeichernutzung für Tabellenvariablen ist mit Ausnahme von nicht gruppierten Indizes mit der Nutzung speicheroptimierter Tabellen vergleichbar. Wenn Sie viele Zeilen in speicheroptimierte Tabellenvariablen mit nicht gruppierten Indizes einfügen und die Indexschlüssel groß sind, beanspruchen diese Tabellenvariablen eine unverhältnismäßig große Speichermenge. Nicht gruppierte Indizes für große Tabellenvariablen erfordern proportional mehr Arbeitsspeicher, als ein nicht gruppierter Index für dieselbe Anzahl von Zeilen, die in eine Tabelle eingefügt wurden, benötigen würde (mehr Speicherplatz in Indexseiten).  
  
 Arbeitsspeicher für Tabellenvariablen wird aus dem Ressourcenpool der für die Datenbank zuständigen Ressourcenkontrolle entnommen.  
  
 Im Gegensatz zu speicheroptimierten Tabellen wird der von Tabellenvariablen genutzte Arbeitsspeicher (einschließlich gelöschter Zeilen) freigegeben, wenn die Tabellenvariable den Gültigkeitsbereich verlässt.  
  
 Arbeitsspeicher wird als Teil des einzelnen PGPOOL-Arbeitsspeicherconsumers der Datenbank behandelt.  
  
## <a name="see-also"></a>Siehe auch  
 [Transact-SQL-Unterstützung für In-Memory-OLTP](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
