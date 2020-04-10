---
title: 'Schritt 4: Herstellen stabiler SQL-Verbindungen mit PHP | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8013474f-48e9-43d5-ab89-7b0504044468
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9467a62d2d3ca1cbbd9b5a543c27f310f7d3ba60
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926892"
---
# <a name="step-4-connect-resiliently-to-sql-with-php"></a>Schritt 4: Herstellen stabiler SQL-Verbindungen mit PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

  
Das Demoprogramm wurde so entworfen, dass vorübergehende Fehler (d. h. solche mit einem Fehlercode mit dem Präfix „08“, wie in diesem [Anhang](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes) aufgeführt), die während des Versuchs auftreten, eine Verbindung herzustellen, zu einem nochmaligen Versuch führen. Ein vorübergehender Fehler während des Abfragebefehls bewirkt jedoch, dass das Programm die Verbindung verwirft und eine neue Verbindung herstellt, bevor der Abfragebefehl wiederholt wird. Microsoft spricht keinerlei Empfehlung für oder gegen diese Entwurfsentscheidung aus. Das Demoprogramm soll lediglich die Entwurfsflexibilität veranschaulichen, die Ihnen zur Verfügung steht.  
  
Die Länge dieses Codebeispiel ist größtenteils auf die Catch-Exception-Logik zurückzuführen.   
  
Mit der [sqlsrv_query()](../../connect/php/sqlsrv-query.md)-Funktion können Sie ein Resultset aus einer Abfrage einer SQL-Datenbank abrufen. Diese Funktion akzeptiert praktisch jede Abfrage und jedes Verbindungsobjekt und gibt ein Resultset zurück, das mithilfe von [sqlsrv_fetch_array()](../../connect/php/sqlsrv-fetch-array.md) durchlaufen werden kann. 
  
```php

    <?php  
        // Variables to tune the retry logic.    
        $connectionTimeoutSeconds = 30;  // Default of 15 seconds is too short over the Internet, sometimes.  
        $maxCountTriesConnectAndQuery = 3;  // You can adjust the various retry count values.  
        $secondsBetweenRetries = 4;  // Simple retry strategy.  
        $errNo = 0;  
        $serverName = "tcp:yourdatabase.database.windows.net,1433";  
        $connectionOptions = array("Database"=>"AdventureWorks",  
           "Uid"=>"yourusername", "PWD"=>"yourpassword", "LoginTimeout" => $connectionTimeoutSeconds);  
        $conn = null;  
        $arrayOfTransientErrors = array('08001', '08002', '08003', '08004', '08007', '08S01'); 
        for ($cc = 1; $cc <= $maxCountTriesConnectAndQuery; $cc++) {  
            // [A.2] Connect, which proceeds to issue a query command.  
            $conn = sqlsrv_connect($serverName, $connectionOptions);    
            if ($conn === true) {  
                echo "Connection was established";  
                echo "<br>";  
  
                $tsql = "SELECT Name FROM Production.ProductCategory";  
                $stmt = sqlsrv_query($conn, $tsql);  
                if ($stmt === false) {
                    echo "Error in query execution";  
                    echo "<br>";  
                    die(print_r(sqlsrv_errors(), true));  
                }
                while($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {     
                    echo $row['Name'] . "<br/>" ;
                }  
                sqlsrv_free_stmt($stmt);  
                sqlsrv_close( $conn); 
                break;  
            } else {    
                // [A.4] Check whether the error code is on the list of allowed transients.  
                $isTransientError = false;  
                $errorCode = '';
                if (($errors = sqlsrv_errors()) != null) {
                    foreach ($errors as $error) {  
                        $errorCode = $error['code'];
                        $isTransientError = in_array($errorCode, $arrayOfTransientErrors);
                        if ($isTransientError) {
                            break;
                        }
                    }
                }  
                if (!$isTransientError) { 
                    // it is a static persistent error...
                    echo("Persistent error suffered with error code = $errorCode. Program will terminate.");  
                    echo "<br>";  
                    // [A.5] Either the connection attempt or the query command attempt suffered a persistent error condition.  
                    // Break the loop, let the hopeless program end.  
                    exit(0);  
                }  
                // [A.6] It is a transient error from an attempt to issue a query command.  
                // So let this method reloop and try again. However, we recommend that the new query  
                // attempt should start at the beginning and establish a new connection.  
                if ($cc >= $maxCountTriesConnectAndQuery) {  
                    echo "Transient errors suffered in too many retries - $cc. Program will terminate.";  
                    echo "<br>";  
                    exit(0);  
                }  
                echo("Transient error encountered with error code = $errorCode. Program might retry by itself.");    
                echo "<br>";  
                echo "$cc attempts so far. Might retry.";  
                echo "<br>";  
                // A very simple retry strategy, a brief pause before looping.  
                sleep(1*$secondsBetweenRetries);  
            }  
            // [A.3] All has gone well, so let the program end.  
        }  
    ?>
```
