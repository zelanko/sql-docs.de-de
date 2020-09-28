---
title: 'Gewusst wie: Abrufen von Datums- und Uhrzeittypen als PHP-DateTime-Objekte mit dem PDO_SQLSRV-Treiber'
description: In diesem Thema wird beschrieben, wie Datums- und Uhrzeittypen als PHP-DateTime-Objekte abgerufen werden können, wenn der Microsoft PDO_SQLSRV-Treiber für PHP für SQL Server verwendet wird.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as datetime objects
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 507dc2a228419fb695d10a437681229ec6586f11
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680755"
---
# <a name="how-to-retrieve-date-and-time-types-as-php-datetime-objects-using-the-pdo_sqlsrv-driver"></a>Abrufen von Datums- und Uhrzeittypen als PHP-DateTime-Objekte mit dem SQLSRV-Treiber
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Diese Funktion wurde in Version 5.6.0 hinzugefügt und ist nur gültig, wenn Sie den PDO_SQLSRV-Treiber für die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] verwenden.

### <a name="to-retrieve-date-and-time-types-as-datetime-objects"></a>Abrufen von Datums- und Uhrzeittypen als DateTime-Objekte

Wenn Sie den PDO_SQLSRV-Treiber verwenden, werden Datums- und Uhrzeittypen (**smalldatetime**, **datetime**, **date**, **time**, **datetime2** und **datetimeoffset**) standardmäßig als Zeichenfolge zurückgegeben. Die beiden Attribute PDO::ATTR_STRINGIFY_FETCHES und PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE ändern daran nichts. Wenn Datums- und Uhrzeittypen als [PHP-DateTime-Objekte](http://php.net/manual/en/class.datetime.php) abgerufen werden sollen, legen Sie für das Verbindungs- oder Anweisungsattribut `PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE` die Einstellung **TRUE** (wahr) fest. Standardmäßig ist **FALSE** (falsch) angegeben.

> [!NOTE]
> Dieses Verbindungs-oder Anweisungsattribut gilt nur für das reguläre Abrufen von Datums-und Uhrzeittypen, da DateTime-Objekte nicht als Ausgabeparameter angegeben werden können.

## <a name="example---use-the-connection-attribute"></a>Beispiel: Verwenden des Verbindungsattributs
Aus Gründen der Übersichtlichkeit wird in den folgenden Beispielen die Prüfung auf Fehler weggelassen. Hier sehen Sie, welche Einstellungen für das Verbindungsattribut vorgenommen werden müssen:

```php
<?php
$server = 'myserver';
$databaseName = 'mydatabase';
$username = 'myusername';
$passwd = 'mypasword';
$tableName = 'mytable';

$conn = new PDO("sqlsrv:Server = $server; Database = $databaseName", $username, $passwd);

// To set the connection attribute
$conn->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$query = "SELECT DateTimeCol FROM $tableName";
$stmt = $conn->prepare($query);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_ASSOC);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-attribute"></a>Beispiel: Verwenden des Anweisungsattributs
Hier sehen Sie, welche Einstellungen für das Anweisungsattribut vorgenommen werden müssen:

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");
$query = "SELECT DateTimeCol FROM myTable";
$stmt = $conn->prepare($query);
$stmt->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_NUM);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-option"></a>Beispiel: Verwenden der Anweisung als Option
Sie können das Anweisungsattribut auch als Option angeben:

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");

$dateObj = null;
$query = "SELECT DateTimeCol FROM aTable";
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => true);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateObj, PDO::PARAM_LOB);
$row = $stmt->fetch(PDO::FETCH_BOUND);
var_dump($dateObj);

unset($stmt);
unset($conn);
?>
```

## <a name="example---retrieve-datetime-types-as-strings"></a>Beispiel: Abrufen von datetime-Typen als Strings
Das folgende Beispiel zeigt, wie Sie das Gegenteil erreichen. Diese Funktion ist jedoch nicht wirklich nötig, da standardmäßig FALSE festgelegt ist:

```php
<?php
$database = "MyData";
$conn = new PDO("sqlsrv:server = (local); Database = $database");

$dateStr = null;
$query = 'SELECT DateTimeCol FROM table1';
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => false);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateStr);
$row = $stmt->fetch(PDO::FETCH_BOUND);
echo $dateStr . PHP_EOL;

unset($stmt);
unset($conn);
?>
```

## <a name="see-also"></a>Weitere Informationen
[Abrufen von Daten](../../connect/php/retrieving-data.md)

[Abrufen von Datums- und Uhrzeittypen als Zeichenfolgen mit dem SQLSRV-Treiber](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)
