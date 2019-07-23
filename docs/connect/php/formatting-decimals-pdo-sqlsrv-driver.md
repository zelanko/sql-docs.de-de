---
title: Formatieren von Dezimalzeichenfolgen und Geldwerten (PDO_SQLSRV-Treiber) | Microsoft-Dokumentation
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
manager: v-mabarw
ms.openlocfilehash: 76c314159faf15e63bf77b17a8a45abf217b205c
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265153"
---
# <a name="formatting-decimal-strings-and-money-values-pdosqlsrv-driver"></a>Formatieren von Dezimalzeichenfolgen und Geldwerten (PDO_SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Um die Genauigkeit beizubehalten, werden [dezimale oder numerische Typen](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) immer als Zeichen folgen mit exakten Spezifikationen und Skalen abgerufen. Wenn ein Wert kleiner als 1 ist, fehlt die führende Null. Das gleiche gilt für die Felder "Money" und "smallmoney", da es sich um Dezimal Felder mit einer festgelegten Skala von 4 handelt.

## <a name="add-leading-zeroes-if-missing"></a>Vorangehende Nullen hinzufügen, wenn Sie fehlen
Ab Version 5.6.0 ermöglicht das Verbindungs-oder Anweisungs `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` Attribut dem Benutzer das Formatieren von Dezimalzeichen folgen. Dieses Attribut erwartet einen booleschen Wert (true oder false) und wirkt sich nur auf die Formatierung der Dezimal-oder numerischen Werte in den abgerufenen Ergebnissen aus. Mit anderen Worten: dieses Attribut hat keine Auswirkung auf andere Vorgänge wie einfügen oder aktualisieren.

Standardmäßig ist `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` **false**. Wenn diese Einstellung auf "true" festgelegt ist, werden die führenden Nullen zu dezimalen Zeichen folgen für einen beliebigen Dezimalwert kleiner als 1 hinzugefügt.

## <a name="configure-number-of-decimal-places"></a>Anzahl von Dezimalstellen konfigurieren
Wenn aktiviert ist, ermöglicht das andere Verbindungs-oder `PDO::SQLSRV_ATTR_DECIMAL_PLACES`Anweisungs Attribut Benutzern das Konfigurieren der Anzahl von Dezimalstellen, wenn Money-und smallmoney-Daten angezeigt werden. `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` Sie akzeptiert ganzzahlige Werte im Bereich von [0, 4], und die Rundung kann auftreten, wenn Sie angezeigt wird. Die zugrunde liegenden Money-Daten bleiben jedoch unverändert.

Die Anweisungs Attribute überschreiben immer die entsprechenden Verbindungseinstellungen. Beachten Sie, `PDO::SQLSRV_ATTR_DECIMAL_PLACES` dass die Option **nur** die Money- `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` Daten betrifft und auf true festgelegt werden muss. Andernfalls wird die Formatierung unabhängig von der `PDO::SQLSRV_ATTR_DECIMAL_PLACES` -Einstellung deaktiviert.

> [!NOTE]
> Da die Felder Money oder smallmoney den Wert 4 haben `PDO::SQLSRV_ATTR_DECIMAL_PLACES` , wird das Festlegen von auf eine negative Zahl oder auf einen Wert größer als 4 ignoriert. Es wird nicht empfohlen, als Eingaben in eine beliebige Berechnung formatierte Money-Daten zu verwenden.

### <a name="to-set-the-connection-attributes"></a>So legen Sie die Verbindungs Attribute fest

-   Legen Sie die Attribute zum Verbindungspunkt fest:

    ```php
    $attrs = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => true,
                   PDO::SQLSRV_ATTR_DECIMAL_PLACES => 2);

    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password, $attrs);
    ```

-   Attribute nach der Verbindung festlegen:

    ```php
    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password);
    $conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
    $conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);
    ```

## <a name="example---format-money-data"></a>Beispiel: Formatieren von Money-Daten
Das folgende Beispiel zeigt, wie Sie mit [PDOStatement:: bindColumn](../../connect/php/pdostatement-bindcolumn.md)Money-Daten abrufen:

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

## <a name="example---override-connection-attributes"></a>Beispiel: Überschreiben von Verbindungs Attributen
Im folgenden Beispiel wird gezeigt, wie die Verbindungs Attribute überschrieben werden:

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
