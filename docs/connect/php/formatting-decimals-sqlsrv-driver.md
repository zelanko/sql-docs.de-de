---
title: Formatieren von Dezimalzeichenfolgen und Geldwerten (SQLSRV-Treiber) | Microsoft-Dokumentation
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
ms.openlocfilehash: 4a5ac641a98077c09bb38a5fc8fbd3fb1a4bf73d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68265143"
---
# <a name="formatting-decimal-strings-and-money-values-sqlsrv-driver"></a>Formatieren von Dezimalzeichenfolgen und Geldwerten (SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Für maximale Genauigkeit werden [Dezimal- oder numerische Typen](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) immer als Zeichenfolgen mit der exakten Anzahl von Zeichen und Dezimalzeichen abgerufen. Wenn ein Wert geringer als 1 ist, fehlt die führende Null. Gleiches gilt für die Felder „money“ und „smallmoney“, da es sich um Dezimalfelder mit einer festen Anzahl von Dezimalzeichen (4) handelt.

## <a name="add-leading-zeroes-if-missing"></a>Hinzufügen von fehlenden führenden Nullen
Ab Version 5.6.0 können Benutzer die Option `FormatDecimals` auf sqlsrv-Verbindungs- und -Anweisungsebene verwenden, um Dezimalzeichenfolgen zu formatieren. Diese Option wird mit einem booleschen Wert (true oder false) verwendet und wirkt sich ausschließlich auf die Formatierung der Dezimal- oder numerischen Werte in den abgerufenen Ergebnissen aus. Mit anderen Worten, die Option `FormatDecimals` hat keine Auswirkungen auf andere Vorgänge wie beispielsweise Einfüge- oder Aktualisierungsvorgänge.

Standardmäßig ist `FormatDecimals`**false**. Bei Festlegung auf „true“ werden führende Nullen zu Dezimalzeichenfolgen hinzugefügt, wenn der Dezimalwert geringer als 1 ist.

## <a name="configure-number-of-decimal-places"></a>Konfigurieren der Anzahl von Dezimalstellen
Wenn `FormatDecimals` aktiviert ist, können Benutzer die Option `DecimalPlaces` verwenden, um die Anzahl von Dezimalstellen bei money- und smallmoney-Daten zu konfigurieren. Für dieses Attribut können ganzzahlige Werte von 0-4 angegeben werden. Bei der Anzeige werden die Werte möglicherweise gerundet. Die zugrunde liegenden money-Daten werden jedoch nicht geändert.

Beide Optionen können auf Verbindungs- oder Anweisungsebene festgelegt werden. Die Anweisungseinstellung setzt stets die entsprechende Verbindungseinstellung außer Kraft. Beachten Sie, dass sich die Option `DecimalPlaces` **ausschließlich** auf money-Daten auswirkt und `FormatDecimals` auf „true“ festgelegt sein muss, damit `DecimalPlaces` wirksam wird. Anderenfalls ist die Formatierung unabhängig von der Einstellung `DecimalPlaces` deaktiviert.

> [!NOTE]
> Da die Felder „money“ und „smallmoney“ über 4 Dezimalzeichen verfügen, wird `DecimalPlaces` ignoriert, wenn ein negativer Wert oder ein höherer Wert als 4 festgelegt wird. Es wird nicht empfohlen, formatierte money-Daten als Eingabe für Berechnungen zu verwenden.

## <a name="example---a-simple-fetch"></a>Beispiel: einfaches Abrufen
Das folgende Beispiel zeigt, wie die neuen Optionen für einen einfachen Datenabruf verwendet werden.

```php
<?php
$username = 'myusername';
$password = 'mypasword';
$tableName = 'mytable';

$connectionInfo = array("UID" => $username, "PWD" => $password, "Database" => "myDB", "FormatDecimals" => true);  
$server = "myServer";  // IP address also works
$conn = sqlsrv_connect( $server, $connectionInfo);  

$numDigits = 2;
$query = "SELECT money1 FROM $tableName";
$options = array("DecimalPlaces" => $numDigits);
$stmt = sqlsrv_prepare($conn, $query, array(), $options);
sqlsrv_execute($stmt);

if (sqlsrv_fetch($stmt)) {
    $field = sqlsrv_get_field($stmt, 0);  
    echo $field;   // expect a numeric value string with 2 decimal places
}

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);
?>
```

## <a name="example---format-the-output-parameter"></a>Beispiel: Formatieren des Ausgabeparameters
Wenn ein Dezimal- oder numerisches Feld als [Ausgabeparameter](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md) zurückgegeben wird, wird der zurückgegebene Wert als reguläre varchar-Zeichenfolge betrachtet. Bei Angabe von SQLSRV_SQLTYPE_DECIMAL oder SQLSRV_SQLTYPE_NUMERIC können Benutzer jedoch `FormatDecimals` auf „true“ festlegen, um sicherzustellen, dass beim numerischen Zeichenfolgenwert keine führenden Nullen fehlen. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Ausgabeparametern mit dem SQLSRV-Treiber](../..//connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).

Das folgende Beispiel zeigt, wie der Ausgabeparameter einer gespeicherten Prozedur formatiert wird, der einen Dezimalwert (8,4) zurückgibt.

```php
$outString = '';
$outSql = '{CALL myStoredProc(?)}';
$stmt = sqlsrv_prepare($conn, 
                       $outSql, 
                       array(array(&$outString, SQLSRV_PARAM_OUT, null, SQLSRV_SQLTYPE_DECIMAL(8, 4))),
                       array('FormatDecimals' => true));

if (sqlsrv_execute($stmt)) {
    echo $outString;  // expect a numeric value string with no missing leading zero
}
```

## <a name="see-also"></a>Weitere Informationen
[Formatieren von Dezimalzeichenfolgen und Geldwerten (PDO_SQLSRV-Treiber)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)

[Abrufen von Daten](../../connect/php/retrieving-data.md)
