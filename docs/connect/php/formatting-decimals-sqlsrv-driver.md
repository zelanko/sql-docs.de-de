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
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265143"
---
# <a name="formatting-decimal-strings-and-money-values-sqlsrv-driver"></a>Formatieren von Dezimalzeichenfolgen und Geldwerten (SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Um die Genauigkeit beizubehalten, werden [dezimale oder numerische Typen](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) immer als Zeichen folgen mit exakten Spezifikationen und Skalen abgerufen. Wenn ein Wert kleiner als 1 ist, fehlt die führende Null. Das gleiche gilt für die Felder "Money" und "smallmoney", da es sich um Dezimal Felder mit einer festgelegten Skala von 4 handelt.

## <a name="add-leading-zeroes-if-missing"></a>Vorangehende Nullen hinzufügen, wenn Sie fehlen
Ab Version 5.6.0 wird die-Option `FormatDecimals` zu den sqlsrv-Verbindungs-und-Anweisungs Ebenen hinzugefügt, die es dem Benutzer ermöglichen, dezimale Zeichen folgen zu formatieren. Diese Option erwartet einen booleschen Wert (true oder false) und wirkt sich nur auf die Formatierung von Dezimal-oder numerischen Werten in den abgerufenen Ergebnissen aus. Mit anderen Worten: die `FormatDecimals` Option hat keine Auswirkung auf andere Vorgänge wie einfügen oder aktualisieren.

Standardmäßig ist `FormatDecimals` **false**. Wenn diese Einstellung auf "true" festgelegt ist, werden die führenden Nullen zu dezimalen Zeichen folgen für einen beliebigen Dezimalwert kleiner als 1 hinzugefügt.

## <a name="configure-number-of-decimal-places"></a>Anzahl von Dezimalstellen konfigurieren
Wenn `FormatDecimals` aktiviert ist, können Benutzer die `DecimalPlaces`Anzahl von Dezimalstellen beim Anzeigen von Money-und smallmoney-Daten mit einer anderen Option () konfigurieren. Sie akzeptiert ganzzahlige Werte im Bereich von [0, 4], und die Rundung kann auftreten, wenn Sie angezeigt wird. Die zugrunde liegenden Money-Daten bleiben jedoch unverändert.

Beide Optionen können auf Verbindungs-oder Anweisungs Ebene festgelegt werden, und die-Anweisungs Einstellung überschreibt immer die entsprechende Verbindungs Einstellung. Beachten Sie, `DecimalPlaces` dass die-Option **nur** die Money `FormatDecimals` -Daten betrifft und auf true `DecimalPlaces` festgelegt werden muss, damit wirksam wird. Andernfalls wird die Formatierung unabhängig von der `DecimalPlaces` -Einstellung deaktiviert.

> [!NOTE]
> Da die Felder Money oder smallmoney den Wert 4 haben `DecimalPlaces` , wird das Festlegen des Werts auf eine negative Zahl oder auf einen Wert größer als 4 ignoriert. Es wird nicht empfohlen, als Eingaben in eine beliebige Berechnung formatierte Money-Daten zu verwenden.

## <a name="example---a-simple-fetch"></a>Beispiel: einfaches Abrufen
Im folgenden Beispiel wird gezeigt, wie die neuen Optionen in einem einfachen Abruf Vorgang verwendet werden.

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

## <a name="example---format-the-output-parameter"></a>Beispiel: Formatieren des Output-Parameters
Wenn ein dezimales oder numerisches Feld als [Output-Parameter](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)zurückgegeben wird, wird der zurückgegebene Wert als reguläre varchar-Zeichenfolge betrachtet. Wenn jedoch entweder SQLSRV_SQLTYPE_DECIMAL oder SQLSRV_SQLTYPE_NUMERIC angegeben wird, können Sie auf true `FormatDecimals` festlegen, um sicherzustellen, dass für den numerischen Zeichen folgen Wert keine fehlende führende Null vorhanden ist. Weitere Informationen finden Sie unter [Gewusst wie: Abrufen von Eingabe-/Ausgabeparametern mit dem SQLSRV-Treiber](../..//connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).

Im folgenden Beispiel wird gezeigt, wie der Output-Parameter einer gespeicherten Prozedur formatiert wird, die einen Dezimalwert (8, 4) zurückgibt.

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
