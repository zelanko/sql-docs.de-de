---
title: PDO::query | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f6f5e6d4-8ca9-4f06-89ed-de65ad3952a2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 809ced4a32081375ebd98c61f7429c22e06cb90a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919167"
---
# <a name="pdoquery"></a>PDO::query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Führt eine SQL-Abfrage aus und gibt ein Resultset als PDOStatement-Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PDOStatement PDO::query ($statement[, $fetch_style);  
```  
  
#### <a name="parameters"></a>Parameter  
*$statement*: Die SQL-Anweisung, die Sie ausführen möchten.  
  
*$fetch_style:* Die optionalen Anweisungen zum Ausführen der Abfrage. Weitere Details finden Sie im Abschnitt „Anmerkungen“. $ *$fetch_style* in PDO::query kann mit $*fetch_style* in PDO::fetch überschrieben werden.  
  
## <a name="return-value"></a>Rückgabewert  
Wenn der Aufruf erfolgreich ist, gibt PDO::query ein PDOStatement-Objekt zurück. Wenn der Aufruf fehlschlägt, löst PDO::query ein PDOException-Objekt aus oder gibt „false“ zurück, abhängig von der Einstellung für PDO::ATTR_ERRMODE.  
  
## <a name="exceptions"></a>Ausnahmen  
PDOException  
  
## <a name="remarks"></a>Bemerkungen  
Bei einer mithilfe von PDO::query ausgeführten Abfrage wird entweder eine vorbereitete Anweisung ausgeführt, oder die Abfrage wird direkt durchgeführt. Dies hängt von der Einstellung für PDO::SQLSRV_ATTR_DIRECT_QUERY ab. Weitere Informationen finden Sie unter [Direkte Anweisungsausführung und vorbereitete Anweisungsausführung im PDO_SQLSRV-Treiber](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).  
  
PDO::SQLSRV_ATTR_QUERY_TIMEOUT wirkt sich auf das Verhalten von PDO::exec aus. Weitere Informationen finden Sie unter [PDO::setAttribute](../../connect/php/pdo-setattribute.md).  
  
Sie können die folgenden Optionen für $*fetch_style* angeben.  
  
|Style|BESCHREIBUNG|  
|---------|---------------|  
|PDO::FETCH_COLUMN, *num*|Abfragen von Daten in der angegebenen Spalte. Die erste Spalte in der Tabelle ist die Spalte „0“.|  
|PDO::FETCH_CLASS, '*Klassenname*', array( *Argumentliste* )|Erstellt eine Instanz einer Klasse und weist Eigenschaften in der Klasse Spaltennamen zu. Wenn der Konstruktor der Klasse einen oder mehrere Parameter akzeptiert, können Sie auch eine *arglist*übergeben.|  
|PDO::FETCH_CLASS, '*classname*'|Weist Eigenschaften in einer vorhandenen Klasse Spaltennamen zu|  
  
Rufen Sie vor dem erneuten Aufrufen von PDO::query das PDOStatement::closeCursor auf, um zum PDOSTATEMENT-Objekt gehörende Datenbankressourcen freizugeben.  
  
Sie können ein PDOStatement-Objekt schließen, indem Sie dafür den Wert NULL festlegen.  
  
Wird für alle Daten in einem Resultset kein Abrufvorgang (FETCH) ausgeführt, wird der nächste Aufruf PDO::query nicht fehlschlagen.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Dieses Beispiel zeigt mehrere Abfragen.  
  
```  
<?php  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
$conn->setAttribute( PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 1 );  
  
$query = 'select * from Person.ContactType';  
  
// simple query  
$stmt = $conn->query( $query );  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print_r( $row['Name'] ."\n" );  
}  
  
echo "\n........ query for a column ............\n";  
  
// query for one column  
$stmt = $conn->query( $query, PDO::FETCH_COLUMN, 1 );  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query with a new class ............\n";  
$query = 'select * from HumanResources.Department order by GroupName';  
// query with a class  
class cc {  
   function __construct( $arg ) {  
      echo "$arg";  
   }  
  
   function __toString() {  
      return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
   }  
}  
  
$stmt = $conn->query( $query, PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query into an existing class ............\n";  
$c_obj = new cc( '' );  
$stmt = $conn->query( $query, PDO::FETCH_INTO, $c_obj );  
while ( $stmt->fetch() ){  
   echo "$c_obj\n";  
}  
  
$stmt = null;  
?>  
```

## <a name="example"></a>Beispiel
In diesem Codebeispiel wird das Erstellen einer Tabelle mit Werten des Datentyps [sql_variant](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql) und das Abrufen der eingefügten Daten veranschaulicht.

```
<?php
$server = 'serverName';
$dbName = 'databaseName';
$uid = 'yourUserName';
$pwd = 'yourPassword';

$conn = new PDO("sqlsrv:server=$server; database = $dbName", $uid, $pwd);
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  

try {
    $tableName = 'testTable';
    $query = "CREATE TABLE $tableName ([c1_int] sql_variant, [c2_varchar] sql_variant)";

    $stmt = $conn->query($query);
    unset($stmt);

    $query = "INSERT INTO [$tableName] (c1_int, c2_varchar) VALUES (1, 'test_data')";
    $stmt = $conn->query($query);
    unset($stmt);

    $query = "SELECT * FROM $tableName";
    $stmt = $conn->query($query);

    $result = $stmt->fetch(PDO::FETCH_ASSOC);
    print_r($result);
    
    unset($stmt);
    unset($conn);
} catch (Exception $e) {
    echo $e->getMessage();
}
?>
```

Die erwartete Ausgabe sieht wie folgt aus:

```
Array
(
    [c1_int] => 1
    [c2_varchar] => test_data
)
```

## <a name="see-also"></a>Weitere Informationen  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
