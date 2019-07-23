---
title: Abrufen von Datums- und Uhrzeittypen als PHP-DateTime-Objekte mit dem SQLSRV-Treiber | Microsoft-Dokumentation
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
manager: v-mabarw
ms.openlocfilehash: 165e91cee3b0b4592f9b746f8b35b46bc73bce50
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264567"
---
# <a name="how-to-retrieve-date-and-time-types-as-php-datetime-objects-using-the-pdosqlsrv-driver"></a>Abrufen von Datums- und Uhrzeittypen als PHP-DateTime-Objekte mit dem SQLSRV-Treiber
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Diese Funktion, die in Version 5.6.0 hinzugefügt wurde, ist nur gültig, wenn der PDO_SQLSRV [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]-Treiber für die verwendet wird.

### <a name="to-retrieve-date-and-time-types-as-datetime-objects"></a>So rufen Sie Datums-und Uhrzeit Typen als DateTime-Objekte ab

Bei Verwendung von PDO_SQLSRV werden Datums-und Uhrzeit Typen (**smalldatetime**, **DateTime**, **Date**, **time**, **datetime2**und **DateTimeOffset**) standardmäßig als Zeichen folgen zurückgegeben. Weder das PDO:: ATTR_STRINGIFY_FETCHES-Attribut noch das PDO:: SQLSRV_ATTR_FETCHES_NUMERIC_TYPE-Attribut hat keinerlei Auswirkung. Um Datums-und Uhrzeit Typen als PHP- [DateTime](http://php.net/manual/en/class.datetime.php) -Objekte abzurufen, legen Sie das Verbindungs- `PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE` oder Anweisungs Attribut auf " **true** " fest (Standardmäßig ist dies " **false** ").

> [!NOTE]
> Dieses Verbindungs-oder Anweisungs Attribut gilt nur für das reguläre Abrufen von Datums-und Uhrzeit Typen, da DateTime-Objekte nicht als Ausgabeparameter angegeben werden können.

## <a name="example---use-the-connection-attribute"></a>Beispiel: Verwenden des Connection-Attributs
In den folgenden Beispielen wird die Fehlerüberprüfung für die Übersichtlichkeit ausgelassen. Dieses Beispiel zeigt, wie das Verbindungs Attribut festgelegt wird:

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

## <a name="example---use-the-statement-attribute"></a>Beispiel: Verwenden des Anweisungs Attributs
Dieses Beispiel zeigt, wie das Anweisungs Attribut festgelegt wird:

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

## <a name="example---use-the-statement-option"></a>Beispiel: Verwenden der Anweisungs Option
Alternativ kann das Anweisungs Attribut als Option festgelegt werden:

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

## <a name="example---retrieve-datetime-types-as-strings"></a>Beispiel: Abrufen von DateTime-Typen als Zeichen folgen
Im folgenden Beispiel wird gezeigt, wie das Gegenteil erreicht wird (was nicht wirklich notwendig ist, weil es standardmäßig false ist):

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