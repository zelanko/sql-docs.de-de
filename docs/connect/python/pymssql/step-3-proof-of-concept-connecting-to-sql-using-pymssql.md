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
ms.openlocfilehash: 27b56a20a0456bef04553c614432bde270d8e98d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935774"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>Schritt 3: Machbarkeitsnachweis für Verbindungen mit SQL mithilfe von pymssql
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

Dieses Beispiel sollte nur als Proof of Concept angesehen werden.  Der Beispielcode wird aus Gründen der Übersichtlichkeit vereinfacht und repräsentiert nicht notwendigerweise die bewährten Methoden, die von Microsoft empfohlen werden.  
  
## <a name="step-1--connect"></a>Schritt 1: verbinden  
  
Die [pymssql. Connect](https://pymssql.org/en/latest/ref/pymssql.html) -Funktion wird zum Herstellen einer Verbindung mit SQL-Datenbank verwendet.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>Schritt 2: Ausführen der Abfrage  
  
Die [Cursor. Execute](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute) -Funktion kann verwendet werden, um ein Resultset aus einer Abfrage für die SQL-Datenbank abzurufen. Diese Funktion akzeptiert im Wesentlichen eine beliebige Abfrage und gibt ein Resultset zurück, das mit der Verwendung von [Cursor. fetchone ()](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone)durchlaufen werden kann.  
  
  
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
  
In diesem Beispiel erfahren Sie, wie Sie eine [Insert](../../../t-sql/statements/insert-transact-sql.md) -Anweisung sicher ausführen, Parameter übergeben, die Ihre Anwendung vor dem SQL- [einschleusungs](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) Wert schützen.    
  
  
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
  
Dieses Codebeispiel veranschaulicht die Verwendung von Transaktionen, in denen Sie folgende Vorgänge ausführen:  
  
* Beginnen einer Transaktion  
* Einfügen einer Zeile mit Daten  
* Zurücksetzen der Transaktion zum Rückgängigmachen der Einfügung  
  
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
  
Weitere Informationen finden Sie im [python Developer Center](https://azure.microsoft.com/develop/python/).
