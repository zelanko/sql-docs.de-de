---
title: 'Schritt 3: Proof of Concept für Verbindungen mit SQL Server mithilfe von pyodbc | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 10/09/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
author: MightyPen
ms.author: genemi
ms.openlocfilehash: faa2d63e0d1104665768ea436986b8fd3a52c107
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251781"
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
  
In diesem Beispiel erfahren Sie, wie Sie eine [Insert](../../../t-sql/statements/insert-transact-sql.md) -Anweisung sicher ausführen, Parameter übergeben, die Ihre Anwendung vor dem [SQL-einschleusungs](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) Wert schützen.    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
cnxn.commit()
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  

## <a name="azure-active-directory-aad-and-the-connection-string"></a>Azure Active Directory (AAD) und Verbindungs Zeichenfolge

pyODBC verwendet den Microsoft ODBC Driver for SQL Server.
Wenn Ihre Version des ODBC-Treibers 17,1 oder höher ist, können Sie den interaktiven Aad-Modus des ODBC-Treibers über pyodbc verwenden.
Diese Aad Interactive-Option funktioniert, wenn Python und pyodbc dem ODBC-Treiber gestatten, das Dialogfeld zu öffnen.
Diese Option ist nur unter dem Windows-Betriebssystem verfügbar.

### <a name="example-connection-string-for-aad-interactive-authentication"></a>Beispiel Verbindungs Zeichenfolge für die interaktive Aad-Authentifizierung

Hier ist ein Beispiel für eine ODBC-Verbindungs Zeichenfolge, die die interaktive Aad-Authentifizierung angibt

- `server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

Ausführliche Informationen zu den Aad-Authentifizierungs Optionen des ODBC-Treibers finden Sie im folgenden Artikel:

- [Verwenden von Azure Active Directory mit dem ODBC-Treiber](../../odbc/using-azure-active-directory.md#new-andor-modified-dsn-and-connection-string-keywords)

## <a name="next-steps"></a>Nächste Schritte
  
Weitere Informationen finden Sie im [python Developer Center](https://azure.microsoft.com/develop/python/).
