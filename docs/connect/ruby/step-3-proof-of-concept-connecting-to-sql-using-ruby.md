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
manager: jroth
ms.openlocfilehash: 20b63a0ffbe12f43ff943b9588e8392a90cff7e0
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800806"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>Schritt 3: Machbarkeitsnachweis für Verbindungen mit SQL mithilfe von Ruby

In diesem Beispiel sollte einen Proof of Concept nur angesehen werden.  Der Beispielcode ist aus Gründen der Übersichtlichkeit vereinfacht und ist nicht notwendigerweise von Microsoft empfohlene bewährte Methoden.  
  
## <a name="step-1--connect"></a>Schritt 1: Verbinden  
  
Die [tinytds:: Client](https://github.com/rails-sqlserver/tiny_tds) Funktion wird für die Verbindung mit SQL-Datenbank verwendet.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>Schritt 2: Ausführen einer Abfrage  
  
Kopieren Sie den folgenden Code in eine leere Datei. Rufen sie "Test.RB". Führen Sie es dann mithilfe des folgenden Befehls über die Befehlszeile aus:  
  
    ruby test.rb  
  
Im Codebeispiel das [tinytds:: result](https://github.com/rails-sqlserver/tiny_tds) Funktion wird verwendet, um ein Resultset aus einer Abfrage für SQL-Datenbank abzurufen. Diese Funktion akzeptiert eine Abfrage und gibt ein Resultset zurück. Das Resultset iteriert wird mithilfe der Tabulatortaste [result.each do | Zeile |](https://github.com/rails-sqlserver/tiny_tds).  
  
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
  
In diesem Beispiel erfahren Sie, wie zum Ausführen einer [einfügen](../../t-sql/statements/insert-transact-sql.md) -Anweisung sicher sind, übergibt Parameter zum Schutz Ihrer Anwendung vor [SQL-Einschleusung](../../relational-databases/tables/primary-and-foreign-key-constraints.md) Wert.    
  
Um TinyTDS mit Azure verwenden zu können, wird empfohlen, dass Sie mehrere ausführen `SET` Anweisungen zu ändern, wie die aktuelle Sitzung bestimmte Informationen behandelt. Empfohlene `SET` Anweisungen werden im Codebeispiel bereitgestellt. Z. B. `SET ANSI_NULL_DFLT_ON` können neue Spalten erstellt, um null-Werte zulassen, auch wenn die NULL-zulässigkeitsstatus der Spalte nicht explizit angegeben ist.  
  
Um mit dem Microsoft SQL Server auszurichten ["DateTime"](../../t-sql/data-types/datetime-transact-sql.md) formatieren, verwenden Sie die [Strftime](https://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime) Funktion, die in das entsprechende Datetime-Format umgewandelt.  
  
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
