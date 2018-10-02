---
title: 'PDO:: Prepare | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca5e1a4d0dd3f76b3fabefa6549eb644a894845a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745138"
---
# <a name="pdoprepare"></a>PDO::prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Bereitet eine Anweisung für die Ausführung vor.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PDOStatement PDO::prepare ( $statement [, array(key_pair)] )  
```  
  
#### <a name="parameters"></a>Parameter  
$*statement*: Eine Zeichenfolge, die die SQL-Anweisung enthält.  
  
*key_pair:* Ein Array, das einen Attributnamen und einen Wert enthält. Weitere Informationen finden Sie im Abschnitt zu den Hinweisen.  
  
## <a name="return-value"></a>Rückgabewert  
Bei Erfolg wird ein PDOStatement-Objekt zurückgegeben. Bei einem Fehler wird entweder ein PDOException-Objekt oder „false“ zurückgegeben, abhängig vom Wert für PDO::ATTR_ERRMODE.  
  
## <a name="remarks"></a>Remarks  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] wertet keine vorbereiteten Anweisungen vor der Ausführung aus.  
  
In der folgenden Tabelle sind die möglichen Werte für *key_pair* aufgelistet.  
  
|Key|und Beschreibung|  
|-------|---------------|  
|PDO::ATTR_CURSOR|Definiert das Cursorverhalten. Der Standardwert ist „PDO::CURSOR_FWDONLY“. Mit „PDO::CURSOR_SCROLL“ ist der Cursor statisch.<br /><br />Beispiel: `array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY )`.<br /><br />Wenn Sie „PDO::CURSOR_SCROLL“ verwenden, können wie nachstehend beschrieben Sie auch „PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE“ verwenden.<br /><br />Weitere Informationen zu Ergebnismengen und Cursorn im PDO_SQLSRV-Treiber finden Sie unter [Cursortypen &#40;PDO_SQLSRV-Treiber&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::ATTR_EMULATE_PREPARES|Dieses Attribut wird standardmäßig "false" kann von dieser geändert werden `PDO::ATTR_EMULATE_PREPARES => true`. Finden Sie unter [emulieren vorbereiten](#emulate-prepare) Einzelheiten und Beispiel.|
|PDO::SQLSRV_ATTR_ENCODING|PDO::SQLSRV_ENCODING_UTF8 (Standard)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|Wird hierfür der Wert „true“ festgelegt, werden Abfragen direkt ausgeführt. Der Wert „false“ sorgt dafür, dass vorbereitete Anweisungen ausgeführt werden. Weitere Informationen zu PDO::SQLSRV_ATTR_DIRECT_QUERY finden Sie unter [Direkte Anweisungsausführung und vorbereitete Anweisungsausführung im PDO_SQLSRV-Treiber](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Weitere Informationen finden Sie unter [PDO::setAttribute](../../connect/php/pdo-setattribute.md).|  
  
Wenn Sie „PDO::CURSOR_SCROLL“ verwenden, können Sie auch „PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE“ verwenden. Beispiel:  
  
```  
array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_DYNAMIC));  
```  
  
In der folgenden Tabelle sind die möglichen Werte für „PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE“ aufgelistet.  
  
|value|und Beschreibung|  
|---------|---------------|  
|PDO::SQLSRV_CURSOR_BUFFERED|Erstellt einen clientseitigen statischen Cursor (gepuffert). Weitere Informationen zu clientseitigen Cursorn finden Sie unter [Cursortypen &#40;PDO_SQLSRV-Treiber&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_CURSOR_DYNAMIC|Erstellt einen serverseitigen (gepufferten) dynamischen Cursor, der es Ihnen erlaubt, auf Zeilen in beliebiger Reihenfolge zuzugreifen und Änderungen in der Datenbank widerspiegelt.|  
|PDO::SQLSRV_CURSOR_KEYSET_DRIVEN|Erstellt einen serverseitigen Keysetcursor. Ein Keysetcursor aktualisiert nach dem Löschen einer Zeile aus einer Tabelle nicht die Zeilenanzahl (eine gelöschte Zeile wird ohne Werte zurückgegeben).|  
|PDO::SQLSRV_CURSOR_STATIC|Erstellt einen serverseitigen statischen Cursor, der es Ihnen zwar erlaubt, auf Zeilen in beliebiger Reihenfolge zuzugreifen, aber die Änderungen in der Datenbank nicht widerspiegelt.<br /><br />„PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL“ ist standardmäßig mit „PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_STATIC“ vorbelegt.|  
  
Sie können ein PDOStatement-Objekt schließen, indem Sie dafür den Wert NULL festlegen.  
  
## <a name="example"></a>Beispiel  
In diesem Beispiel wird erläutert, wie Sie die Methode „PDO::prepare“ mit Parametermarkern und einem Vorwärtscursor verwenden.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table1(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
echo "\n";  
  
$query = "insert into Table1(col1, col2) values(:col1, :col2)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( ':col1' => $col1, ':col2' => $col2 ) );  
print $stmt->rowCount();  
  
$stmt = null  
?>  
```  

