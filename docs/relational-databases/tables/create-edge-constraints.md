---
title: Erstellen von Edgeeinschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 97ad249695c4fbe0fd79a23a5493d998fbaf5191
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582306"
---
# <a name="create-edge-constraints"></a>Erstellen von Edgeeinschränkungen
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

   Sie können mit [!INCLUDE[tsql](../../includes/tsql-md.md)] eine Edgeeinschränkung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definieren. 
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Eine Edgeeinschränkung kann nur in einer Graph-Edgetabelle definiert werden. 
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  

### <a name="to-create-an-edge-constraint-on-a-new-edge-table"></a>So erstellen Sie eine Edgeeinschränkung in einer neuen Edgetabelle
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Dieses Beispiel erstellt eine Edgeeinschränkung in der Edgetabelle **bought**.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 ```sql
 USE TEMPDB
 GO
 -- CREATE node and edge tables
 CREATE TABLE Customer
    (
        ID INTEGER PRIMARY KEY, 
        CustomerName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Product 
  (
        ID INTEGER PRIMARY KEY, 
        ProductName VARCHAR(100)
  ) AS NODE
 GO

 CREATE TABLE bought
    (
        PurchaseCount INT,
        CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
    )
 AS EDGE
 GO
 ```  

### <a name="to-add-edge-constraint-to-an-existing-edge-table"></a>So fügen Sie einer vorhandenen Edgetabelle eine Edgeeinschränkung hinzu 
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Das Beispiel verwendet ALTER TABLE, um der Edgetabelle **bought** eine Edgeeinschränkung hinzuzufügen.
  
 ```sql
 USE TEMPDB
 GO
 -- CREATE node and edge tables
 CREATE TABLE Customer
    (
        ID INTEGER PRIMARY KEY, 
        CustomerName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Product 
  (
        ID INTEGER PRIMARY KEY, 
        ProductName VARCHAR(100)
  ) AS NODE
 GO

 CREATE TABLE bought
    (
        PurchaseCount INT
    )
 AS EDGE
 GO

 ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT1 CONNECTION (Customer TO Product)
 GO
 ```  

### <a name="creating-a-new-edge-constraint-on-existing-edge-table-with-additional-edge-constraint-clauses"></a>In einer vorhandenen Edgetabelle wird eine neue Edgeeinschränkung mit zusätzlichen Edgeeinschränkungsklauseln erstellt.
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Das Beispiel verwendet ALTER TABLE, um eine neue Edgeeinschränkung mit zusätzlichen Edgeeinschränkungsklauseln in der Edgetabelle **bought** hinzuzufügen.
  
 ```sql
 USE TEMPDB
 GO
 -- CREATE node and edge tables
 CREATE TABLE Customer
    (
        ID INTEGER PRIMARY KEY, 
        CustomerName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Supplier
    (
        ID INTEGER PRIMARY KEY, 
        SupplierName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Product 
  (
        ID INTEGER PRIMARY KEY, 
        ProductName VARCHAR(100)
  ) AS NODE
 GO

 CREATE TABLE bought
    (
        PurchaseCount INT,
        CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
    )
 AS EDGE
 GO

 -- Drop the existing edge constraint first and then create a new one.
 ALTER TABLE bought DROP CONSTRAINT EC_BOUGHT
 GO

 -- User ALTER TABLE to create a new edge constraint.
 ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT1 CONNECTION (Customer TO Product, Supplier TO Product)
 GO
 ```  
 Beachten Sie, dass es in der Einschränkung *EC_BOUGHT1* zwei Edgeeinschränkungsklauseln gibt: Eine stellt eine Verbindung von **Customer** zu **Product** her, die andere verbindet **Supplier** mit **Product**. Beide Klauseln werden in Disjunktion angewendet. Das bedeutet, dass ein Edge die Bedingung einer der beiden Klauseln erfüllen muss, um in der Edgetabelle zugelassen zu werden. 



### <a name="creating-a-new-edge-constraint-on-existing-edge-table-with-new-edge-constraint-clause"></a>In einer vorhandenen Edgetabelle wird eine neue Edgeeinschränkung mit einer neuen Edgeeinschränkungsklausel erstellt.
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Das Beispiel verwendet ALTER TABLE, um eine neue Edgeeinschränkung mit einer neuen Edgeeinschränkungsklausel in der Edgetabelle **bought** hinzuzufügen.
  
 ```sql
 USE TEMPDB
 GO
 -- CREATE node and edge tables
 CREATE TABLE Customer
    (
        ID INTEGER PRIMARY KEY, 
        CustomerName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Supplier
    (
        ID INTEGER PRIMARY KEY, 
        SupplierName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Product 
  (
        ID INTEGER PRIMARY KEY, 
        ProductName VARCHAR(100)
  ) AS NODE
 GO

 CREATE TABLE bought
    (
        PurchaseCount INT,
        CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
    )
 AS EDGE
 GO

 ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT1 CONNECTION (Supplier TO Product)
 GO
 ```  

 In diesem Beispiel haben wir zwei separate Edgeeinschränkungen in der Edgetabelle **bought** erstellt: *EC_BOUGHT* und *EC_BOUGHT1*. Beide Edgeeinschränkungen weisen unterschiedliche Edgeeinschränkungsklauseln auf. Wenn eine Edgetabelle über mehr als eine Edgeeinschränkung verfügt, muss ein Edge **ALLE** Edgeeinschränkungen erfüllen, um in der Tabelle zugelassen zu werden. Da kein Edge hier sowohl *EC_BOUGHT* als auch *EC_BOUGHT1* erfüllen kann, muss die Tabelle **bought** leer bleiben. 

 Damit Einfügungen in diese Edgetabelle funktionieren, muss entweder eine der Edgeeinschränkungen gelöscht werden, oder es müssen beide Einschränkungen gelöscht und eine neue Edgeeinschränkung erstellt werden, die beide Edgeeinschränkungsklauseln enthält. 

 ```sql
 USE TEMPDB
 GO
 -- Drop the existing edge constraint first and then create a new one.
 ALTER TABLE bought DROP CONSTRAINT EC_BOUGHT
 GO
 
 ALTER TABLE bought DROP CONSTRAINT EC_BOUGHT1
 GO
 
 ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT_NEW CONNECTION (Customer TO Product, Supplier TO Product)
 GO
 ```  

 Damit ein Edge in der Edgetabelle **bought** zugelassen wird, muss es eine der Edgeeinschränkungsklauseln in der Einschränkung *EC_BOUGHT_NEW* erfüllen. Daher wird jedes Edge zugelassen, das versucht, eine Verbindung zwischen den gültigen Knoten **Customer** und **Product** bzw. **Supplier** und **Product** herzustellen. 
