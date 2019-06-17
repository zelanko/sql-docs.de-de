---
title: Implementieren des OR-Operator in systemintern kompilierten gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2528e74-2b1c-48cb-861b-c4e57b51ac35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 64de082cd12c967f3f3c90ca3cb99c51985ed41a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62778911"
---
# <a name="implementing-the-or-operator-in-natively-compiled-stored-procedures"></a>Implementieren des OR-Operators in systemintern kompilierten gespeicherten Prozeduren
  OR-Operatoren werden in Abfrageprädikaten systemintern kompilierter gespeicherter Prozeduren nicht unterstützt. Da NOT-Operatoren in Abfrageprädikaten systemintern kompilierter gespeicherter Prozeduren ebenfalls nicht unterstützt werden, können die Auswirkungen der OR-Operatoren nicht allein durch Verwendung der entsprechenden logischen Operatoren simuliert werden. Die Auswirkungen eines OR-Operators können jedoch anhand von speicheroptimierten Tabellenvariablen simuliert werden.  
  
## <a name="or-operator-in-where-clause"></a>OR-Operator in einer WHERE-Klausel  
 Wenn Sie über einen OR-Operator in einer WHERE-Klausel verfügen, können Sie dessen Verhalten auf die folgende Weise simulieren:  
  
1.  Erstellen Sie eine speicheroptimierte Tabellenvariable mit dem entsprechenden Schema. Dies erfordert einen vordefinierten speicheroptimierten Tabellentyp.  
  
2.  Unterteilen Sie die WHERE-Klausel ab dem OR-Operator der obersten Ebene in zwei Teile. Dabei richten Sie sich nach den vom OR-Operator verknüpften Prädikaten. Wenn Sie über mehr als einen OR-Operator in einer WHERE-Klausel verfügen, müssen Sie diesen Vorgang möglicherweise mehrere Male wiederholen. Wiederholen Sie diesen Schritt, bis keine OR-Operatoren mehr übrig sind. Angenommen, Sie verfügen über das folgende Prädikat:  
  
    ```  
    pred1 OR (pred2 AND (pred3 OR pred4)) OR (pred5 AND pred6)  
    ```  
  
     Nach diesem Schritt sollten Sie über die folgenden Prädikate verfügen:  
  
    ```  
    pred1  
    pred5 AND pred6  
    pred2 AND pred3  
    pred2 AND pred4  
    ```  
  
3.  Führen Sie eine Abfrage mit jedem der beiden Teile aus, die in Schritt 2 als Prädikat angegeben werden. Fügen Sie das Ergebnis für jede Abfrage in die unter Schritt 1 erstellte speicheroptimierte Tabellenvariable ein.  
  
4.  Entfernen Sie ggf. Duplikate aus der speicheroptimierten Tabellenvariablen.  
  
