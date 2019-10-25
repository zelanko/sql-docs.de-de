---
title: Einrichten des Massenkopierbeispiels
description: Beschreibt die Tabellen, die in den Massen Kopier Beispielen verwendet werden, und stellt SQL-Skripts zum Erstellen der Tabellen in der AdventureWorks-Datenbank bereit.
ms.date: 09/30/2019
dev_langs:
- sql
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 68a453efa165d73df521bc2ce3a00984f843f4fd
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452306"
---
# <a name="bulk-copy-example-setup"></a>Einrichten des Massenkopierbeispiels

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Die <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse kann verwendet werden, um Daten nur in SQL Server Tabellen zu schreiben. Die in diesem Thema gezeigten Codebeispiele verwenden die SQL Server-Beispieldatenbank **AdventureWorks**. Um eine Änderung der vorhandenen Codebeispiele zu vermeiden, schreiben die Codebeispiele Daten in Tabellen, die zuvor von Ihnen erstellt werden.  
  
Die Tabellen **BulkCopyDemoMatchingColumns** und **BulkCopyDemoDifferentColumns** basieren beide auf der Tabelle **AdventureWorks** **Production.Products**. In Codebeispielen, die diese Tabellen verwenden, werden Daten aus der Tabelle **Production.Products** einer dieser Beispieltabellen hinzugefügt. Die Tabelle **BulkCopyDemoDifferentColumns** wird verwendet, um im Beispiel zu veranschaulichen, wie Spalten aus den Quelldaten der Zieltabelle zugeordnet werden; für die meisten anderen Beispiele wird **BulkCopyDemoMatchingColumns** verwendet.  
  
Einige der Codebeispiele zeigen, wie eine Klasse <xref:Microsoft.Data.SqlClient.SqlBulkCopy> zum Schreiben in mehrere Tabellen verwendet werden kann. Für diese Beispiele werden die Tabellen **BulkCopyDemoOrderHeader** und **BulkCopyDemoOrderDetail** als Zieltabellen verwendet. Diese Tabellen basieren auf den Tabellen **Sales.SalesOrderHeader** und **Sales.SalesOrderDetail** in **AdventureWorks**.  
  
> [!NOTE]
>  Die **SqlBulkCopy**-Codebeispiele dienen ausschließlich der Veranschaulichung der für **SqlBulkCopy** verwendeten Syntax. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung `INSERT … SELECT` zum Kopieren der Daten einfacher und schneller.  
  
## <a name="table-setup"></a>Tabelleneinrichtung  
Zum Erstellen der Tabellen, die für die ordnungsgemäße Ausführung der Codebeispiele erforderlich sind, müssen Sie die folgenden Transact-SQL-Anweisungen in einer SQL Server-Datenbank ausführen.  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Massenkopiervorgänge in SQL Server](bulk-copy-operations-sql-server.md)
