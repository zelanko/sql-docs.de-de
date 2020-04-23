---
title: 'Schritt 3: Herstellen der Verbindung mit SQL mithilfe von pymssql'
description: Schritt 3 ist ein Proof of Concept, der zeigt, wie Sie mithilfe von Python and pymssql eine Verbindung mit SQL Server herstellen können. Die grundlegenden Beispiele veranschaulichen das Auswählen und Einfügen von Daten.
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
ms.openlocfilehash: c1c75d13e9e44632c411639385227776f54ca1a9
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528564"
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
  
Mit der [cursor.execute](https://pypi.org/project/pymssql/) -Funktion können Sie ein Resultset aus einer Abfrage einer SQL-Datenbank abrufen. Diese Funktion akzeptiert praktisch jede Abfrage und gibt ein Resultset zurück, das mithilfe von [cursor.fetchone()](https://pypi.org/project/pymssql/) durchlaufen werden kann.  
  
  
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
  
In diesem Beispiel erfahren Sie, wie Sie eine [INSERT-](../../../t-sql/statements/insert-transact-sql.md) Anweisung auf sichere Weise ausführen und Parameter übergeben. Das Übergeben von Parametern als Werte schützt Ihre Anwendung vor einer [Einschleusung von SQL-Befehlen](../../../relational-databases/tables/primary-and-foreign-key-constraints.md).  
  
  
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
  
## <a name="step-4-roll-back-a-transaction"></a>Schritt 4: Durchführen des Rollbacks für eine Transaktion  
  
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
