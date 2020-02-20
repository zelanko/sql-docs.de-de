---
title: 'Gewusst wie: Senden von Daten als Stream | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data
- streaming data
ms.assetid: ab6b95d6-b6e6-4bd7-a18c-50f2918f7532
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d524e7c7f00b08ce636f8a3b7b945f3e8b349af0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67936407"
---
# <a name="how-to-send-data-as-a-stream"></a>Gewusst wie: Senden von Daten als Stream
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] nutzt PHP-Datenströme, um große Objekte an den Server zu senden. In diesem Thema wird erklärt, wie Sie Daten in Strömen senden können. Im ersten Beispiel wird mithilfe des SQLSRV-Treibers die Standardvorgehensweise veranschaulicht, bei der alle Datenstromdaten direkt bei der Abfrageausführung gesendet werden. Im zweiten Beispiel wird mithilfe des SQLSRV-Treibers veranschaulicht, wie Sie bis zu 8 Kilobyte (8 KB) an Streamdaten gleichzeitig an den Server senden können.  
  
Im dritten Beispiel wird veranschaulicht, wie Sie mithilfe des PDO_SQLSRV-Treibers Datenstromdaten an den Server senden.  
  
## <a name="example-sending-stream-data-at-execution"></a>Beispiel: Senden von Streamdaten bei der Ausführung
Im folgenden Beispiel wird eine einzelne Zeile in die *Production.ProductReview* Tabelle der AdventureWorks-Datenbank eingefügt. Die Kundenkommentare ($*comments*) werden mithilfe der PHP-Funktion [fopen](https://php.net/manual/en/function.fopen.php) als Stream geöffnet und bei der Ausführung der Abfrage dann an den Server gestreamt.  
  
Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Die Ausgabe wird in die Konsole geschrieben.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if ($conn === false) {
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "INSERT INTO Production.ProductReview (ProductID,   
                                               ReviewerName,  
                                               ReviewDate,  
                                               EmailAddress,  
                                               Rating,  
                                               Comments)  
         VALUES (?, ?, ?, ?, ?, ?)";  
  
/* Set the parameter values and put them in an array.  
Note that $comments is opened as a stream. */  
$productID = '709';  
$name = 'Customer Name';  
$date = date("Y-m-d");  
$email = 'customer@name.com';  
$rating = 3;  
$data = 'Insert any lengthy comment here.';
$comments = fopen('data:text/plain,'.urlencode($data), 'r');
$params = array($productID, $name, $date, $email, $rating, $comments);
  
/* Execute the query. All stream data is sent upon execution.*/  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if ($stmt === false) {
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
} else {
     echo "The query was successfully executed.";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example-sending-stream-data-using-sqlsrv_send_stream_data"></a>Beispiel: Senden von Streamdaten mithilfe von sqlsrv_send_stream_data
Das nächste Beispiel ähnelt dem vorherigen Beispiel, allerdings wurde hier die Standardvorgehensweise zum Senden von Streamdaten bei der Ausführung der Abfrage deaktiviert. Im Beispiel wird [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md) verwendet, um Datenstromdaten an den Server zu senden. Mit jedem Aufruf werden bis zu acht Kilobyte (8 KB) Daten an **sqlsrv_send_stream_data** gesendet. Das Skript zählt die Anzahl der Aufrufe durch **sqlsrv_send_stream_data** und zeigt sie in der Konsole an.  
  
Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Die Ausgabe wird in die Konsole geschrieben.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if ($conn === false) {
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "INSERT INTO Production.ProductReview (ProductID,   
                                               ReviewerName,  
                                               ReviewDate,  
                                               EmailAddress,  
                                               Rating,  
                                               Comments)  
         VALUES (?, ?, ?, ?, ?, ?)";  
  
/* Set the parameter values and put them in an array.  
Note that $comments is opened as a stream. */  
$productID = '709';  
$name = 'Customer Name';  
$date = date("Y-m-d");  
$email = 'customer@name.com';  
$rating = 3;  
$data = 'Insert any lengthy comment here.';
$comments = fopen('data:text/plain,'.urlencode($data), 'r');
$params = array($productID, $name, $date, $email, $rating, $comments);  
  
/* Turn off the default behavior of sending all stream data at  
execution. */  
$options = array("SendStreamParamsAtExec" => 0);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params, $options);  
if ($stmt === false) {
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Send up to 8K of parameter data to the server with each call to  
sqlsrv_send_stream_data. Count the calls. */  
$i = 1;  
while (sqlsrv_send_stream_data($stmt)) {
     echo "$i call(s) made.\n";  
     $i++;  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Obwohl in den Beispielen in diesem Thema nur Zeichendaten an den Server gesendet werden, können Daten aller Formate als Strom gesendet werden. Sie können die in diesem Thema erläuterten Techniken beispielsweise nutzen, um Bilder im Binärformat als Ströme zu senden.  
  
## <a name="example-sending-an-image-as-a-stream"></a>Beispiel: Senden eines Image als Stream 
  
```  
<?php  
   $server = "(local)";   
   $database = "Test";  
   $conn = new PDO( "sqlsrv:server=$server;Database = $database", "", "");  
  
   $binary_source = fopen( "data://text/plain,", "r");  
  
   $stmt = $conn->prepare("insert into binaries (imagedata) values (?)");  
   $stmt->bindParam(1, $binary_source, PDO::PARAM_LOB);   
  
   $conn->beginTransaction();  
   $stmt->execute();  
   $conn->commit();  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Aktualisieren von Daten &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

[Abrufen von Daten als Stream mit dem SQLSRV-Treiber](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  
