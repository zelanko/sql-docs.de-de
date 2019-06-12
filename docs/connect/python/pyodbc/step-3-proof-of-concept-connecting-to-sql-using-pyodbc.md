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
manager: jroth
ms.openlocfilehash: e8f4c34c1b6b945c28193a549a06546ec952a5d9
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66780371"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Schritt 3: Proof of Concept für Verbindungen mit SQL mithilfe von pyodbc

In diesem Beispiel sollte einen Proof of Concept nur angesehen werden.  Der Beispielcode ist aus Gründen der Übersichtlichkeit vereinfacht und ist nicht notwendigerweise von Microsoft empfohlene bewährte Methoden.  

**Führen Sie folgenden Beispielskript** erstellen Sie eine Datei namens test.py, und fügen Sie jeden Codeausschnitt hinzu, alles. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Schritt 1: Verbinden  
  
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
  
Die cursor.executefunction kann verwendet werden, um ein Resultset aus einer Abfrage für SQL-Datenbank abzurufen. Diese Funktion im Wesentlichen akzeptiert jede Abfrage und gibt ein Resultset mit der Verwendung von cursor.fetchone() durchlaufen werden können
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print row[0] 
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Schritt 3: Einfügen einer Zeile  
  
In diesem Beispiel erfahren Sie, wie zum Ausführen einer [einfügen](../../../t-sql/statements/insert-transact-sql.md) -Anweisung sicher sind, übergibt Parameter zum Schutz Ihrer Anwendung vor [SQL-Einschleusung](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) Wert.    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  
  `      
  ## <a name="next-steps"></a>Nächste Schritte  
  
Weitere Informationen finden Sie unter den [Python Developer Center](https://azure.microsoft.com/develop/python/).
