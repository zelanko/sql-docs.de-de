---
title: 'Gewusst wie: Senden und Abrufen von ASCII-Daten unter Linux und macOS (SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, ASCII data
- sending data
- linux
- macOS
author: yitam
ms.author: v-yitam
manager: v-mabarw
ms.openlocfilehash: 9edd73f5ef01d1d3f22db78400cc3c204efe1379
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68251906"
---
# <a name="how-to-send-and-retrieve-ascii-data-in-linux-and-macos"></a>Gewusst wie: Senden und Abrufen von ASCII-Daten unter Linux und macOS 
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Artikel wird vorausgesetzt, dass die ASCII-Gebietsschemata (nicht UTF-8) auf Ihren Linux- oder macOS-Systemen generiert oder installiert wurden. 

So senden Sie ASCII-Zeichensätze an den Server oder rufen dort ab:  

1.  Wenn das gewünschte Gebietsschema nicht der Standard in Ihrer Systemumgebung ist, stellen Sie sicher, dass Sie `setlocale(LC_ALL, $locale)` aufrufen, bevor Sie die erste Verbindung herstellen. Die PHP-Funktion setlocale() ändert das Gebietsschema nur für das aktuelle Skript. Wenn sie nach dem Herstellen der ersten Verbindung aufgerufen wird, wird sie möglicherweise ignoriert.
 
2.  Wenn Sie den SQLSRV-Treiber verwenden, können Sie `'CharacterSet' => SQLSRV_ENC_CHAR` als Verbindungsoption angeben, aber dieser Schritt ist optional, da es sich um die Standardcodierung handelt.

3.  Bei Verwendung des PDO_SQLSRV-Treibers haben Sie zwei Möglichkeiten. Erstens können Sie beim Herstellen der Verbindung `PDO::SQLSRV_ATTR_ENCODING` auf `PDO::SQLSRV_ENCODING_SYSTEM` festlegen (ein Beispiel für das Festlegen einer Verbindungsoption finden Sie unter [PDO::__construct](../../connect/php/pdo-construct.md)). Alternativ können Sie nach erfolgreicher Verbindungsherstellung diese Zeile `$conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);` hinzufügen. 
  
Wenn Sie die Codierung einer Verbindungsressource (in SQLSRV) oder eines Verbindungsobjekts (PDO_SQLSRV) angeben, geht der Treiber davon aus, dass für die anderen Verbindungsoptions-Zeichenfolgen dieselbe Codierung verwendet wird. Auch beim Servernamen und den Abfragezeichenfolgen geht er vom selben Zeichensatz aus.  
  
Die Standardcodierung für den PDO_SQLSRV-Treiber ist UTF-8 (PDO::SQLSRV_ENCODING_UTF8), anders als der SQLSRV-Treiber. Weitere Informationen zu diesen Konstanten finden Sie unter [Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md). 
  
## <a name="example"></a>Beispiel  
In den folgenden Beispielen wird veranschaulicht, wie ASCII-Daten mithilfe der PHP-Treiber für SQL Server gesendet und abgerufen werden, indem vor dem Herstellen der Verbindung ein bestimmtes Gebietsschema angegeben wird. Die Gebietsschemata auf verschiedenen Linux-Plattformen können anders benannt werden als die gleichen Gebietsschemata in macOS. Beispielsweise ist das Gebietsschema „USA ISO-8859-1 (Lateinisch 1)“ in Linux `en_US.ISO-8859-1`, während es in macOS `en_US.ISO8859-1` ist.
  
In den Beispielen wird davon ausgegangen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Server installiert ist. Wenn die Beispiele über den Browser ausgeführt werden, werden alle Ausgaben im Browser geschrieben.  
  
```  
<?php  
  
// SQLSRV Example
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';
$connectionInfo = array('Database'=>'Test', 'UID'=>$uid, 'PWD'=>$pwd);
$conn = sqlsrv_connect($serverName, $connectionInfo);
  
if ($conn === false) {
    echo "Could not connect.<br>";  
    die(print_r(sqlsrv_errors(), true));
}  
  
// Set up the Transact-SQL query to create a test table
//   
$stmt = sqlsrv_query($conn, "CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");

// Insert data using a parameter array 
//
$tsql = "INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (?, ?)";
  
// Execute the query, $value being some ASCII string
//   
$stmt = sqlsrv_query($conn, $tsql, array(1, array($value, SQLSRV_PARAM_IN, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR))));
  
if ($stmt === false) {
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
else {  
    echo "The insertion was successfully executed.<br>";  
}  
  
// Retrieve the newly inserted data
//   
$stmt = sqlsrv_query($conn, "SELECT * FROM Table1");
$outValue = null;  
if ($stmt === false) {  
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
// Retrieve and display the data
//   
if (sqlsrv_fetch($stmt)) {  
    $outValue = sqlsrv_get_field($stmt, 1, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR));
    echo "Value: " . $outValue . "<br>";
    if ($value !== $outValue) {
        echo "Data retrieved, \'$outValue\', is unexpected!<br>";
    }
}  
else {  
    echo "Error in fetching data.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Free statement and connection resources
//   
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
```
<?php  
  
// PDO_SQLSRV Example:
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';

try {
    $conn = new PDO("sqlsrv:Server=$serverName;Database=$database;", $uid, $pwd);
    $conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);
    
    // Set up the Transact-SQL query to create a test table
    //   
    $stmt = $conn->query("CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");
    
    // Insert data using parameters, $value being some ASCII string
    //
    $stmt = $conn->prepare("INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (:var1, :var2)");
    $stmt->bindValue(1, 1);
    $stmt->bindParam(2, $value);
    $stmt->execute();
    
    // Retrieve and display the data
    //
    $stmt = $conn->query("SELECT * FROM [Table1]");
    $outValue = null;
    if ($row = $stmt->fetch()) {
        $outValue = $row[1];
        echo "Value: " . $outValue . "<br>";
        if ($value !== $outValue) {
            echo "Data retrieved, \'$outValue\', is unexpected!<br>";
        }
    }
} catch (PDOException $e) {
    echo $e->getMessage() . "<br>";
} finally {
    // Free statement and connection resources
    //
    unset($stmt);
    unset($conn);
}

?>  
```  

## <a name="see-also"></a>Weitere Informationen  
[Abrufen von Daten](../../connect/php/retrieving-data.md)  
[Arbeiten mit UTF-8-Daten](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)
[Aktualisieren von Daten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  
[Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Beispielanwendung &#40;SQLSRV-Treiber&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
  
