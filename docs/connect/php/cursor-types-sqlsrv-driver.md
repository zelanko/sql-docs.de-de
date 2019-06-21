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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6452fc506814cdfdeee4f61085ec9a1ee0cededa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801493"
---
# <a name="cursor-types-sqlsrv-driver"></a>Cursortypen (SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Mit dem SQLSRV-Treiber können Sie ein Resultset mit Zeilen erstellen, auf die Sie in beliebiger Reihenfolge (abhängig vom Cursortyp) zugreifen können.  In diesem Thema wird erläutert, der clientseitigen (gepufferten) und (wird ungepufferten) von serverseitigen Cursorn.  
  
## <a name="cursor-types"></a>Cursortypen  
Wenn Sie ein Resultset mit erstellen [Sqlsrv_query](../../connect/php/sqlsrv-query.md) oder mit [Sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md), Sie können den Typ des Cursors angeben. Standardmäßig wird ein Vorwärtscursor verwendet das können Sie eine Zeile verschieben, zu einem Zeitpunkt, ab der ersten Zeile des Resultsets, bis das Ende des Resultsets erreicht.  
  
Sie können ein Resultset mit einem bildlauffähigen Cursor, der Sie auf eine beliebige Zeile im Resultset, in beliebiger Reihenfolge zugreifen kann, erstellen. Die folgende Tabelle enthält die Werte, die übergeben werden können die **Scrollable** Option im Sqlsrv_query oder Sqlsrv_prepare.  
  
|Option|und Beschreibung|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|Können Sie eine Zeile verschieben, zu einem Zeitpunkt, ab der ersten Zeile des Resultsets, bis das Ende des Resultsets erreicht.<br /><br />Dies ist der Standardcursortyp.<br /><br />[zu Sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) gibt die Fehlermeldung für Resultsets, die für diesen Cursortyp erstellt.<br /><br />**Vorwärts** ist die verkürzte Form der SQLSRV_CURSOR_FORWARD.|  
|SQLSRV_CURSOR_STATIC|Können Sie auf Zeilen in beliebiger Reihenfolge zuzugreifen, aber nicht wider, Änderungen in der Datenbank.<br /><br />**statische** ist die verkürzte Form der SQLSRV_CURSOR_STATIC.|  
|SQLSRV_CURSOR_DYNAMIC|Können Sie den Zugriff auf Zeilen in beliebiger Reihenfolge und Änderungen in der Datenbank wiedergibt.<br /><br />[zu Sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) gibt die Fehlermeldung für Resultsets, die für diesen Cursortyp erstellt.<br /><br />**dynamische** ist die verkürzte Form der SQLSRV_CURSOR_DYNAMIC.|  
|SQLSRV_CURSOR_KEYSET|Können Sie die Zeilen in beliebiger Reihenfolge zugreifen. Ein Keysetcursor aktualisiert nach dem Löschen einer Zeile aus einer Tabelle jedoch nicht die Zeilenanzahl (eine gelöschte Zeile wird ohne Werte zurückgegeben).<br /><br />**Keyset** ist die verkürzte Form der SQLSRV_CURSOR_KEYSET.|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|Können Sie die Zeilen in beliebiger Reihenfolge zugreifen. Erstellt eine Cursorabfrage für clientseitige.<br /><br />**gepufferte** ist die verkürzte Form der SQLSRV_CURSOR_CLIENT_BUFFERED.|  
  
Wenn eine Abfrage mehrere Resultsets generiert die **Scrollable** Option gilt für alle Resultsets.  
  
## <a name="selecting-rows-in-a-result-set"></a>Auswählen von Zeilen in einem Resultset  
Nachdem Sie ein Resultset erstellen, können Sie [Sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md), [Sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md), oder [Sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) eine Zeile an.  
  
Die folgende Tabelle beschreibt die Werte Sie, in angeben können der *Zeile* Parameter.  
  
|Parameter|und Beschreibung|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|Gibt die nächste Zeile an. Dies ist der Standardwert, wenn Sie keinen angeben der *Zeile* Parameter für einen Satz scrollfähigen Resultsets.|  
|SQLSRV_SCROLL_PRIOR|Gibt die Zeile vor der aktuellen Zeile.|  
|SQLSRV_SCROLL_FIRST|Gibt die erste Zeile im Resultset an.|  
|SQLSRV_SCROLL_LAST|Gibt die letzte Zeile im Resultset an.|  
|SQLSRV_SCROLL_ABSOLUTE|Gibt an, der Zeile angegeben wird, mit der *Offset* Parameter.|  
|SQLSRV_SCROLL_RELATIVE|Gibt an, der Zeile angegeben wird, mit der *Offset* Parameter aus der aktuellen Zeile.|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>Serverseitige Cursor und den SQLSRV-Treiber  
Das folgende Beispiel zeigt die Auswirkungen der verschiedenen Cursor. Auf Zeile 33 des Beispiels sehen Sie die erste von drei abfrageanweisungen, die verschiedene Cursor angeben.  Zwei der dem abfrageanweisungen auskommentiert werden. Jedes Mal, wenn Sie das Programm ausführen, verwenden eines anderen Cursortyps, um die Auswirkungen des Datenbankupdates in Zeile 47 anzuzeigen.  
  
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
  
## <a name="client-side-cursors-and-the-sqlsrv-driver"></a>Clientseitige Cursor und den SQLSRV-Treiber  
Clientseitige Cursor sind ein Feature in Version 3.0 von der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] , mit der Sie ein komplettes Resultset im Arbeitsspeicher zwischengespeichert. Anzahl der Zeilen ist verfügbar, nachdem die Abfrage ausgeführt wird, wenn Sie einen clientseitigen Cursor verwenden.  
  
Clientseitige Cursor eignen sich für kleine bis mittelgroße Resultsets. Verwenden Sie serverseitige Cursor für große Resultsets an.  
  
Eine Abfrage wird "false" ist der Puffer nicht groß genug für das gesamte Resultset zurück. Sie können die Puffergröße bis zur Grenze des PHP-Speichers erhöhen.  
  
Mit dem SQLSRV-Treiber können Sie konfigurieren, die Größe des Puffers, das Resultset mit der Einstellung ClientBufferMaxKBSize für enthält [Sqlsrv_configure](../../connect/php/sqlsrv-configure.md). [Sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) gibt den Wert der ClientBufferMaxKBSize zurück. Sie können auch die maximale Puffergröße in der Datei "PHP.ini" mit Sqlsrv festlegen. ClientBufferMaxKBSize (z. B. Sqlsrv. ClientBufferMaxKBSize = 1024).  
  
Das folgende Beispiel zeigt:  
  
-   Zeilenanzahl ist immer verfügbar, mit einem clientseitigen Cursor.  
  
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
  
Das folgende Beispiel zeigt einen clientseitigen Cursor verwenden [Sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) und einem anderen Client-Puffergröße.
  
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
  
