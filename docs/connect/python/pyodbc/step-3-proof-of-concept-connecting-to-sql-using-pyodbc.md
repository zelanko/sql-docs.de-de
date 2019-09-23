---
title: 'Schritt 3: Proof of Concept für Verbindungen mit SQL Server mithilfe von pyodbc | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 30ba3db5e23d95128aecbb5cc8974faeb6d58d75
ms.sourcegitcommit: 6413b7495313830ad1ae5aefe0c09e8e7a284b07
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2019
ms.locfileid: "71016841"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Schritt 3: Proof of Concept für Verbindungen mit SQL mithilfe von pyodbc

Dieses Beispiel sollte nur als Proof of Concept angesehen werden.  Der Beispielcode wird aus Gründen der Übersichtlichkeit vereinfacht und repräsentiert nicht notwendigerweise die bewährten Methoden, die von Microsoft empfohlen werden.  

**Beispielskript unten ausführen**  Erstellen Sie eine Datei mit dem Namen Test.py, und fügen Sie jeden Code Ausschnitt hinzu. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Schritt 1: verbinden  
  
```python

import pyodbc 
# Some other example server values are
# server = 'localhost\sqlexpress' # for a named instance
# server = 'myserver,port' # to specify an alternate port
server = 'tcp:myserver.database.windows.net' 
database = 'mydb' 
username = 'myusername' 
password = 'mypassword' 
cnxn = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
cursor = cnxn.cursor()

```  
  
  
## <a name="step-2--execute-query"></a>Schritt 2: Ausführen der Abfrage  
  
Die Cursor. ExecuteFunction kann verwendet werden, um ein Resultset aus einer Abfrage für die SQL-Datenbank abzurufen. Diese Funktion akzeptiert im Grunde jede beliebige Abfrage und gibt ein Resultset zurück, das mit der Verwendung von Cursor. fetchone () durchlaufen werden kann.
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print row[0] 
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Schritt 3: Einfügen einer Zeile  
  
In diesem Beispiel erfahren Sie, wie Sie eine [Insert](../../../t-sql/statements/insert-transact-sql.md) -Anweisung sicher ausführen, Parameter übergeben, die Ihre Anwendung vor dem SQL- [einschleusungs](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) Wert schützen.    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
cnxn.commit()
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  
  `      
  ## <a name="next-steps"></a>Nächste Schritte  
  
Weitere Informationen finden Sie im [python Developer Center](https://azure.microsoft.com/develop/python/).
