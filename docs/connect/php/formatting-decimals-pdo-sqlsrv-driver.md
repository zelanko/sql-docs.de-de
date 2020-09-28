---
title: Formatieren von Dezimalzeichenfolgen und Geldwerten (PDO_SQLSRV-Treiber)
description: Erfahren Sie, wie Sie bei Verwendung des PDO_SQLSRV-Treibers die Attribute PDO::SQLSRV_ATTR_FORMAT_DECIMALS und SQLSRV_ATTR_DECIMAL_PLACES verwenden, um Dezimal- oder Geldwerte zu formatieren.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- formatting, decimal types, money values
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae61b239fca2a923645b9de963309c62a3919b3d
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680655"
---
# <a name="formatting-decimal-strings-and-money-values-pdo_sqlsrv-driver"></a>Formatieren von Dezimalzeichenfolgen und Geldwerten (PDO_SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Für maximale Genauigkeit werden [Dezimal- oder numerische Typen](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) immer als Zeichenfolgen mit der exakten Anzahl von Zeichen und Dezimalzeichen abgerufen. Wenn ein Wert geringer als 1 ist, fehlt die führende Null. Gleiches gilt für die Felder „money“ und „smallmoney“, da es sich um Dezimalfelder mit einer festen Anzahl von Dezimalzeichen (4) handelt.

## <a name="add-leading-zeroes-if-missing"></a>Hinzufügen von fehlenden führenden Nullen
Ab Version 5.6.0 können Benutzer Dezimalzeichenfolgen über das Verbindungs- oder Anweisungsattribut `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` formatieren. Dieses Attribut wird mit einem booleschen Wert (true oder false) verwendet und wirkt sich ausschließlich auf die Formatierung der Dezimal- oder numerischen Werte in den abgerufenen Ergebnissen aus. Mit anderen Worten, es hat keine Auswirkungen auf andere Vorgänge wie beispielsweise Einfüge- oder Aktualisierungsvorgänge.

Standardmäßig ist `PDO::SQLSRV_ATTR_FORMAT_DECIMALS`**false**. Bei Festlegung auf „true“ werden führende Nullen zu Dezimalzeichenfolgen hinzugefügt, wenn der Dezimalwert geringer als 1 ist.

## <a name="configure-number-of-decimal-places"></a>Konfigurieren der Anzahl von Dezimalstellen
Wenn `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` aktiviert ist, können Benutzer das Verbindungs- oder Anweisungsattribut `PDO::SQLSRV_ATTR_DECIMAL_PLACES` verwenden, um die Anzahl von Dezimalstellen bei money- und smallmoney-Daten zu konfigurieren. Für dieses Attribut können ganzzahlige Werte von 0-4 angegeben werden. Bei der Anzeige werden die Werte möglicherweise gerundet. Die zugrunde liegenden money-Daten werden jedoch nicht geändert.

Anweisungsattribute setzen die entsprechenden Verbindungseinstellungen stets außer Kraft. Beachten Sie, dass sich die Option `PDO::SQLSRV_ATTR_DECIMAL_PLACES`**ausschließlich** auf money-Daten auswirkt und `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` auf „true“ festgelegt sein muss. Anderenfalls ist die Formatierung unabhängig von der Einstellung `PDO::SQLSRV_ATTR_DECIMAL_PLACES` deaktiviert.

> [!NOTE]
> Da die Felder „money“ und „smallmoney“ über 4 Dezimalzeichen verfügen, wird `PDO::SQLSRV_ATTR_DECIMAL_PLACES` ignoriert, wenn ein negativer Wert oder ein höherer Wert als 4 festgelegt wird. Es wird nicht empfohlen, formatierte money-Daten als Eingabe für Berechnungen zu verwenden.

### <a name="to-set-the-connection-attributes"></a>Festlegen der Verbindungsattribute

-   So legen Sie Attribute für den Verbindungspunkt fest:

    ```php
    $attrs = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => true,
                   PDO::SQLSRV_ATTR_DECIMAL_PLACES => 2);

    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password, $attrs);
    ```

-   So legen Sie Attribute nach der Verbindung fest:

    ```php
    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password);
    $conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
    $conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);
    ```

## <a name="example---format-money-data"></a>Beispiel: Formatieren von money-Daten
Das folgende Beispiel zeigt, wie money-Daten mithilfe von [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md) abgerufen werden:

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

## <a name="example---override-connection-attributes"></a>Beispiel: Außerkraftsetzung von Verbindungsattributen
Das folgende Beispiel zeigt, wie Sie die Verbindungsattribute außer Kraft setzen:

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
[Formatieren von Dezimalzeichenfolgen und Geldwerten (SQLSRV-Treiber)](../../connect/php/formatting-decimals-sqlsrv-driver.md)

[Abrufen von Daten](../../connect/php/retrieving-data.md)
