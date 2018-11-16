---
title: 'Schritt 3: Proof of Concept für Verbindungen mit SQL Server mithilfe von pymssql | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2246ddeb-7c2f-46f3-8a91-cdd718d39b40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef8c981dea064595433568a89088e800d81876e7
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606820"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>Schritt 3: Machbarkeitsnachweis für Verbindungen mit SQL mithilfe von pymssql
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

In diesem Beispiel sollte einen Proof of Concept nur angesehen werden.  Der Beispielcode ist aus Gründen der Übersichtlichkeit vereinfacht und ist nicht notwendigerweise von Microsoft empfohlene bewährte Methoden.  
  
## <a name="step-1--connect"></a>Schritt 1: Verbinden  
  
Die [pymssql.connect](https://pymssql.org/en/latest/ref/pymssql.html) Funktion wird für die Verbindung mit SQL-Datenbank verwendet.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>Schritt 2: Ausführen der Abfrage  
  
Die [cursor.execute](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute) Funktion kann verwendet werden, um ein Resultset aus einer Abfrage für SQL-Datenbank abzurufen. Diese Funktion im Wesentlichen akzeptiert jede Abfrage und gibt ein Resultset mit der Verwendung von durchlaufen werden kann [cursor.fetchone()](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone).  
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute('SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC;')  
    row = cursor.fetchone()  
    while row:  
        print str(row[0]) + " " + str(row[1]) + " " + str(row[2])     
        row = cursor.fetchone()  
```  
  
## <a name="step-3--insert-a-row"></a>Schritt 3: Einfügen einer Zeile  
  
In diesem Beispiel erfahren Sie, wie zum Ausführen einer [einfügen](../../../t-sql/statements/insert-transact-sql.md) -Anweisung sicher sind, übergibt Parameter zum Schutz Ihrer Anwendung vor [SQL-Einschleusung](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) Wert.    
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express', 'SQLEXPRESS', 0, 0, CURRENT_TIMESTAMP)")  
    row = cursor.fetchone()  
    while row:  
        print "Inserted Product ID : " +str(row[0])  
        row = cursor.fetchone()  
    conn.commit()
    conn.close()
```  
  
## <a name="step-4--rollback-a-transaction"></a>Schritt 4: Rollback einer Transaktion  
  
Dieses Codebeispiel veranschaulicht die Verwendung von Transaktionen in der Sie:  
  
* Starten von Transaktionen  
* Einfügen von Zeilen mit Daten  
* Rollback der Transaktion zum Rückgängigmachen von einfügungen  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("BEGIN TRANSACTION")  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, CURRENT_TIMESTAMP)")  
    conn.rollback()  
    conn.close()
```  
    
  ## <a name="next-steps"></a>Nächste Schritte  
  
Weitere Informationen finden Sie unter den [Python Developer Center](https://azure.microsoft.com/develop/python/).
