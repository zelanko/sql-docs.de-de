---
title: 'Schritt 4: Herstellen einer resilientes Verbindung mit SQL mit PHP | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8013474f-48e9-43d5-ab89-7b0504044468
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 002c27145360e0877d4e1bff816c25070247ddd8
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874376"
---
# <a name="step-4-connect-resiliently-to-sql-with-php"></a>Schritt 4: Herstellen belastbarer SQL-Verbindungen mit PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

  
Das Demo Programm ist so konzipiert, dass ein vorübergehender Fehler (bei dem es sich um einen beliebigen Fehlercode mit dem Präfix "08" handelt, wie in diesem [Anhang](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes)aufgeführt) während eines Verbindungsversuchs zu einer Wiederholung führt. Ein vorübergehender Fehler während des Abfrage Befehls bewirkt jedoch, dass das Programm die Verbindung verwirft und eine neue Verbindung erstellt, bevor der Abfragebefehl erneut versucht wird. Diese Entwurfs Auswahl wird weder empfohlen noch empfohlen. Das Demo Programm veranschaulicht einen Teil der Entwurfs Flexibilität, die Ihnen zur Verfügung steht.  
  
Die Länge dieses Code Beispiels ist hauptsächlich auf die Logik zum Abfangen von Ausnahmen zurückzuführen.   
  
Die [sqlsrv_query ()](../../connect/php/sqlsrv-query.md) -Funktion kann verwendet werden, um ein Resultset aus einer Abfrage für die SQL-Datenbank abzurufen. Diese Funktion akzeptiert im Wesentlichen alle Abfrage-und Verbindungs Objekte und gibt ein Resultset zurück, das mit der Verwendung von [sqlsrv_fetch_array ()](../../connect/php/sqlsrv-fetch-array.md)durchlaufen werden kann. 
  
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
