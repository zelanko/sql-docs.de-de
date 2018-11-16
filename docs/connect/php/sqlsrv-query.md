---
title: Sqlsrv_query | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_query
apitype: NA
helpviewer_keywords:
- sqlsrv_query
- executing queries
- API Reference, sqlsrv_query
ms.assetid: 9fa7c4c8-4da8-4299-9893-f61815055aa3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19d7f4d6562f64061f01bf0ff7a73fcd03a4f63c
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606250"
---
# <a name="sqlsrvquery"></a>sqlsrv_query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Bereitet eine Anweisung vor und führt diese aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_query(resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>Parameter  
*$conn*: Die mit der vorbereiteten Anweisung verknüpfte Verbindungsressource.  
  
*$tsql:* Der Transact-SQL-Ausdruck, der der vorbereiteten Anweisung entspricht.  
  
*$params* [OPTIONAL]: Ein **Array** von Werten, die Parametern in einer parametrisierten Abfrage entsprechen. Jedes Element des Arrays kann eines der folgenden sein:
  
-   Ein Literalwert  
  
-   Eine PHP-Variable.  
  
-   Ein **Array** mit der folgenden Struktur:  
  
    ```  
    array($value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    Die Beschreibung für jedes Element des Arrays finden Sie in der folgenden Tabelle:  
  
    |Element|und Beschreibung|  
    |-----------|---------------|  
    |*$value*|Ein Literalwert, eine PHP-Variable oder eine PHP-Variable als Verweis.|  
    |*$direction*[OPTIONAL]|Eine der folgenden verwendeten **SQLSRV_PARAM_\***-Konstanten, um die Parameterrichtung anzugeben: **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. Der Standardwert ist **SQLSRV_PARAM_IN**.<br /><br />Weitere Informationen zu PHP-Konstanten finden Sie unter [Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[OPTIONAL]|Eine **SQLSRV_PHPTYPE_\***-Konstante, die den PHP-Datentyp des zurückgegebenen Werts angibt.<br /><br />Weitere Informationen zu PHP-Konstanten finden Sie unter [Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$sqlType*[OPTIONAL]|Eine **SQLSRV_SQLTYPE_\***-Konstante, die den SQL Server-Datentyp des Eingabewerts angibt.<br /><br />Weitere Informationen zu PHP-Konstanten finden Sie unter [Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
  
*$options* [OPTIONAL]: Ein assoziatives Array, das Abfrageeigenschaften festlegt. Die folgenden Schlüssel werden unterstützt:  
  
|Key|Unterstützte Werte|und Beschreibung|  
|-------|--------------------|---------------|  
|QueryTimeout|Ein positiver ganzzahliger Wert|Legt das Abfragetimeout in Sekunden fest. Standardmäßig wartet der Treiber unbegrenzt auf Ergebnisse.|  
|SendStreamParamsAtExec|**WAHR** oder **FALSCH**<br /><br />Der Standardwert ist **true**.|Konfiguriert den Treiber, um alle Streamdaten bei der Ausführung zu senden (**TRUE**) oder Streamdaten in Blöcken (**FALSE**) zu senden. In der Standardeinstellung ist dieser Wert mit **true**festgelegt. Weitere Informationen finden Sie unter [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md).|  
|Bildlauffähigkeit|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|Weitere Informationen zu diesen Werten finden Sie unter [Festlegen eines Cursortyps und Zeilenauswahl](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|  
  
## <a name="return-value"></a>Rückgabewert  
Eine Anweisungsressource. Wenn die Anweisung nicht erstellt und/oder ausgeführt werden kann, wird **FALSE** zurückgegeben.  
  
## <a name="remarks"></a>Remarks  
Die **sqlsrv_query**-Funktion eignet sich ideal für einmalige Abfragen und sollte auch die Standardauswahl sein, um Abfragen auszuführen, es sei denn, es gelten besondere Umstände. Diese Funktion bietet eine optimierte Methode zum Ausführen einer Abfrage mit einem Minimum von Codes. Die **sqlsrv_query** -Funktion führt jeweils eine Anweisungsvorbereitung und eine Anweisungsausführung durch und kann verwendet werden, um parametrisierte Abfragen auszuführen.  
  
Weitere Informationen finden Sie unter [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Beispiel  
Im folgenden Beispiel wird eine einzelne Zeile in die *Sales.SalesOrderDetail* -Tabelle der AdventureWorks-Datenbank eingefügt. Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
> [!NOTE]  
> Obwohl folgendes Beispiel eine INSERT-Anweisung verwendet, um die Verwendung von **sqlsrv_query** für einmaliges Ausführen einer Anweisung zu demonstrieren, gilt das Konzept für jede Transact-SQL-Anweisung.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "INSERT INTO Sales.SalesOrderDetail   
        (SalesOrderID,   
         OrderQty,   
         ProductID,   
         SpecialOfferID,   
         UnitPrice,   
         UnitPriceDiscount)  
        VALUES   
        (?, ?, ?, ?, ?, ?)";  
  
/* Set parameter values. */  
$params = array(75123, 5, 741, 1, 818.70, 0.00);  
  
/* Prepare and execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if ($stmt) {  
    echo "Row successfully inserted.\n";  
} else {  
    echo "Row insertion failed.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="example"></a>Beispiel  
Im folgenden Beispiel wird ein Feld in der *Sales.SalesOrderDetail*-Tabelle der AdventureWorks-Datenbank aktualisiert. Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = (?)   
         WHERE SalesOrderDetailID = (?)";  
  
/* Assign literal parameter values. */  
$params = array(5, 10);  
  
/* Execute the query. */  
if (sqlsrv_query($conn, $tsql, $params)) {  
    echo "Statement executed.\n";  
} else {  
    echo "Error in statement execution.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close($conn);  
?>  
```  
  
