---
title: PDOStatement::setAttribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e88504bd68c9f61d0178423b8e57ecf6679e4e8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918389"
---
# <a name="pdostatementsetattribute"></a>PDOStatement::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Legt einen Attributwert fest. Entweder ein vordefiniertes PDO-Attribut oder ein benutzerdefiniertes Treiberattribut.  
  
## <a name="syntax"></a>Syntax  
  
```  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### <a name="parameters"></a>Parameter  
$*attribute:* Eine ganze Zahl, eine der Konstanten PDO::ATTR_* oder PDO::SQLSRV_ATTR_\*. Eine Liste der verfügbaren Attribute finden Sie im Abschnitt „Anmerkungen“.  
  
$*value:* Der (gemischte) Wert, der für den angegebenen $*attribute*-Parameter festgelegt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
„true“ bei Erfolg, andernfalls „false“.  
  
## <a name="remarks"></a>Bemerkungen  
Die folgende Tabelle enthält die Liste mit den verfügbaren Attributen:  
  
|attribute|Werte|Beschreibung|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|1 bis zur Grenze des PHP-Speichers.|Konfiguriert die Größe des Puffers, der das Resultset für einen clientseitigen Cursor enthält.<br /><br />Die Standardeinstellung ist 10.240 KB (10 MB).<br /><br />Weitere Informationen zu clientseitigen Cursorn finden Sie unter [Cursortypen &#40;PDO_SQLSRV-Treiber&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DATA_CLASSIFICATION|true oder false|Gibt an, ob die Metadaten für die Datenklassifizierung beim Aufruf von [PDOStatement::getColumnMeta](../../connect/php/pdostatement-getcolumnmeta.md) abgerufen werden sollen. Die Standardeinstellung ist „false“.|
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|Ganze Zahl zwischen 0 und (einschließlich) 4|Gibt die Anzahl der Dezimalstellen beim Formatieren abgerufener Geldwerte (vom Typ „money“) an.<br /><br />Negative ganze Zahlen oder Werte größer als 4 werden ignoriert.<br /><br />Diese Option funktioniert nur, wenn PDO::SQLSRV_ATTR_FORMAT_DECIMALS auf TRUE festgelegt ist.<br /><br />Diese Option kann auch auf Verbindungsebene festgelegt werden. In diesem Fall überschreibt diese Option die Option auf Verbindungsebene.<br /><br />Weitere Informationen finden Sie unter [Formatieren von Dezimalzeichenfolgen und Geldwerten (PDO_SQLSRV-Treiber)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).|
|PDO::SQLSRV_ATTR_ENCODING|Integer<br /><br />PDO::SQLSRV_ENCODING_UTF8 (Standard)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Legt die Zeichensatzcodierung fest, die vom Treiber verwendet wird, um mit dem Server zu kommunizieren.|  
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|true oder false|Gibt an, ob Datums- und Uhrzeittypen als [PHP-DateTime-Objekte](http://php.net/manual/en/class.datetime.php) abgerufen werden sollen. Bei FALSE erfolgt die Standardrückgabe als Zeichenfolgen.<br /><br />Diese Option kann auch auf Verbindungsebene festgelegt werden. In diesem Fall überschreibt diese Option die Option auf Verbindungsebene.<br /><br />Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Datums- und Uhrzeittypen als PHP-datetime-Objekte mit dem PDO_SQLSRV-Treiber](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|true oder false|Verarbeitet numerische Abrufvorgänge aus Spalten mit numerischen SQL-Typen („bit“, „integer“, „smallint“, „tinyint“, „float“ oder „real“).<br /><br />Wenn das Flag für die Verbindungsoption ATTR_STRINGIFY_FETCHES auf „On“ festgelegt ist, ist der Rückgabewert selbst dann eine Zeichenfolge, wenn SQLSRV_ATTR_FETCHES_NUMERIC_TYPE auf „On“ festgelegt ist.<br /><br />Wenn der zurückgegebene PDO-Typ in einer bind-Spalte PDO_PARAM_INT lautet, ist der Rückgabewert aus einer integer-Spalte vom Typ „int“, selbst wenn SQLSRV_ATTR_FETCHES_NUMERIC_TYPE auf „Off“ festgelegt ist.|  
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|true oder false|Gibt an, ob Dezimalzeichenfolgen gegebenenfalls führende Nullen hinzugefügt werden sollen. Bei Festlegung erlaubt diese Option der Option PDO::SQLSRV_ATTR_DECIMAL_PLACES das Formatieren von Datentypen vom Typ „money“. Bei FALSE wird als Standardverhalten die Rückgabe absoluter Genauigkeit und das Auslassen führender Nullen für Werte kleiner 1 verwendet.<br /><br />Diese Option kann auch auf Verbindungsebene festgelegt werden. In diesem Fall überschreibt diese Option die Option auf Verbindungsebene.<br /><br />Weitere Informationen finden Sie unter [Formatieren von Dezimalzeichenfolgen und Geldwerten (PDO_SQLSRV-Treiber)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).| 
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Integer|Legt das Abfragetimeout in Sekunden fest.<br /><br />Standardmäßig wartet der Treiber unbegrenzt auf Ergebnisse. Negative Zahlen sind nicht zulässig.<br /><br />„0“ bedeutet „kein Timeout“.|  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets'=>false )  );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
echo $stmt->getAttribute( constant( "PDO::ATTR_CURSOR" ) );  
  
echo "\n";  
  
$stmt->setAttribute(PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 2);  
echo $stmt->getAttribute( constant( "PDO::SQLSRV_ATTR_QUERY_TIMEOUT" ) );  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
