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
manager: mbarwin
ms.openlocfilehash: 76b6d27acedcfe2ec462a764559237a1a2218f78
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62669602"
---
# <a name="formatting-decimal-strings-and-money-values-sqlsrv-driver"></a>Formatieren von Dezimalzeichenfolgen und Geldwerten (SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Beibehalten der Genauigkeit der [Datentypen decimal und numeric](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) immer als Zeichenfolgen mit genauen genauigkeiten und Skalierungen abgerufen werden. Wenn Sie einen beliebigen Wert kleiner als 1 ist, ist die führende 0 (null) nicht vorhanden. Es ist identisch mit Money- und Smallmoney-Feldern wie Dezimalfelder mit festen gleich 4 Dezimalstellen.

## <a name="add-leading-zeroes-if-missing"></a>Hinzufügen von führenden Nullen bei fehlen
Ab Version 5.6.0, die Option `FormatDecimals` hinzugefügt Sqlsrv Verbindungs- und Ebenen, die dem Benutzer ermöglicht, Dezimalzeichenfolgen zu formatieren. Diese Option erwartet, dass einen booleschen Wert (true oder false), und wirkt sich nur auf die Formatierung von decimal oder numeric-Werten in der abgerufenen Ergebnissen. Das heißt, die `FormatDecimals` Option hat keine Auswirkungen auf andere Vorgänge wie das Einfügen oder aktualisieren.

Standardmäßig ist `FormatDecimals` **false**. Wenn auf True festgelegt, die führenden Nullen in decimal Zeichenfolgen für jeden decimal-Wert kleiner als 1 hinzugefügt werden.

## <a name="configure-number-of-decimal-places"></a>Konfigurieren Sie die Anzahl der Dezimalstellen
Mit `FormatDecimals` aktiviert ist, eine weitere Möglichkeit ist `DecimalPlaces`, ermöglicht es Benutzern, die Anzahl der Dezimalstellen zu konfigurieren, Anzeigen von Money und Smallmoney-Daten. Er akzeptiert ganzzahlige Werte im Bereich [0, 4], und runden auftreten, wenn angezeigt. Die zugrunde liegenden Money-Daten bleiben jedoch gleich.

Beide Optionen können auf Verbindung oder Anweisungsebene festgelegt werden, und überschreibt die Anweisung, die Einstellung immer die entsprechende verbindungseinstellung. Beachten Sie, dass die `DecimalPlaces` Option **nur** wirkt sich auf Money-Daten und `FormatDecimals` muss festgelegt werden, um für "true" `DecimalPlaces` wirksam werden. Andernfalls formatieren ist deaktiviert unabhängig von `DecimalPlaces` festlegen.

> [!NOTE]
> Da Felder Money "oder" Smallmoney Skalierung 4 enthalten, festlegen `DecimalPlaces` Wert auf eine negative Zahl oder einen beliebigen Wert größer als 4 werden ignoriert. Es wird nicht empfohlen, alle formatierte Money-Daten als Eingabe für eine beliebige Berechnung verwenden.

## <a name="example---a-simple-fetch"></a>Beispiel: einen einfachen Abruf
Das folgende Beispiel zeigt, wie die neuen Optionen in einen einfachen Abruf verwendet wird.

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

## <a name="example---format-the-output-parameter"></a>Beispiel: Format der Output-parameter
Wenn ein decimal oder numerische-Feld, als zurückgegeben wird die [Ausgabeparameter](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md), der zurückgegebene Wert wird als reguläre Varchar Zeichenfolge betrachtet werden. Wenn entweder SQLSRV_SQLTYPE_DECIMAL oder SQLSRV_SQLTYPE_NUMERIC angegeben ist, Sie können jedoch festlegen `FormatDecimals` auf true festlegen, um sicherzustellen, dass es keine führende 0 (null), für den numerischen Zeichenfolgenwert fehlt. Weitere Informationen finden Sie unter [Gewusst wie: Abrufen von Eingabe-/Ausgabeparametern mit dem SQLSRV-Treiber](../..//connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).

Das folgende Beispiel zeigt, wie den Output-Parameter einer gespeicherten Prozedur formatiert werden, die einen decimal(8,4) Wert zurückgibt.

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
