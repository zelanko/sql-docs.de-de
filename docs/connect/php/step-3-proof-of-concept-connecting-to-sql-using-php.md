---
title: 'Schritt 3: Herstellen der Verbindung mit SQL mithilfe von PHP'
description: Schritt 3 ist ein Proof of Concept, der zeigt, wie Sie mithilfe von PHP eine Verbindung mit SQL Server herstellen können. Die grundlegenden Beispiele veranschaulichen das Auswählen und Einfügen von Daten.
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a7451a85-18e5-4fd0-bbcb-2f15a1117290
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69c8b1ec58dbb40ab6e4463d343720e02e583ac8
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528584"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-php"></a>Schritt 3: Proof of Concept für Verbindungen mit SQL Server mithilfe von PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="step-1--connect"></a>Schritt 1:  Verbinden  
  
  
Diese **OpenConnection** -Funktion wird zu Beginn in allen im Folgenden aufgeführten Funktionen aufgerufen.  
  
  
```php 
    function OpenConnection()  
    {  
        try  
        {  
            $serverName = "tcp:myserver.database.windows.net,1433";  
            $connectionOptions = array("Database"=>"AdventureWorks",  
                "Uid"=>"MyUser", "PWD"=>"MyPassword");  
            $conn = sqlsrv_connect($serverName, $connectionOptions);  
            if($conn == false)  
                die(FormatErrors(sqlsrv_errors()));  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-2--execute-query"></a>Schritt 2:  Abfrage ausführen  
  
Mit der [sqlsrv_query](https://php.net/manual/en/function.sqlsrv-query.php)-Funktion können Sie ein Resultset aus einer Abfrage einer SQL-Datenbank abrufen. Diese Funktion akzeptiert praktisch jede Abfrage und jedes Verbindungsobjekt und gibt ein Resultset zurück, das mithilfe von [sqlsrv_fetch_array()](https://php.net/manual/en/function.sqlsrv-fetch-array.php) durchlaufen werden kann.  
  
```php  
    function ReadData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
            $tsql = "SELECT [CompanyName] FROM SalesLT.Customer";  
            $getProducts = sqlsrv_query($conn, $tsql);  
            if ($getProducts == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
            $productCount = 0;  
            while($row = sqlsrv_fetch_array($getProducts, SQLSRV_FETCH_ASSOC))  
            {  
                echo($row['CompanyName']);  
                echo("<br/>");  
                $productCount++;  
            }  
            sqlsrv_free_stmt($getProducts);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
  
## <a name="step-3--insert-a-row"></a>Schritt 3:  Einfügen einer Zeile  
  
In diesem Beispiel erfahren Sie, wie Sie eine [INSERT](../../t-sql/statements/insert-transact-sql.md)-Anweisung auf sichere Weise ausführen und Parameter übergeben. Parameterwerte schützen Ihre Anwendung vor einer [Einschleusung von SQL-Befehlen](../../relational-databases/tables/primary-and-foreign-key-constraints.md).
  
```php 
    function InsertData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            $tsql = "INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT            INSERTED.ProductID VALUES ('SQL Server 1', 'SQL Server 2', 0, 0, getdate())";  
            //Insert query  
            $insertReview = sqlsrv_query($conn, $tsql);  
            if($insertReview == FALSE)  
                die(FormatErrors( sqlsrv_errors()));  
            echo "Product Key inserted is :";  
            while($row = sqlsrv_fetch_array($insertReview, SQLSRV_FETCH_ASSOC))  
            {     
                echo($row['ProductID']);  
            }  
            sqlsrv_free_stmt($insertReview);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-4--roll-back-a-transaction"></a>Schritt 4:  Ausführen des Rollbacks für eine Transaktion  
  
  
Dieses Codebeispiel veranschaulicht die Verwendung von Transaktionen für folgende Aufgaben:  
  
\- Starten von Transaktionen  
  
\- Hinzufügen einer Zeile mit Daten und Aktualisieren einer anderen Datenzeile  
  
– Durchführen eines Commits der Transaktion, wenn Einfügung und Aktualisierung erfolgreich waren, und eines Rollbacks der Transaktion, wenn bei einem Vorgang ein Fehler aufgetreten ist  
  
  
```php 
    function Transactions()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            if (sqlsrv_begin_transaction($conn) == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
  
            $tsql1 = "INSERT INTO SalesLT.SalesOrderDetail (SalesOrderID,OrderQty,ProductID,UnitPrice)  
            VALUES (71774, 22, 709, 33)";  
            $stmt1 = sqlsrv_query($conn, $tsql1);  
  
            /* Set up and execute the second query. */  
            $tsql2 = "UPDATE SalesLT.SalesOrderDetail SET OrderQty = (OrderQty + 1) WHERE ProductID = 709";  
            $stmt2 = sqlsrv_query( $conn, $tsql2);  
  
            /* If both queries were successful, commit the transaction. */  
            /* Otherwise, rollback the transaction. */  
            if($stmt1 && $stmt2)  
            {  
                   sqlsrv_commit($conn);  
                   echo("Transaction was commited");  
            }  
            else  
            {  
                sqlsrv_rollback($conn);  
                echo "Transaction was rolled back.\n";  
            }  
            /* Free statement and connection resources. */  
            sqlsrv_free_stmt( $stmt1);  
            sqlsrv_free_stmt( $stmt2);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="additional-examples"></a>Zusätzliche Beispiele  
  
[Beispielanwendung (SQLSRV-Treiber)](../../connect/php/example-application-sqlsrv-driver.md)  

[Beispielanwendung (PDO_SQLSRV-Treiber)](../../connect/php/example-application-pdo-sqlsrv-driver.md)