## <a name="example"></a>Beispiel  
In diesem Beispiel wird veranschaulicht, wie Sie die PDO::prepare-Methode mit einem clientseitigen Cursor verwenden. Ein Beispiel für einen serverseitigen Cursor finden Sie unter [Cursortypen &#40;PDO_SQLSRV-Treiber&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  

<a name="emulate-prepare" />

## <a name="example"></a>Beispiel 

Dieses Beispiel zeigt, wie die Methode PDO :: prepare mit `PDO::ATTR_EMULATE_PREPARES` auf true gesetzt wird. 

```
<?php
$serverName = "yourservername";
$username = "yourusername";
$password = "yourpassword";
$database = "tempdb";
$conn = new PDO("sqlsrv:server = $serverName; Database = $database", $username, $password);

$pdo_options = array();
$pdo_options[PDO::ATTR_EMULATE_PREPARES] = true;
$pdo_options[PDO::SQLSRV_ATTR_ENCODING] = PDO::SQLSRV_ENCODING_UTF8;

$stmt = $conn->prepare("CREATE TABLE TEST([id] [int] IDENTITY(1,1) NOT NULL, 
                                          [name] nvarchar(max))", 
                                          $pdo_options);
$stmt->execute();

$prefix = '가각';
$name = '가각ácasa';
$name2 = '가각sample2';

$stmt = $conn->prepare("INSERT INTO TEST(name) VALUES(:p0)", $pdo_options);
$stmt->execute(['p0' => $name]);
unset($stmt);

$stmt = $conn->prepare("SELECT * FROM TEST WHERE NAME LIKE :p0", $pdo_options);
$stmt->execute(['p0' => "$prefix%"]);
foreach ($stmt as $row) {
    echo "\n" . 'FOUND: ' . $row['name'];
}

unset($stmt);
unset($conn);
?>
```

Der PDO_SQLSRV-Treiber ersetzt alle Platzhalter intern mit den Parametern, die gebunden werden, indem [PDOStatement::bindParam()](../../connect/php/pdostatement-bindparam.md). Aus diesem Grund wird eine SQL-Abfragezeichenfolge mit keine Platzhalter an den Server gesendet. Betrachten Sie dieses Beispiel

```
$statement = $PDO->prepare("INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)");
$statement->bindParam(:cus_name, "Cardinal");
$statement->bindParam(:con_name, "Tom B. Erichsen");
$statement->execute();
```

Mit `PDO::ATTR_EMULATE_PREPARES` festgelegt auf "false" (der Standardfall), die Daten an die Datenbank gesendet werden:

```
"INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)"
Information on :cus_name parameter
Information on :con_name parameter
```

Der Server wird die Abfrage, die über das Feature für die parametrisierte Abfrage für das Binden von Parametern ausführen. Auf der anderen Seite mit `PDO::ATTR_EMULATE_PREPARES` auf True festgelegt, die an den Server gesendete Abfrage ist im Wesentlichen:

```
"INSERT into Customers (CustomerName, ContactName) VALUES ('Cardinal', 'Tom B. Erichsen')"
```

Festlegen von `PDO::ATTR_EMULATE_PREPARES` auf "true" einige Einschränkungen in SQL Server kann umgangen werden. SQL Server unterstützt beispielsweise keine benannten oder positionellen Parameter in einige Transact-SQL-Klauseln. Darüber hinaus verfügt SQL Server maximal 2100 Bindungsparameter.

> [!NOTE]
> Mit Emulate bereitet auf True festgelegt, die Sicherheit von parametrisierten Abfragen ist nicht aktiv. Ihre Anwendung sollte deshalb sicherstellen, dass die an den bzw. die Parameter gebunden Daten keinen bösartigen Transact-SQL-Code enthalten.

### <a name="encoding"></a>Codierung

Wenn der Benutzer möchte zum Binden von Parametern mit verschiedenen Codierungen (z. B. UTF-8 oder binär), sollte der Benutzer eindeutig angeben der Codierung in PHP-Skripts.

Der PDO_SQLSRV-Treiber überprüft zuerst, die angegebene Codierung `PDO::bindParam()` (z. B. `$statement->bindParam(:cus_name, "Cardinal", PDO::PARAM_STR, 10, PDO::SQLSRV_ENCODING_UTF8)`). 

Wenn der Treiber wurde nicht gefunden, überprüft werden, wenn Codierung, im festgelegt ist `PDO::prepare()` oder `PDOStatement::setAttribute()`. Andernfalls wird der Treiber die angegebene Codierung verwenden `PDO::__construct()` oder `PDO::setAttribute()`.

### <a name="limitations"></a>Einschränkungen

Wie Sie sehen können, erfolgt die Bindung intern durch den Treiber. Eine gültige Abfrage wird für die Ausführung ohne Parameter an den Server gesendet. Im Vergleich zu im Normalfall, führen einige Einschränkungen, wenn das Feature für die parametrisierte Abfrage nicht verwendet wird.

- Es funktioniert nicht für Parameter, die als gebunden wurden `PDO::PARAM_INPUT_OUTPUT`.
    - Wenn der Benutzer gibt `PDO::PARAM_INPUT_OUTPUT` in `PDO::bindParam()`, eine PDO-Ausnahme ausgelöst wird.
- Es funktioniert nicht für Parameter, die als Ausgabeparameter gebunden sind.
    - Wenn der Benutzer eine vorbereitete Anweisung mit Platzhaltern erstellt gelten für das Output-Parameter (, also müssen ein Gleichheitszeichen unmittelbar nach dem ein Platzhalter, z. B. `SELECT ? = COUNT(*) FROM Table1`), eine PDO-Ausnahme ausgelöst wird.
    - Wenn eine vorbereitete Anweisung eine gespeicherte Prozedur mit einem Platzhalter als Argument für ein Output-Parameter aufruft, wird keine Ausnahme ausgelöst, da der Treiber den Output-Parameter nicht erkannt werden. Die Variable, die der Benutzer für den Ausgabeparameter bleibt jedoch unverändert.
- Doppelte Platzhalter für einen binären codierten Parameter funktioniert nicht

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
