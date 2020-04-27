---
title: Migrieren von Triggern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7df393f26523991abafded74ded242390cb0e3b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63071468"
---
# <a name="migrating-triggers"></a>Migrieren von Triggern
  In diesem Thema werden DDL- und DML-Trigger sowie speicheroptimierte Tabellen erläutert.  
  
 LOGON-Trigger sind Trigger zum Auslösen von LOGON-Ereignissen. LOGON-Trigger wirken sich nicht auf speicheroptimierte Tabellen aus.  
  
## <a name="ddl-triggers"></a>DDL-Trigger  
 DDL-Trigger sind Trigger, die ausgelöst werden, wenn eine CREATE-, ALTER-, DROP-, GRANT-, DENY-, REVOKE- oder UPDATE STATISTICS-Anweisung für die Datenbank oder den Server ausgeführt wird, für die oder den sie definiert wurde.  
  
 Sie können keine speicheroptimierten Tabellen erstellen, wenn die Datenbank oder der Server über mindestens einen DDL-Trigger verfügt, der für CREATE_TABLE oder eine beliebige Ereignisgruppe definiert wurde, in der das Ereignis enthalten ist. Sie können keine speicheroptimierte Tabelle löschen, wenn die Datenbank oder der Server über mindestens einen DDL-Trigger verfügt, der für DROP_TABLE oder eine beliebige Ereignisgruppe definiert wurde, in der das Ereignis enthalten ist.  
  
 Systemintern kompilierte gespeicherte Prozeduren können nicht erstellt werden, wenn mindestens ein DDL-Trigger für CREATE_PROCEDURE, DROP_PROCEDURE oder eine beliebige Ereignisgruppe definiert wurde, in der diese Ereignisse enthalten sind.  
  
## <a name="dml-triggers"></a>DML-Trigger  
 DML-Trigger können nicht für speicheroptimierte Tabellen definiert werden. Mit In-Memory OLTP können Sie jedoch eine mit DML-Triggern vergleichbare Wirkung erzielen, wenn Sie gespeicherte Prozeduren explizit verwenden, um INSERT-, UPDATE- oder DELETE-Vorgänge für Daten auszuführen. Wenn Ihr System Ad-hoc-Abfragen enthält, sollten Sie sie konvertieren, damit sie die gespeicherten Prozeduren verwenden, anstatt die Wirkung von DML-Triggern zu simulieren.  
  
 Je nach Triggerereignis (FOR/AFTER oder INSTEAD OF) können Sie den Inhalt des Triggers in die entsprechende gespeicherte Prozedur einschließen, von der INSERT, UPDATE oder DELETE für die Tabelle ausgeführt wird. Bei der Migration eines AFTER INSERT-Triggers können Sie beispielsweise die gespeicherte Prozedur ändern, die den Einfügevorgang ausführt. Dazu fügen Sie den Inhalt des Triggers nach der entsprechenden INSERT-Anweisung ein.  
  
 Sie können eine interpretierte gespeicherte Prozedur oder eine systemintern kompilierte gespeicherte Prozedur verwenden. Die meisten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Konstrukte in einer interpretierten gespeicherten Prozedur können für eine speicheroptimierte Tabelle ausgeführt werden. In systemintern kompilierten gespeicherten Prozeduren wird jedoch nur eine Teilmenge der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Konstrukte unterstützt. Informationen zur [!INCLUDE[tsql](../../includes/tsql-md.md)] Unterstützung für Speicher optimierte Tabellen finden Sie unter [zugreifen auf Speicher optimierte Tabellen mit interpretiertem Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md). Informationen zur [!INCLUDE[tsql](../../includes/tsql-md.md)] Unterstützung in System intern kompilierten gespeicherten Prozeduren finden Sie unter [von in-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
 Im Folgenden finden Sie ein einfaches Beispiel dafür, wie Sie das Verhalten von DML-Triggern für eine speicheroptimierte Tabelle simulieren.  
  
 Die Datenbank enthält die folgenden Objekte, die in Form von CREATE TABLE-, CREATE TRIGGER- und CREATE PROCEDURE-Anweisungen in Skripts definiert sind:  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null primary key,  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
)  
GO  
  
CREATE TRIGGER tr_order_details_insteadof_insert  
ON OrderDetails  
INSTEAD OF INSERT AS  
BEGIN  
   DECLARE @pid int, @qty_buy int, @qty_remain int  
   SELECT @pid = ProductId, @qty_buy = Quantity FROM inserted  
   SELECT @qty_remain = Quantity FROM Inventory WHERE ProductId = @pid  
   IF (@qty_remain <= @qty_buy)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      SELECT OrderId, ProductId, SalePrice, Quantity, Total FROM inserted  
      UPDATE Inventory SET Quantity = Quantity - @qty_buy WHERE ProductId = @pid  
   END  
END  
GO  
  
CREATE TRIGGER tr_order_details_after_update  
ON OrderDetails  
AFTER UPDATE AS  
BEGIN  
   INSERT INTO UpdateNotifications (OrderId, UpdateTime) SELECT OrderId, GETDATE() FROM inserted     
END  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
AS BEGIN  
   INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
   VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
AS BEGIN  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
END  
GO  
```  
  
 Die folgenden Objekte sind funktional äquivalent mit dem Zustand vor der Migration:  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 1048576),  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE Inventory  
(  
   ProductId int not null PRIMARY KEY NONCLUSTERED,  
   Quantity int not null  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE UpdateNotifications  
(  
   OrderId int not null,  
   UpdateTime datetime2 not null  
   CONSTRAINT pk_updateNotifications PRIMARY KEY NONCLUSTERED (OrderId, UpdateTime)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   DECLARE @qty_remain int  
   SELECT @qty_remain = Quantity FROM dbo.Inventory WHERE ProductId = @ProductId  
   IF (@qty_remain <= @Quantity)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
      UPDATE dbo.Inventory SET Quantity = Quantity - @Quantity WHERE ProductId = @ProductId  
   END  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
   INSERT INTO dbo.UpdateNotifications (OrderId, UpdateTime) VALUES (@OrderId, GETDATE())  
END  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
