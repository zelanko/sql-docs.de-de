---
title: sqlsrv_commit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_commit
apitype: NA
helpviewer_keywords:
- transaction support
- API Reference, sqlsrv_commit
- sqlsrv_commit
ms.assetid: bad67571-61ad-45b5-b4ff-677e3544f809
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 13c4f2534ec49c1d3467045d778e0c446f972573
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992849"
---
# <a name="sqlsrvcommit"></a>Sqlsrv_commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Überträgt die aktuelle Transaktion auf der angegebenen Verbindung, und gibt die Verbindung im Autocommit-Modus zurück. Die aktuelle Transaktion enthält alle Anweisungen für die angegebene Verbindung, die nach dem Aufruf von [sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md) und vor allen Aufrufen von [sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md) oder **sqlsrv_commit**ausgeführt wurden.  
  
> [!NOTE]  
> [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] befindet sich standardmäßig im Autocommit-Modus. Dies bedeutet, dass alle Abfragen bei Erfolg automatisch committet werden, es sei denn, sie wurden durch **sqlsrv_begin_transaction**.  
  
> [!NOTE]  
> Wenn **sqlsrv_commit** für eine Verbindung aufgerufen wird, die sich nicht in einer aktiven Transaktion mit der Initiierung **sqlsrv_begin_transaction**befindet, gibt der Aufruf **false** zurück, und der Fehlerauflistung wird ein *Not in Transaction* -Fehler hinzugefügt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_commit( resource $conn )  
```  
  
#### <a name="parameters"></a>Parameter  
*$conn*: Die Verbindung, auf der die Transaktion aktiv ist.  
  
## <a name="return-value"></a>Rückgabewert  
Ein boolescher Wert: **true** , wenn die Transaktion erfolgreich übertragen wurde. Andernfalls lautet der Wert **false**.  
  
## <a name="example"></a>Beispiel  
Im folgenden Beispiel werden zwei Abfragen im Rahmen einer Transaktion ausgeführt. Wenn beide Abfragen erfolgreich sind, wird die Transaktion committet. Wenn eine oder beide Abfragen fehlschlagen, wird für die Transaktion ein Rollback ausgeführt.  
  
Die erste Abfrage im Beispiel fügt einen neuen Verkaufsauftrag in die *Sales.SalesOrderDetail* -Tabelle der AdventureWorks-Datenbank ein. Der Auftrag umfasst fünf Einheiten des Produkts, das die Produkt-ID 709 besitzt. In der zweiten Abfrage wird der Lagerbestand des Produkts mit der ID 709 um fünf Einheiten reduziert. Diese Abfragen werden in eine Transaktion aufgenommen, weil beide Abfragen erfolgreich ausgeführt werden müssen, damit die Datenbank den Status von Aufträgen und die Verfügbarkeit von Produkten korrekt widerspiegelt.  
  
Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initiate transaction. */  
/* Exit script if transaction cannot be initiated. */  
if (sqlsrv_begin_transaction( $conn) === false)  
{  
     echo "Could not begin transaction.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initialize parameter values. */  
$orderId = 43659; $qty = 5; $productId = 709;  
$offerId = 1; $price = 5.70;  
  
/* Set up and execute the first query. */  
$tsql1 = "INSERT INTO Sales.SalesOrderDetail   
                     (SalesOrderID,   
                      OrderQty,   
                      ProductID,   
                      SpecialOfferID,   
                      UnitPrice)  
          VALUES (?, ?, ?, ?, ?)";  
$params1 = array( $orderId, $qty, $productId, $offerId, $price);  
$stmt1 = sqlsrv_query( $conn, $tsql1, $params1 );  
  
/* Set up and execute the second query. */  
$tsql2 = "UPDATE Production.ProductInventory   
          SET Quantity = (Quantity - ?)   
          WHERE ProductID = ?";  
$params2 = array($qty, $productId);  
$stmt2 = sqlsrv_query( $conn, $tsql2, $params2 );  
  
/* If both queries were successful, commit the transaction. */  
/* Otherwise, rollback the transaction. */  
if( $stmt1 && $stmt2 )  
{  
     sqlsrv_commit( $conn );  
     echo "Transaction was committed.\n";  
}  
else  
{  
     sqlsrv_rollback( $conn );  
     echo "Transaction was rolled back.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_close( $conn);  
?>  
```  
  
Für die Überwachung des Transaktionsverhaltens ist eine empfohlene Fehlerbehandlung im vorherigen Beispiel nicht enthalten. Für eine Produktionsanwendung wird empfohlen, dass jeder Aufruf einer **sqlsrv** -Funktion auf Fehler überprüft und entsprechend behandelt wird.  
  
> [!NOTE]  
> Verwenden Sie eingebettetes Transact-SQL nicht zum Durchführen von Transaktionen. Führen Sie z. B. keine Anweisung mit "BEGIN TRANSACTION" als Transact-SQL-Abfrage aus, um eine Transaktion zu beginnen. Das erwartete Transaktionsverhalten kann nicht garantiert werden, wenn eingebettetes Transact-SQL zum Durchführen von Transaktionen verwendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[Gewusst wie: Ausführen von Transaktionen](../../connect/php/how-to-perform-transactions.md)

[Overview of the Microsoft Drivers for PHP for SQL Server (Übersicht über die Microsoft-Treiber für PHP für SQL Server)](../../connect/php/overview-of-the-php-sql-driver.md)
  
