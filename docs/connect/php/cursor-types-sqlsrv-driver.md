---
title: Cursortypen (SQLSRV-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8472d839-8124-4a62-a83c-7e771b0d4962
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 763795618eb90fe24db313b801bc01af3cd6737b
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928038"
---
# <a name="cursor-types-sqlsrv-driver"></a>Cursortypen (SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Mit dem SQLSRV-Treiber können Sie ein Resultset mit Zeilen erstellen, auf die Sie in beliebiger Reihenfolge (abhängig vom Cursortyp) zugreifen können.  In diesem Thema werden clientseitige (gepufferte) und serverseitige (nicht gepufferte) Cursor erläutert.  
  
## <a name="cursor-types"></a>Cursortypen  
Wenn Sie ein Resultset mit [sqlsrv_query](../../connect/php/sqlsrv-query.md) oder [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) erstellen, können Sie den Cursortyp angeben. Standardmäßig wird ein Vorwärtscursor verwendet, mit dem Sie beginnend bei der ersten Zeile um jeweils eine Zeile vorrücken können, bis das Ende des Resultsets erreicht ist.  
  
Sie können ein Resultset mit einem scrollbaren Cursor erstellen, mit dem Sie in beliebiger Reihenfolge auf alle Zeilen im Resultset zugreifen können. In den folgenden Tabellen sind die Werte aufgeführt, die an die **Scrollable**-Option in „sqlsrv_query“ oder „sqlsrv_prepare“ übergeben werden können.  
  
|Option|BESCHREIBUNG|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|Hiermit können Sie beginnend bei der ersten Zeile um jeweils eine Zeile vorrücken, bis das Ende des Resultsets erreicht ist.<br /><br />Dies ist der Standardcursortyp.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) gibt einen Fehler für Resultsets zurück, die mit diesem Cursortyp erstellt wurden.<br /><br />**forward** ist die abgekürzte Form von SQLSRV_CURSOR_FORWARD.|  
|SQLSRV_CURSOR_STATIC|Hiermit können Sie in beliebiger Reihenfolge auf Zeilen zugreifen, aber die Änderungen in der Datenbank werden nicht widergespiegelt.<br /><br />**static** ist die abgekürzte Form von SQLSRV_CURSOR_STATIC.|  
|SQLSRV_CURSOR_DYNAMIC|Hiermit können Sie in beliebiger Reihenfolge auf Zeilen zugreifen, und die Änderungen in der Datenbank werden widergespiegelt.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) gibt einen Fehler für Resultsets zurück, die mit diesem Cursortyp erstellt wurden.<br /><br />**dynamic** ist die abgekürzte Form von SQLSRV_CURSOR_DYNAMIC.|  
|SQLSRV_CURSOR_KEYSET|Hiermit können Sie in beliebiger Reihenfolge auf Zeilen zugreifen. Ein Keysetcursor aktualisiert nach dem Löschen einer Zeile aus einer Tabelle jedoch nicht die Zeilenanzahl (eine gelöschte Zeile wird ohne Werte zurückgegeben).<br /><br />**keyset** ist die abgekürzte Form von SQLSRV_CURSOR_KEYSET.|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|Hiermit können Sie in beliebiger Reihenfolge auf Zeilen zugreifen. Es wird eine clientseitige Cursorabfrage erstellt.<br /><br />**buffered** ist die abgekürzte Form von SQLSRV_CURSOR_CLIENT_BUFFERED.|  
  
Wenn eine Abfrage mehrere Resultsets generiert, gilt die **Scrollable**-Option für alle Resultsets.  
  
## <a name="selecting-rows-in-a-result-set"></a>Auswählen von Zeilen in einem Resultset  
Nach dem Erstellen eines Resultsets können Sie [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md), [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) oder [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) verwenden, um eine Zeile anzugeben.  
  
In der folgenden Tabelle werden die Werte beschrieben, die Sie im Parameter *row* angeben können.  
  
|Parameter|BESCHREIBUNG|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|Gibt die nächste Zeile an. Dies ist der Standardwert, wenn Sie den *row*-Parameter nicht für ein scrollbares Resultset festlegen.|  
|SQLSRV_SCROLL_PRIOR|Gibt die Zeile vor der aktuellen Zeile an.|  
|SQLSRV_SCROLL_FIRST|Gibt die erste Zeile im Resultset an.|  
|SQLSRV_SCROLL_LAST|Gibt die letzte Zeile im Resultset an.|  
|SQLSRV_SCROLL_ABSOLUTE|Gibt die mit dem Parameter *offset* angegebene Zeile an.|  
|SQLSRV_SCROLL_RELATIVE|Gibt die mit dem Parameter *offset* ab der aktuellen Zeile angegebene Zeile an.|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>Serverseitige Cursor und der SQLSRV-Treiber  
Das folgende Beispiel veranschaulicht die Auswirkungen der verschiedenen Cursor. In Zeile 33 des Beispiels sehen Sie die erste von drei Abfrageanweisungen, die verschiedene Cursor angeben.  Zwei der Abfrageanweisungen sind auskommentiert. Verwenden Sie bei jeder Programmausführung einen anderen Cursor, und sehen Sie sich die Auswirkung auf die Datenbankaktualisierung in Zeile 47 an.  
  
