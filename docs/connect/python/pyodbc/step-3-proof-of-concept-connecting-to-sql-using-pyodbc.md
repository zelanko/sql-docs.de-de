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
ms.openlocfilehash: 0e241d84ebc60acceafe09b1a9240711a72d2067
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "72798319"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Schritt 3: Proof of Concept für Verbindungen mit SQL mithilfe von pyodbc

Dieses Beispiel ist lediglich als Proof of Concept zu verstehen.  Es wurde zur Verdeutlichung vereinfacht und entspricht nicht zwangsläufig den von Microsoft empfohlenen Best Practices.  

**Führen Sie das unten angegebene Beispielskript aus.** Erstellen Sie eine Datei namens „test.py“, und fügen Sie nach und nach alle Codeausschnitte ein. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Schritt 1:  Verbinden  
  
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
  
  
## <a name="step-2--execute-query"></a>Schritt 2:  Abfrage ausführen  
  
Mit der Funktion „cursor.execute“ können Sie ein Resultset aus einer Abfrage einer SQL-Datenbank abrufen. Diese Funktion akzeptiert praktisch jede Abfrage und gibt ein Resultset zurück, das mithilfe von „cursor.fetchone()“ durchlaufen werden kann.
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print(row[0])
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Schritt 3:  Einfügen einer Zeile  
  
In diesem Beispiel erfahren Sie, wie Sie eine [INSERT](../../../t-sql/statements/insert-transact-sql.md)-Anweisung sicher ausführen und Parameter zum Schutz Ihrer Anwendung vor einer [Einschleusung von SQL-Befehlen](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) übergeben.    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
cnxn.commit()
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  

## <a name="azure-active-directory-aad-and-the-connection-string"></a>Azure Active Directory (AAD) und die Verbindungszeichenfolge

pyODBC verwendet den Microsoft ODBC Driver for SQL Server.
Wenn Sie den ODBC-Treiber, Version 17.1 oder höher haben, können Sie den interaktiven AAD-Modus des ODBC-Treibers mithilfe von pyODBC verwenden.
Diese interaktive AAD-Option funktioniert, wenn Python und pyODBC dem ODBC-Treiber gestatten, das Dialogfeld zu öffnen.
Diese Option ist nur unter dem Windows-Betriebssystem verfügbar.

### <a name="example-connection-string-for-aad-interactive-authentication"></a>Beispielverbindungszeichenfolge für die interaktive AAD-Authentifizierung

Im Folgenden finden Sie ein Beispiel für eine ODBC-Verbindungszeichenfolge, die die interaktive AAD-Authentifizierung angibt:

- `server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

Weitere Informationen zu den AAD-Authentifizierungsoptionen des ODBC-Treibers finden Sie im folgenden Artikel:

- [Verwenden von Azure Active Directory mit dem ODBC-Treiber](../../odbc/using-azure-active-directory.md#new-andor-modified-dsn-and-connection-string-keywords)

## <a name="next-steps"></a>Nächste Schritte
  
Weitere Informationen finden Sie im [Python Developer Center](https://azure.microsoft.com/develop/python/).
