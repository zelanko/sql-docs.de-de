---
title: Abrufen von Datums- und Uhrzeittypen als Zeichenfolgen mit dem SQLSRV-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as strings
ms.assetid: 58a974ea-4daf-4e3b-98ed-9731b9c9250f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8c3fbd475d5f7038d36ba17a9578713c3ed1b53
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993527"
---
# <a name="how-to-retrieve-date-and-time-types-as-strings-using-the-sqlsrv-driver"></a>Gewusst wie: Abrufen von Datums- und Uhrzeittypen als Zeichenfolgen mit dem SQLSRV-Treiber
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Wenn Sie den sqlsrv-Treiber für [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]verwenden, können Sie Datums-und Uhrzeit Typen (**smalldatetime**, **DateTime**, **Date**, **time**, **datetime2**und **DateTimeOffset**) als Zeichen folgen abrufen, indem Sie Folgendes angeben: -Option in der Verbindungs Zeichenfolge oder auf der Anweisungs Ebene:

```
'ReturnDatesAsStrings'=>true
```

Der Standardwert ist **false**, was bedeutet, dass die Typen **smalldatetime**, **datetime**, **date**, **time**, **datetime2** und **datetimeoffset** als [PHP DateTime](http://php.net/manual/en/class.datetime.php)-Objekte zurückgegeben werden. Wenn diese Option auf Anweisungs Ebene festgelegt wird, wird die Einstellung der Verbindungs Ebene überschrieben.

Der PDO_SQLSRV-Treiber gibt Datums-und Uhrzeit Typen standardmäßig als Zeichen folgen zurück. Informationen dazu, wie Sie diese als PHP DateTime-Objekte abrufen, finden Sie unter Gewusst [wie: Abrufen von Datums-und Uhrzeit Typen als PHP DateTime-Objekte mithilfe von PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md)

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt die Syntax, welche festlegt, dass die Datums- und Uhrzeittypen als Zeichenfolgen abgerufen werden.

```php
<?php
$serverName = "MyServer";
$connectionInfo = array("Database"=>"AdventureWorks", 'ReturnDatesAsStrings '=> true);
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

sqlsrv_close($conn);
?>
```

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, dass Sie verschiedene Datumsangaben als Zeichenfolge abrufen können, sofern Sie beim Abruf UTF-8 spezifizieren. Dies gilt auch, wenn die Verbindung mittels `"ReturnDatesAsStrings" => false` erstellt wurde.

```php
<?php
$serverName = "MyServer";
$connectionInfo = array("Database"=>"AdventureWorks", "ReturnDatesAsStrings" => false);
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

$tsql = "SELECT VersionDate FROM AWBuildVersion";

$stmt = sqlsrv_query($conn, $tsql);

if ($stmt === false) {
   echo "Error in statement preparation/execution.\n";
   die(print_r(sqlsrv_errors(), true));
}

sqlsrv_fetch($stmt);

// retrieve date as string
$date = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STRING("UTF-8"));

if ($date === false) {
   die(print_r(sqlsrv_errors(), true));
}

echo $date;

sqlsrv_close($conn);
?>
```

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Datumsangaben als Zeichenfolgen abgerufen werden können, indem UTF-8 und `"ReturnDatesAsStrings" => true` in der Verbindungszeichenfolge spezifiziert werden.

```php
<?php
$serverName = "MyServer";
$connectionInfo = array("Database"=>"AdventureWorks", 'ReturnDatesAsStrings'=> true, "CharacterSet" => 'utf-8');
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

$tsql = "SELECT VersionDate FROM AWBuildVersion";

$stmt = sqlsrv_query($conn, $tsql);

if ($stmt === false) {
   echo "Error in statement preparation/execution.\n";
   die(print_r(sqlsrv_errors(), true));
}

sqlsrv_fetch($stmt);

// retrieve date as string
$date = sqlsrv_get_field($stmt, 0);

if ($date === false) {
   die(print_r(sqlsrv_errors(), true));
}

echo $date;
sqlsrv_close($conn);
?>
```

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie das Datum als PHP-Typ abgerufen wird. `'ReturnDatesAsStrings'=> false` ist standardmäßig aktiviert.

```php
<?php
$serverName = "MyServer";
$connectionInfo = array("Database"=>"AdventureWorks");
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

$tsql = "SELECT VersionDate FROM AWBuildVersion";

$stmt = sqlsrv_query($conn, $tsql);

if ($stmt === false) {
   echo "Error in statement preparation/execution.\n";
   die(print_r(sqlsrv_errors(), true));
}

sqlsrv_fetch($stmt);

// retrieve date as a DateTime object, then convert to string using PHP's date_format function
$date = sqlsrv_get_field($stmt, 0);

if ($date === false) {
   die(print_r(sqlsrv_errors(), true));
}

$date_string = date_format($date, 'jS, F Y');
echo "Date = $date_string\n";

sqlsrv_close($conn);
?>
```

## <a name="example"></a>Beispiel
Die Option ReturnDatesAsStrings auf der Anweisungs Ebene überschreibt die entsprechende Verbindungs Option.

```php
<?php
$serverName = 'MyServer';
$connectionInfo = array('Database' => 'MyDatabase', 'ReturnDatesAsStrings' => false);
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

$tableName = 'MyTable';
$options = array('ReturnDatesAsStrings' => true);
$query = "SELECT DateTimeCol FROM $tableName";
$stmt = sqlsrv_prepare($conn, $query, array(), $options);
if ($stmt === false) {
   echo "Error in statement preparation/execution.\n";
   die(print_r(sqlsrv_errors(), true));
}
sqlsrv_execute($stmt);

// Expect the fetched value to be a string
$field = sqlsrv_get_field($stmt, 0);
echo $field . PHP_EOL;

sqlsrv_close($conn);
?>
```

## <a name="see-also"></a>Weitere Informationen
[Abrufen von Daten](../../connect/php/retrieving-data.md)

[Abrufen von Datums- und Uhrzeittypen als PHP-datetime-Objekte mit dem PDO_SSQLSRV-Treiber](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md)