```  
<?php  
$server = "server_name";  
$conn = sqlsrv_connect( $server, array( 'Database' => 'test' ));  
if ( $conn === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "DROP TABLE dbo.ScrollTest" );  
if ( $stmt !== false ) {   
   sqlsrv_free_stmt( $stmt );   
}  
  
$stmt = sqlsrv_query( $conn, "CREATE TABLE ScrollTest (id int, value char(10))" );  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 1, "Row 1" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 2, "Row 2" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 3, "Row 3" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'keyset' ));  
// $stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'dynamic' ));  
// $stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'static' ));  
  
$rows = sqlsrv_has_rows( $stmt );  
if ( $rows != true ) {  
   die( "Should have rows" );  
}  
  
$result = sqlsrv_fetch( $stmt, SQLSRV_SCROLL_LAST );  
$field1 = sqlsrv_get_field( $stmt, 0 );  
$field2 = sqlsrv_get_field( $stmt, 1 );  
echo "\n$field1 $field2\n";  
  
$stmt2 = sqlsrv_query( $conn, "delete from ScrollTest where id = 3" );  
// or  
// $stmt2 = sqlsrv_query( $conn, "UPDATE ScrollTest SET id = 4 WHERE id = 3" );  
if ( $stmt2 !== false ) {   
   sqlsrv_free_stmt( $stmt2 );   
}  
  
$result = sqlsrv_fetch( $stmt, SQLSRV_SCROLL_LAST );  
$field1 = sqlsrv_get_field( $stmt, 0 );  
$field2 = sqlsrv_get_field( $stmt, 1 );  
echo "\n$field1 $field2\n";  
  
sqlsrv_free_stmt( $stmt );  
sqlsrv_close( $conn );  
?>  
```  
  
## <a name="client-side-cursors-and-the-sqlsrv-driver"></a>Clientseitige Cursor und der SQLSRV-Treiber  
Das Feature „clientseitige Cursor“ wurde in Version 3.0 der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] hinzugefügt. Mit ihnen können Sie ein komplettes Resultset im Arbeitsspeicher zwischenspeichern. Bei Verwendung eines clientseitigen Cursors ist die Zeilenanzahl nach Ausführung der Abfrage verfügbar.  
  
Clientseitige Cursor eignen sich für kleine bis mittelgroße Resultsets. Verwenden Sie bei großen Resultsets serverseitige Cursor.  
  
Eine Abfrage gibt FALSE zurück, wenn der Puffer nicht groß genug für das komplette Resultset ist. Sie können die Puffergröße bis zur Grenze des PHP-Speichers erhöhen.  
  
Bei Verwendung des SQLSRV-Treibers können Sie mit der ClientBufferMaxKBSize-Einstellung für [sqlsrv_configure](../../connect/php/sqlsrv-configure.md) die Größe des Puffers für das Resultset konfigurieren. [sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) gibt den Wert von ClientBufferMaxKBSize zurück. Sie können die maximale Puffergröße auch mit sqlsrv.ClientBufferMaxKBSize (z. B. sqlsrv.ClientBufferMaxKBSize = 1024) in der Datei „php.ini“ festlegen.  
  
Dieses Beispiel zeigt Folgendes:  
  
-   Die Zeilenanzahl ist bei einem clientseitigen Cursor immer verfügbar.  
  
-   Verwendung von clientseitigen Cursorn und Batchanweisungen.  
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "select * from HumanResources.Department";  
  
// Execute the query with client-side cursor.  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
if (! $stmt) {  
   echo "Error in statement execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// row count is always available with a client-side cursor  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count = $row_count\n";  
  
// Move to a specific row in the result set.  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
  
// Client-side cursor and batch statements  
$tsql = "select top 2 * from HumanResources.Employee;Select top 3 * from HumanResources.EmployeeAddress";  
  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
if (! $stmt) {  
   echo "Error in statement execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for first result set = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
  
sqlsrv_next_result($stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for second result set = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_LAST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
?>  
```  
  
Das folgende Beispiel zeigt einen clientseitigen Cursor mit Verwendung von [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) und einer anderen Clientpuffergröße.
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "select * from HumanResources.Employee";  
$stmt = sqlsrv_prepare( $conn, $tsql, array(), array("Scrollable" => SQLSRV_CURSOR_CLIENT_BUFFERED, "ClientBufferMaxKBSize" => 51200));
  
if (! $stmt ) {  
   echo "Statement could not be prepared.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_execute( $stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
if ($row_count)  
   echo "\nRow count = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
if ($row ) {  
   $EmployeeID = sqlsrv_get_field( $stmt, 0);  
   echo "Employee ID = $EmployeeID \n";  
}  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Festlegen eines Cursortyps und Zeilenauswahl](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)  
  
