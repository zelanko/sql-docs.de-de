---
title: 'Vorgehensweise: Abrufen von Datums- und Uhrzeittypen als PHP-DateTime-Objekte mit dem Treiber PDO_SQLSRV | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as datetime objects
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 54e5b5c9c1ba59ed64db740fbbb1a643e7cb1b2c
ms.sourcegitcommit: c1105ce638078d2c941cd656b34f78486e6b2d89
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676522"
---
# <a name="how-to-retrieve-date-and-time-types-as-php-datetime-objects-using-the-pdosqlsrv-driver"></a>Vorgehensweise: Abrufen von Datums- und Uhrzeittypen als PHP-DateTime-Objekte mit dem PDO_SQLSRV-Treiber
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Hinzugefügt in Version 5.6.0, dieses Feature ist nur gültig, bei den PDO_SQLSRV-Treiber für die Verwendung der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

### <a name="to-retrieve-date-and-time-types-as-datetime-objects"></a>Zum Abrufen von Datums- und Uhrzeittypen als DateTime-Objekte

Bei Verwendung des PDO_SQLSRV, Datums- und Uhrzeittypen (**Smalldatetime**, **"DateTime"**, **Datum**, **Zeit**, **datetime2**, und **Datetimeoffset**) werden standardmäßig als Zeichenfolgen zurückgegeben. Weder das PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE-Attribut als auch die PDO::ATTR_STRINGIFY_FETCHES hat keinerlei Auswirkungen. Zum Abrufen von Datums- und Uhrzeittypen als [PHP-DateTime](http://php.net/manual/en/class.datetime.php) Objekte, legen Sie das Attribut Verbindung oder Anweisung `PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE` zu **"true"** (es ist **"false"** standardmäßig).

> [!NOTE]
> Dieses Programm oder -Anweisungsattribut gilt nur, um reguläre Abrufen von Datums- und Uhrzeittypen, da DateTime-Objekte können nicht als Output-Parameter angegeben werden.

## <a name="example---use-the-connection-attribute"></a>Beispiel: Verwenden Sie das Verbindungsattribut
In den folgenden Beispielen lassen Fehler beim Überprüfen der aus Gründen der Übersichtlichkeit. Veranschaulicht, wie das Verbindungsattribut festgelegt:

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

## <a name="example---use-the-statement-attribute"></a>Beispiel: Verwenden Sie das Anweisungsattribut
Dieses Beispiel zeigt, wie das Anweisungsattribut festgelegt wird:

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

## <a name="example---use-the-statement-option"></a>Beispiel: verwenden die Option-Anweisung
Alternativ kann das Anweisungsattribut als eine Option festgelegt werden:

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

## <a name="example---retrieve-datetime-types-as-strings"></a>Beispiel: Datetime-Datentypen als Zeichenfolgen abrufen
Das folgende Beispiel zeigt, wie Sie das Gegenteil zu erreichen (die nicht wirklich notwendig ist, da sie standardmäßig "false" ist):

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