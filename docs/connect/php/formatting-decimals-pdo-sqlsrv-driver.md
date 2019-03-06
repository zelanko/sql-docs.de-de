---
title: Formatieren von Dezimalzeichenfolgen und Währungswerte (PDO_SQLSRV-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- formatting, decimal types, money values
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 35626c192c3d74ad0201cee3c5e97adbce92a3aa
ms.sourcegitcommit: c1105ce638078d2c941cd656b34f78486e6b2d89
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676528"
---
# <a name="formatting-decimal-strings-and-money-values-pdosqlsrv-driver"></a>Formatieren von Dezimalzeichenfolgen und Währungswerte (PDO_SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Beibehalten der Genauigkeit der [Datentypen decimal und numeric](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) immer als Zeichenfolgen mit genauen genauigkeiten und Skalierungen abgerufen werden. Wenn Sie einen beliebigen Wert kleiner als 1 ist, ist die führende 0 (null) nicht vorhanden. Es ist identisch mit Money- und Smallmoney-Feldern wie Dezimalfelder mit festen gleich 4 Dezimalstellen.

## <a name="add-leading-zeroes-if-missing"></a>Hinzufügen von führenden Nullen bei fehlen
Ab Version 5.6.0, die Verbindung oder Anweisungsattribut `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` ermöglicht dem Benutzer Dezimalzeichenfolgen zu formatieren. Dieses Attribut erwartet, dass einen booleschen Wert (true oder false), und wirkt sich nur auf die Formatierung der decimal oder numeric-Werte in den abgerufenen Ergebnissen. Das heißt, hat dieses Attribut keine Auswirkungen auf andere Vorgänge wie das Einfügen oder aktualisieren.

Standardmäßig ist `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` **false**. Wenn auf True festgelegt, die führenden Nullen in decimal Zeichenfolgen für jeden decimal-Wert kleiner als 1 hinzugefügt werden.

## <a name="configure-number-of-decimal-places"></a>Konfigurieren Sie die Anzahl der Dezimalstellen
Mit `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` aktiviert ist, eine andere Verbindung oder Anweisung Attribut `PDO::SQLSRV_ATTR_DECIMAL_PLACES`, ermöglicht es Benutzern, die Anzahl der Dezimalstellen zu konfigurieren, Anzeigen von Money und Smallmoney-Daten. Er akzeptiert ganzzahlige Werte im Bereich [0, 4], und runden auftreten, wenn angezeigt. Die zugrunde liegenden Money-Daten bleiben jedoch gleich.

Die Anweisungsattribute überschreiben immer die entsprechenden Einstellungen. Beachten Sie, dass die `PDO::SQLSRV_ATTR_DECIMAL_PLACES` Option **nur** wirkt sich auf Money-Daten und `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` muss festgelegt werden, auf "true". Andernfalls formatieren ist deaktiviert unabhängig von `PDO::SQLSRV_ATTR_DECIMAL_PLACES` festlegen.

> [!NOTE]
> Da Felder Money "oder" Smallmoney Skalierung 4 enthalten, festlegen `PDO::SQLSRV_ATTR_DECIMAL_PLACES` eine negative Zahl oder einen beliebigen Wert größer als 4 werden ignoriert. Es wird nicht empfohlen, alle formatierte Money-Daten als Eingabe für eine beliebige Berechnung verwenden.

### <a name="to-set-the-connection-attributes"></a>Festlegen der Verbindungsattribute

-   Festlegen von Attributen zum Zeitpunkt der Verbindung:

    ```php
    $attrs = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => true,
                   PDO::SQLSRV_ATTR_DECIMAL_PLACES => 2);

    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password, $attrs);
    ```

-   Legen Sie Attribute Post-Verbindung:

    ```php
    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password);
    $conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
    $conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);
    ```

## <a name="example---format-money-data"></a>Beispiel: Format Money-Daten
Das folgende Beispiel zeigt, wie Sie Geld mit abrufen [pdostatement:: Bindcolumn](../../connect/php/pdostatement-bindcolumn.md):

```php
<?php
$database = "myDB";
$server = "(local)";
$conn = new PDO( "sqlsrv:server=$server; Database = $database", "", "");
$conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);

$numDigits = 3;
$query = "SELECT smallmoney1 FROM aTable";
$options = array(PDO::SQLSRV_ATTR_DECIMAL_PLACES => $numDigits);
$stmt = $conn->prepare($query, $options);
$stmt->execute();

$stmt->bindColumn('smallmoney1', $field);
$result = $stmt->fetch(PDO::FETCH_BOUND);
echo $field;    // expect a number string with 3 decimal places

unset($stmt);
unset($conn);
?>
```

## <a name="example---override-connection-attributes"></a>Beispiel: Verbindungsattribute außer Kraft setzen
Das folgende Beispiel zeigt, wie die Verbindungsattribute überschrieben wird:

```php
<?php
$database = 'myDatabase';
$server = 'myServer';
$username = 'myuser';
$password = 'mypassword'

$conn = new PDO("sqlsrv:server=$server; Database = $database", $username, $password);
$conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
$conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);

$query = 'SELECT smallmoney1 FROM testTable1';
$options = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => false);
$stmt = $conn->prepare($query, $options);
$stmt->execute();

$stmt->bindColumn('smallmoney1', $field);
$result = $stmt->fetch(PDO::FETCH_BOUND);  
echo $field;   // expect a number string showing the original scale -- 4 decimal places

unset($stmt);
unset($conn);
?>
```

## <a name="see-also"></a>Weitere Informationen
[Formatieren von Dezimalzeichenfolgen und Währungswerte (SQLSRV-Treiber)](../../connect/php/formatting-decimals-sqlsrv-driver.md)

[Abrufen von Daten](../../connect/php/retrieving-data.md)