> [!NOTE]
> Es wird empfohlen, die Zeichenfolgen als Eingabe verwendet, bei der Bindung von Werten, eine [decimal oder numeric-Spalte](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) auf Richtigkeit und Genauigkeit zu gewährleisten, wie PHP Genauigkeit für eingeschränkten [Gleitkommazahlen](https://php.net/manual/en/language.types.float.php). Dasselbe gilt auch für Bigint-Spalten, insbesondere, wenn die Werte außerhalb des Bereichs von sind ein [Ganzzahl](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="example"></a>Beispiel  
In diesem Codebeispiel wird veranschaulicht, wie einen decimal-Wert als Eingabeparameter gebunden wird.  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
     echo "Could not connect.\n";  
     die(print_r(sqlsrv_errors(), true));  
}  

// Assume TestTable exists with a decimal field 
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_query($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```

## <a name="example"></a>Beispiel
In diesem Codebeispiel wird veranschaulicht, wie zum Erstellen einer Tabelle von [Sql_variant](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql) Typen und die eingefügten Daten abzurufen.

```
<?php
$server = 'serverName';
$dbName = 'databaseName';
$uid = 'yourUserName';
$pwd = 'yourPassword';

$options = array("Database"=>$dbName, "UID"=>$uid, "PWD"=>$pwd);
$conn = sqlsrv_connect($server, $options);
if($conn === false) {
    die(print_r(sqlsrv_errors(), true));
}

$tableName = 'testTable';
$query = "CREATE TABLE $tableName ([c1_int] sql_variant, [c2_varchar] sql_variant)";

$stmt = sqlsrv_query($conn, $query);
if($stmt === false) {
    die(print_r(sqlsrv_errors(), true));
}
sqlsrv_free_stmt($stmt);

$query = "INSERT INTO [$tableName] (c1_int, c2_varchar) VALUES (1, 'test_data')";
$stmt = sqlsrv_query($conn, $query);
if($stmt === false) {
    die(print_r(sqlsrv_errors(), true));
}
sqlsrv_free_stmt($stmt);

$query = "SELECT * FROM $tableName";
$stmt = sqlsrv_query($conn, $query);

if(sqlsrv_fetch($stmt) === false) {
    die(print_r(sqlsrv_errors(), true));
}

$col1 = sqlsrv_get_field($stmt, 0);
echo "First field:  $col1 \n";

$col2 = sqlsrv_get_field($stmt, 1);
echo "Second field:  $col2 \n";

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

?>
```

Die erwartete Ausgabe wäre:

```
First field:  1
Second field:  test_data
```

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  

[Gewusst wie: Ausführen von parametrisierten Abfragen](../../connect/php/how-to-perform-parameterized-queries.md)  

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)  

[Gewusst wie: Streamen von Daten](../../connect/php/how-to-send-data-as-a-stream.md)  

[Verwenden direktionaler Parameter](../../connect/php/using-directional-parameters.md)  

  