5.  Verwenden Sie den Inhalt der speicheroptimierten Tabellenvariablen als Ergebnis der Abfrage.  
  
 Im folgenden Beispiel werden Tabellen aus der AdventureWorks2012-Datenbank verwendet, die für [!INCLUDE[hek_2](../includes/hek-2-md.md)]aktualisiert wurden. Zum Herunterladen der Dateien in diesem Beispiel "GoTo" [AdventureWorks-Datenbanken – 2012, 2008R2 und 2008](http://msftdbprodsamples.codeplex.com/releases/view/93587). Um das [!INCLUDE[hek_2](../includes/hek-2-md.md)] -Codebeispiel auf AdventureWorks2012 anzuwenden, rufen Sie [Beispiel zu SQL Server 2014 In-Memory OLTP](https://msftdbprodsamples.codeplex.com/releases/view/114491)auf.  
  
 Fügen Sie der Datenbank die folgende gespeicherte Prozedur hinzu. Diese gespeicherte Prozedur wird konvertiert, sodass sie die systeminterne Kompilierung verwendet.  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_ondisk  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
AS BEGIN  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  WHERE  s.SalesOrderId = @SalesOrderId  
      OR s.SalesOrderDetailId = @SalesOrderDetailId  
      OR s.CarrierTrackingNumber = @CarrierTrackingNumber  
      OR s.ProductID = @ProductId  
      OR (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
END  
GO  
```  
  
 Nach der Konvertierung erhalten Sie folgendes Schema für die Tabelle und die gespeicherte Prozedur:  
  
```  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesOrderDetailType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailTempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  recordcount int not null  
  INDEX ix_fuzzySearchSalesOrderDetailTempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_inmem  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.fuzzySearchSalesOrderDetailType  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderId = @SalesOrderId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderDetailId = @SalesOrderDetailId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.CarrierTrackingNumber COLLATE Latin1_General_BIN2 = @CarrierTrackingNumber COLLATE Latin1_General_BIN2   
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.ProductID = @ProductId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
  
  -- After the above statements, there will be duplicates inside @retValue  
  -- Delete the duplicates from @retValue  
  DECLARE @duplicates Sales.fuzzySearchSalesOrderDetailTempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, recordcount)   
  SELECT SalesOrderId, SalesOrderDetailId, COUNT(*) AS recordCount  
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId  
  
  -- Now we have one row per pair  
  -- clear and rebuild the result set  
  DELETE FROM @retValue  
  
  INSERT INTO @retValue  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates d ON s.SalesOrderId = d.SalesOrderId AND s.SalesOrderDetailId = d.SalesOrderDetailId  
  
  -- After this every pair of (SalesOrderId, SalesOrderDetailId) in @retValue should be unique.  
  SELECT SalesorderId, SalesOrderDetailId, ModifiedDate FROM @retValue  
END  
GO  
```  
  
## <a name="or-operator-in-join-condition"></a>OR-Operator in einer JOIN-Bedingung  
 Wenn Sie über einen OR-Operator in einer JOIN-Bedingung einer SELECT-Anweisung verfügen, können Sie dessen Verhalten auf die folgende Weise simulieren. Wenn Sie über mehr als einen OR-Operator in einer JOIN-Bedingung bzw. über mehrere JOIN-Bedingungen bei OR-Operatoren verfügen, müssen Sie diesen Schritt ggf. mehrere Male ausführen.  
  
 Wenn Sie über OUTER JOIN-Bedingungen verfügen, können Sie diese Umgehungslösung mit der Umgehungslösung für OUTER JOIN-Bedingungen kombinieren.  
  
1.  Erstellen Sie eine speicheroptimierte Tabellenvariable mit dem entsprechenden Schema. Dies erfordert einen vordefinierten speicheroptimierten Tabellentyp.  
  
2.  Unterteilen Sie das Prädikat in der JOIN-Bedingung in zwei Teile. Dabei richten Sie sich nach den durch den OR-Operator verknüpften Prädikaten. Wenn Sie über mehrere JOIN-Bedingungen verfügen, müssen Sie diesen Schritt u. U. für jede JOIN-Bedingung ausführen und die resultierenden Fragmente dann auf verschiedene Weisen kombinieren. Wenn Sie beispielsweise über drei JOIN-Bedingungen mit einem OR-Operator pro JOIN-Bedingung verfügen, haben Sie möglicherweise 2x2x2=8 Prädikate.  
  
3.  Erstellen Sie für jedes unter Schritt 2 erstellte Prädikat eine Abfrage, durch die das Ergebnis in die unter Schritt 1 erstellte speicheroptimierte Tabellenvariable eingefügt wird.  
  
4.  Entfernen Sie ggf. Duplikate aus der speicheroptimierten Tabellenvariablen.  
  
5.  Verwenden Sie den Inhalt der speicheroptimierten Tabellenvariablen als Ergebnis der Abfrage.  
  
 Im folgenden Beispiel werden Tabellen aus der AdventureWorks2012-Datenbank verwendet, die für [!INCLUDE[hek_2](../includes/hek-2-md.md)]aktualisiert wurden. Zum Herunterladen der Dateien in diesem Beispiel "GoTo" [AdventureWorks-Datenbanken – 2012, 2008R2 und 2008](http://msftdbprodsamples.codeplex.com/releases/view/93587). Um das [!INCLUDE[hek_2](../includes/hek-2-md.md)] -Codebeispiel auf AdventureWorks2012 anzuwenden, rufen Sie [Beispiel zu SQL Server 2014 In-Memory OLTP](https://msftdbprodsamples.codeplex.com/releases/view/114491)auf.  
  
 Fügen Sie der Datenbank die folgende gespeicherte Prozedur hinzu. Diese gespeicherte Prozedur wird konvertiert, sodass sie die systeminterne Kompilierung verwendet. In diesem Beispiel werden INNER JOIN-Bedingungen verwendet.  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_ondisk  
  @SpecialOfferId int  
AS BEGIN  
  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  JOIN Sales.SpecialOffer_onDisk offer   
    ON s.SpecialOfferID = offer.SpecialOfferID   
    OR s.ProductID IN (SELECT ProductId FROM Sales.SpecialOfferProduct sop WHERE sop.SpecialOfferID = @SpecialOfferId)  
END  
```  
  
 Nach der Konvertierung erhalten Sie folgendes Schema für die Tabelle und die gespeicherte Prozedur:  
  
```  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_Type AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesSpecialOffers_Type NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_TempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  recordcount int null  
  INDEX ix_fuzzySearchSalesSpecialOffers_TempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_inmem  
  @SpecialOfferId int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.FuzzySearchSalesSpecialOffers_Type  
  
  -- Find all special offers matching the conditions  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOffer_inmem offer   
    ON s.SpecialOfferID = offer.SpecialOfferID  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOfferProduct_inmem sop   
    ON sop.SpecialOfferId = @SpecialOfferId AND s.ProductID = sop.ProductId  
  
  -- Now we need to remove the duplicates from @matchingSpecialOffers  
  DECLARE @duplicates Sales.fuzzySearchSalesSpecialOffers_TempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, SpecialOfferid, recordcount)  
  SELECT SalesOrderId, SalesOrderDetailId, SpecialOfferId, COUNT(*)   
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId, SpecialOfferId  
  
  -- now there should be no duplicates within @duplicate  
  -- use @duplicate for join.  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates offer   
    ON    s.SalesOrderId = offer.SalesOrderId   
      AND s.SalesOrderDetailId = offer.SalesOrderDetailID   
      AND s.SpecialOfferId = offer.SpecialOfferId  
END  
GO  
```  
  
## <a name="side-effects"></a>Nebeneffekte  
 Wenn Sie über mehr als einen OR-Operator in der WHERE-Klausel oder JOIN-Bedingung verfügen, kann die Anzahl der Abfragen, die zur Simulation des Verhaltens ausgeführt werden müssen, exponentiell ansteigen. Das kann die Abfrageleistung verlangsamen und zu einer höheren Arbeitsspeicherauslastung führen, weil speicheroptimierte Tabellenvariablen verwendet werden müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
