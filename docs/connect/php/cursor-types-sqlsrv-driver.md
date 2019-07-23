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
ms.openlocfilehash: ac090ad8831397bf31c0911ab8a8db21486528db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015115"
---
# <a name="cursor-types-sqlsrv-driver"></a>Cursortypen (SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Mit dem SQLSRV-Treiber können Sie ein Resultset mit Zeilen erstellen, auf die Sie in beliebiger Reihenfolge (abhängig vom Cursortyp) zugreifen können.  In diesem Thema werden Client seitige (gepufferte) und serverseitige (nicht gepufferte) Cursor behandelt.  
  
## <a name="cursor-types"></a>Cursortypen  
Wenn Sie ein Resultset mit [sqlsrv_query](../../connect/php/sqlsrv-query.md) oder mit [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)erstellen, können Sie den Cursortyp angeben. Standardmäßig wird ein Vorwärts Cursor verwendet, mit dem Sie zeilenweise beginnend an der ersten Zeile des Resultsets verschieben können, bis Sie das Ende des Resultsets erreichen.  
  
Sie können ein Resultset mit einem Bild lauffähigen Cursor erstellen, mit dem Sie in beliebiger Reihenfolge auf eine beliebige Zeile im Resultset zugreifen können. In der folgenden Tabelle sind die Werte aufgeführt, die in sqlsrv_query oder sqlsrv_prepare an die **scrollable** -Option übermittelt werden können.  
  
|Option|und Beschreibung|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|Ermöglicht das Verschieben von Zeilen zu einem Zeitpunkt ab der ersten Zeile des Resultsets, bis das Ende des Resultsets erreicht ist.<br /><br />Dies ist der Standard Cursortyp.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) gibt einen Fehler für Resultsets zurück, die mit diesem Cursortyp erstellt wurden.<br /><br />**Forward** ist die abgekürzte Form von SQLSRV_CURSOR_FORWARD.|  
|SQLSRV_CURSOR_STATIC|Ermöglicht den Zugriff auf Zeilen in beliebiger Reihenfolge, aber die Änderungen in der Datenbank werden nicht widerspiegelt.<br /><br />**static** ist die abgekürzte Form von SQLSRV_CURSOR_STATIC.|  
|SQLSRV_CURSOR_DYNAMIC|Ermöglicht den Zugriff auf Zeilen in beliebiger Reihenfolge und spiegelt Änderungen in der Datenbank wider.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) gibt einen Fehler für Resultsets zurück, die mit diesem Cursortyp erstellt wurden.<br /><br />**Dynamic** ist die abgekürzte Form von SQLSRV_CURSOR_DYNAMIC.|  
|SQLSRV_CURSOR_KEYSET|Ermöglicht den Zugriff auf Zeilen in beliebiger Reihenfolge. Ein Keysetcursor aktualisiert nach dem Löschen einer Zeile aus einer Tabelle jedoch nicht die Zeilenanzahl (eine gelöschte Zeile wird ohne Werte zurückgegeben).<br /><br />**Keyset** ist die abgekürzte Form von SQLSRV_CURSOR_KEYSET.|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|Ermöglicht den Zugriff auf Zeilen in beliebiger Reihenfolge. Erstellt eine Client seitige Cursor Abfrage.<br /><br />**gepuffert** ist die abgekürzte Form von SQLSRV_CURSOR_CLIENT_BUFFERED.|  
  
Wenn eine Abfrage mehrere Resultsets generiert, gilt die **scrollable** -Option für alle Resultsets.  
  
## <a name="selecting-rows-in-a-result-set"></a>Auswählen von Zeilen in einem Resultset  
Nachdem Sie ein Resultset erstellt haben, können Sie mit [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md), [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)oder [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) eine Zeile angeben.  
  
In der folgenden Tabelle werden die Werte beschrieben, die Sie im *Zeilen* Parameter angeben können.  
  
|Parameter|und Beschreibung|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|Gibt die nächste Zeile an. Dies ist der Standardwert, wenn Sie den *Zeilen* Parameter für ein scrollbares Resultset nicht angeben.|  
|SQLSRV_SCROLL_PRIOR|Gibt die Zeile vor der aktuellen Zeile an.|  
|SQLSRV_SCROLL_FIRST|Gibt die erste Zeile im Resultset an.|  
|SQLSRV_SCROLL_LAST|Gibt die letzte Zeile im Resultset an.|  
|SQLSRV_SCROLL_ABSOLUTE|Gibt die mit dem *Offset* -Parameter angegebene Zeile an.|  
|SQLSRV_SCROLL_RELATIVE|Gibt die Zeile an, die mit dem *Offset* -Parameter aus der aktuellen Zeile angegeben wird.|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>Server seitige Cursor und der sqlsrv-Treiber  
Im folgenden Beispiel werden die Auswirkungen der verschiedenen Cursor veranschaulicht. In Zeile 33 des Beispiels sehen Sie die erste von drei Abfrage Anweisungen, die verschiedene Cursor angeben.  Zwei der Abfrage Anweisungen werden kommentiert. Jedes Mal, wenn Sie das Programm ausführen, verwenden Sie einen anderen Cursortyp, um die Auswirkung der Datenbankaktualisierung in Zeile 47 anzuzeigen.  
  
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
  
## <a name="client-side-cursors-and-the-sqlsrv-driver"></a>Client seitige Cursor und der sqlsrv-Treiber  
Client seitige Cursor sind ein Feature, das in Version 3,0 von hinzu [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] gefügt wurde, mit dem Sie ein gesamtes Resultset im Arbeitsspeicher zwischenspeichern können. Die Zeilen Anzahl ist verfügbar, nachdem die Abfrage ausgeführt wurde, wenn ein Client seitiger Cursor verwendet wird.  
  
Clientseitige Cursor eignen sich für kleine bis mittelgroße Resultsets. Verwenden Sie serverseitige Cursor für große Resultsets.  
  
Eine Abfrage gibt false zurück, wenn der Puffer nicht groß genug ist, um das gesamte Resultset zu speichern. Sie können die Puffergröße bis zur Grenze des PHP-Speichers erhöhen.  
  
Mit dem sqlsrv-Treiber können Sie die Größe des Puffers, der das Resultset enthält, mit der Einstellung clientbuffermaxkbsize für [sqlsrv_configure](../../connect/php/sqlsrv-configure.md)konfigurieren. [sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) gibt den Wert von clientbuffermaxkbsize zurück. Sie können auch die maximale Puffergröße in der Datei "php. ini" mit sqlsrv festlegen. Clientbuffermaxkbsize (z. b. sqlsrv). Clientbuffermaxkbsize = 1024).  
  
Das folgende Beispiel zeigt Folgendes:  
  
-   Die Zeilen Anzahl ist immer mit einem Client seitigen Cursor verfügbar.  
  
-   Verwendung von Client seitigen Cursorn und Batch Anweisungen.  
  
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
  
Das folgende Beispiel zeigt einen Client seitigen Cursor mit [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) und einer anderen Client Puffergröße.
  
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
  
