---
title: GetAttribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c81833ea-8b8a-459d-8f24-920098da994d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7a7b634b10be90b164f67eb2837a053eef3db7e8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66762141"
---
# <a name="pdogetattribute"></a>PDO::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft den Wert eines vordefinierten PDO- oder Treiberattributs ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
mixed PDO::getAttribute ( $attribute )  
```  
  
#### <a name="parameters"></a>Parameter  
*$attribute*: Eines der unterstützten Attribute. Eine Liste der unterstützten Attribute finden Sie bei den Anmerkungen.  
  
## <a name="return-value"></a>Rückgabewert  
Im Erfolgsfall wird der Wert einer Verbindungsoption, eines vordefinierten PDO-Attributs, oder eines benutzerdefinierten Treiberattributs zurückgegeben. Gibt bei einem Fehler NULL zurück.  
  
## <a name="remarks"></a>Remarks  
Die nachfolgende Tabelle enthält die Liste mit den unterstützten Attributen:  
  
|attribute|Verarbeitet von|Unterstützte Werte|und Beschreibung|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR_CASE|PDO|PDO::CASE_LOWER<br /><br />PDO::CASE_NATURAL<br /><br />PDO::CASE_UPPER|Dies gibt an, ob die Spaltennamen entweder groß oder klein geschrieben sein sollen. PDO::CASE_LOWER erzwingt die Schreibung der Spaltennamen in Kleinbuchstaben, PDO::CASE_NATURAL belässt die Spaltennamen so wie sie aus der Datenbank zurückgegeben wurden und PDO::CASE_UPPER erzwingt die Schreibung der Spaltennamen in Großbuchstaben.<br /><br />Die Standardeinstellung ist PDO::CASE_NATURAL.<br /><br />Dieses Attribut kann auch mit PDO::setAttribute eingerichtet werden.|  
|PDO::ATTR_CLIENT_VERSION|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Ein Array von Zeichenfolgen|Beschreibt die Version des Treibers und der verbundenen Bibliotheken Gibt ein Array mit den folgenden Elementen zurück: ODBC-Version (*Hauptversion*.*Nebenversion*), Name und Version der nativen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Client-DLL, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]-Version (*Hauptversion*.*Nebenversion*.*Buildnummer*.*Revision*)|  
|PDO::ATTR_DRIVER_NAME|PDO|Zeichenfolge|Gibt immer „sqlsrv“ zurück.|  
|PDO::ATTR_DRIVER_VERSION|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Zeichenfolge|Gibt die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]-Version (*Hauptversion*.*Nebenversion*.*Buildnummer*.*Revision*)|  
|PDO::ATTR_ERRMODE|PDO|PDO::ERRMODE_SILENT<br /><br />PDO::ERRMODE_WARNING<br /><br />PDO::ERRMODE_EXCEPTION|Gibt an, wie Fehler vom Treiber behandelt werden sollen.<br /><br />PDO::ERRMODE_SILENT (der Standard) legt die Fehlercodes und -informationen fest.<br /><br />PDO::ERRMODE_WARNING veranlasst E_WARNING.<br /><br />PDO::ERRMODE_EXCEPTION löst eine Ausnahme aus.<br /><br />Dieses Attribut kann auch mit PDO::setAttribute eingerichtet werden.|  
|PDO::ATTR_ORACLE_NULLS|PDO|Siehe PDO-Dokumentation.|Siehe PDO-Dokumentation.|  
|PDO::ATTR_SERVER_INFO|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Array aus drei Elementen|Gibt die aktuelle Datenbank, SQL Server-Version und SQL  Server-Instanz zurück.|  
|PDO::ATTR_SERVER_VERSION|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Zeichenfolge|Gibt die SQL Server-Version (*Hauptversion*.*Nebenversion*.*Buildnummer*) an.|  
|PDO::ATTR_STRINGIFY_FETCHES|PDO|Siehe PDO-Dokumentation.|Siehe PDO-Dokumentation.|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|1 bis zur Grenze des PHP-Speichers.|Konfiguriert die Größe des Puffers, der das Resultset für einen clientseitigen Cursor enthält.<br /><br />Die Standardeinstellung ist 10.240 KB (10 MB).<br /><br />Weitere Informationen zu clientseitigen Cursorn finden Sie unter [Cursortypen &#40;SQLSRV-Treiber&#41;](../../connect/php/cursor-types-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true<br /><br />false|Legt fest, ob eine direkte oder eine vorbereitete Anweisung ausgeführt wird. Weitere Informationen finden Sie unter [Direkte Anweisungsausführung und vorbereitete Anweisungsausführung im PDO_SQLSRV-Treiber](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PDO::SQLSRV_ENCODING_UTF8<br /><br />PDO::SQLSRV_ENCODING_SYSTEM|Legt die Zeichensatzcodierung fest, die vom Treiber verwendet wird, um mit dem Server zu kommunizieren<br /><br />Der Standard ist PDO::SQLSRV_ENCODING_UTF8.|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true oder false|Verarbeitet numerische Abrufvorgänge aus Spalten mit numerischen SQL-Typen („bit“, „integer“, „smallint“, „tinyint“, „float“ oder „real“).<br /><br />Wenn das Flag für die Verbindungsoption ATTR_STRINGIFY_FETCHES auf „On“ festgelegt ist, ist der Rückgabewert selbst dann eine Zeichenfolge, wenn SQLSRV_ATTR_FETCHES_NUMERIC_TYPE auf „On“ festgelegt ist.<br /><br />Wenn der zurückgegebene PDO-Typ in einer bind-Spalte PDO_PARAM_INT lautet, ist der Rückgabewert aus einer integer-Spalte vom Typ „int“, selbst wenn SQLSRV_ATTR_FETCHES_NUMERIC_TYPE auf „Off“ festgelegt ist.|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|integer|Legt das Abfragetimeout in Sekunden fest.<br /><br />Der Standard ist 0, d. h. dass der Treiber unendlich lange auf Ergebnisse wartet.<br /><br />Negative Zahlen sind nicht zulässig.|  

  
PDO verarbeitet einige der vordefinierten Attribute selbst, während für die Handhabung anderer der Treiber erforderlich ist. Alle benutzerdefinierten Attribute und Verbindungsoptionen werden vom Treiber gehandhabt. Ein nicht unterstütztes Attribut oder eine nicht unterstützte Verbindungsversion gibt NULL zurück.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Dieses Beispiel zeigt den Wert des Attributs PDO::ATTR_ERRMODE, bevor und nachdem der Wert geändert wurde.  
  
```  
<?php  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
  
$attributes1 = array( "ERRMODE" );  
foreach ( $attributes1 as $val ) {  
     echo "PDO::ATTR_$val: ";  
     var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
}  
  
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
  
$attributes1 = array( "ERRMODE" );  
foreach ( $attributes1 as $val ) {  
     echo "PDO::ATTR_$val: ";  
     var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
}  
  
// An example using PDO::ATTR_CLIENT_VERSION  
print_r($conn->getAttribute( PDO::ATTR_CLIENT_VERSION ));  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
