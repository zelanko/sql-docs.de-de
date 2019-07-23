---
title: 'Schritt 3: Proof of Concept für Verbindungen mit SQL Server mithilfe von Ruby | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cac20b18-0a6d-4243-bbda-a5d1b9476441
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9724fb48f6ae896d9026bfec63056070e2180a8e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992491"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>Schritt 3: Machbarkeitsnachweis für Verbindungen mit SQL mithilfe von Ruby

Dieses Beispiel sollte nur als Proof of Concept angesehen werden.  Der Beispielcode wird aus Gründen der Übersichtlichkeit vereinfacht und repräsentiert nicht notwendigerweise die bewährten Methoden, die von Microsoft empfohlen werden.  
  
## <a name="step-1--connect"></a>Schritt 1: verbinden  
  
Die [tinytds:: Client](https://github.com/rails-sqlserver/tiny_tds) -Funktion wird zum Herstellen einer Verbindung mit SQL-Datenbank verwendet.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>Schritt 2: Ausführen einer Abfrage  
  
Kopieren Sie den folgenden Code, und fügen Sie ihn in eine leere Datei ein. Nennen Sie Sie "Test. rb". Führen Sie den folgenden Befehl an der Eingabeaufforderung aus:  
  
    ruby test.rb  
  
Im Codebeispiel wird die Funktion [tinytds:: result](https://github.com/rails-sqlserver/tiny_tds) verwendet, um ein Resultset aus einer Abfrage für die SQL-Datenbank abzurufen. Diese Funktion akzeptiert eine Abfrage und gibt ein Resultset zurück. Das Resultset wird mithilfe von " [result. each do | Row |](https://github.com/rails-sqlserver/tiny_tds)" durchlaufen.  
  
``` ruby 
    require 'tiny_tds'    
    print 'test'       
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC")  
    results.each do |row|  
    puts row  
    end  
```  
  
## <a name="step-3--insert-a-row"></a>Schritt 3: Einfügen einer Zeile  
  
In diesem Beispiel erfahren Sie, wie Sie eine [Insert](../../t-sql/statements/insert-transact-sql.md) -Anweisung sicher ausführen, Parameter übergeben, die Ihre Anwendung vor dem SQL- [einschleusungs](../../relational-databases/tables/primary-and-foreign-key-constraints.md) Wert schützen.    
  
Um tinytds mit Azure zu verwenden, empfiehlt es sich, mehrere `SET` Anweisungen auszuführen, um zu ändern, wie die aktuelle Sitzung bestimmte Informationen verarbeitet. Empfohlene `SET` Anweisungen werden im Codebeispiel bereitgestellt. Beispielsweise können `SET ANSI_NULL_DFLT_ON` neue Spalten, die erstellt werden, auch dann NULL-Werte zulassen, wenn der Zulässigkeit-Status der Spalte nicht explizit angegeben wird.  
  
Um das Microsoft SQL Server [DateTime](../../t-sql/data-types/datetime-transact-sql.md) -Format auszurichten, verwenden Sie die Funktion " [strauftime](https://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime) ", um Sie in das entsprechende DateTime-Format umzuwandeln.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SET ANSI_NULLS ON")  
    results = client.execute("SET CURSOR_CLOSE_ON_COMMIT OFF")  
    results = client.execute("SET ANSI_NULL_DFLT_ON ON")  
    results = client.execute("SET IMPLICIT_TRANSACTIONS OFF")  
    results = client.execute("SET ANSI_PADDING ON")  
    results = client.execute("SET QUOTED_IDENTIFIER ON")  
    results = client.execute("SET ANSI_WARNINGS ON")  
    results = client.execute("SET CONCAT_NULL_YIELDS_NULL ON")  
    require 'date'  
    t = Time.now  
    curr_date = t.strftime("%Y-%m-%d %H:%M:%S.%L")  
    results = client.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate)  
    OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, '#{curr_date}' )")  
    results.each do |row|  
    puts row  
    end  
```
