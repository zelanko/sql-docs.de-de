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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ea474658e57c3f61df7eb95866ea4688c942a750
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80913096"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>Schritt 3: Proof of Concept für Verbindungen mit SQL mithilfe von pymssql
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

Dieses Beispiel ist lediglich als Proof of Concept zu verstehen.  Es wurde zur Verdeutlichung vereinfacht und entspricht nicht zwangsläufig den von Microsoft empfohlenen Best Practices.  
  
## <a name="step-1--connect"></a>Schritt 1:  Verbinden  
  
Die [pymssql.connect](https://pypi.org/project/pymssql/) -Funktion dient zum Herstellen einer Verbindung mit der SQL-Datenbank.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>Schritt 2:  Abfrage ausführen  
  
Mit der [cursor.execute](https://pypi.org/project/pymssql/) -Funktion können Sie ein Resultset aus einer Abfrage einer SQL-Datenbank abrufen. Diese Funktion akzeptiert praktisch jede Abfrage und gibt ein Resultset zurück, das mithilfe von [cursor.fetchone()](https://pypi.org/project/pymssql/)durchlaufen werden kann.  
  
  
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
  
## <a name="step-3--insert-a-row"></a>Schritt 3:  Einfügen einer Zeile  
  
In diesem Beispiel erfahren Sie, wie Sie eine [INSERT](../../../t-sql/statements/insert-transact-sql.md)-Anweisung sicher ausführen und Parameter zum Schutz Ihrer Anwendung vor einer [Einschleusung von SQL-Befehlen](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) übergeben.    
  
  
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
  
## <a name="step-4--rollback-a-transaction"></a>Schritt 4:  Durchführen eines Rollbacks für eine Transaktion  
  
Dieses Codebeispiel veranschaulicht die Verwendung von Transaktionen für folgende Aufgaben:  
  
* Starten von Transaktionen  
* Einfügen einer Zeile mit Daten  
* Durchführen von Rollbacks für Transaktionen, um Einfügungen rückgängig zu machen  
  
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
  
Weitere Informationen finden Sie im [Python Developer Center](https://azure.microsoft.com/develop/python/).
