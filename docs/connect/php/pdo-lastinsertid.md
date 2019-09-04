---
title: 'PDO:: lastInsertId | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0c617b53-a74b-4d5b-b76b-3ec7f1b8e8de
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2068b4099649b7ebd8aa2bcb4c58aa0d59e123d0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936215"
---
# <a name="pdolastinsertid"></a>PDO::lastInsertId
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt den Bezeichner für eine Zeile an, die zuletzt in eine Tabelle in der Datenbank eingefügt wurde. Die Tabelle muss eine IDENTITY NOT NULL-Spalte enthalten. Wenn ein Sequenz Name bereitgestellt wird `lastInsertId` , wird die zuletzt eingefügte Sequenznummer für den angegebenen Sequenznamen zurückgegeben (Weitere Informationen zu Sequenznummern finden Sie [hier](https://docs.microsoft.com/sql/relational-databases/sequence-numbers/sequence-numbers)).
  
## <a name="syntax"></a>Syntax  
  
```  
  
string PDO::lastInsertId ([ $name = NULL ] );  
```  
  
#### <a name="parameters"></a>Parameter  
$*name*: Eine optionale Zeichenfolge, mit der Sie den Sequenznamen angeben können. 
  
## <a name="return-value"></a>Rückgabewert  
Wenn kein Sequenz Name angegeben wird, eine Zeichenfolge des Bezeichners für die Zeile, die zuletzt hinzugefügt wurde.
Wenn ein Sequenz Name angegeben wird, eine Zeichenfolge des Bezeichners für die Sequenz, die zuletzt hinzugefügt wurde.
Wenn der Methodenaufrufe fehlschlägt, wird eine leere Zeichenfolge zurückgegeben.
  
## <a name="remarks"></a>Bemerkungen  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
Zwischen Version 2,0 und 4,3 ist der optionale Parameter ein Tabellenname, und der Rückgabewert ist die ID der Zeile, die der bereitgestellten Tabelle zuletzt hinzugefügt wurde.
Ab 5,0 wird der optionale Parameter als Sequenz Name betrachtet, und der Rückgabewert ist die Sequenz, die zuletzt für den bereitgestellten Sequenznamen hinzugefügt wurde.
Wenn ein Tabellenname für Versionen nach 4,3 bereitgestellt wird `lastInsertId` , wird eine leere Zeichenfolge zurückgegeben.
Sequenzen werden nur in SQL Server 2012 und höher unterstützt.
  
## <a name="example"></a>Beispiel
  
```
<?php
$server = "myserver";
$databaseName = "mydatabase";
$uid = "myusername";
$pwd = "mypasword";

try {
    $conn = new PDO("sqlsrv:Server=$server;Database=$databaseName", $uid, $pwd);
    
    // One sequence, two tables
    $tableName1 = 'seqtable1';
    $tableName2 = 'seqtable2';
    $sequenceName = 'sequence1';

    $stmt = $conn->query("IF OBJECT_ID('$sequenceName', 'SO') IS NOT NULL DROP SEQUENCE $sequenceName");
    $sql = "CREATE TABLE $tableName1 (seqnum INTEGER NOT NULL PRIMARY KEY, SomeNumber INT)";
    $stmt = $conn->query($sql);
    $sql = "CREATE TABLE $tableName2 (ID INT IDENTITY(1,2), SomeValue char(10))";
    $stmt = $conn->query($sql);

    $sql = "CREATE SEQUENCE $sequenceName AS INTEGER START WITH 1 INCREMENT BY 1 MINVALUE 1 MAXVALUE 100 CYCLE";
    $stmt = $conn->query($sql);

    $ret = $conn->exec("INSERT INTO $tableName1 VALUES( NEXT VALUE FOR $sequenceName, 20)");
    $ret = $conn->exec("INSERT INTO $tableName1 VALUES( NEXT VALUE FOR $sequenceName, 40)");
    $ret = $conn->exec("INSERT INTO $tableName1 VALUES( NEXT VALUE FOR $sequenceName, 60)");
    $ret = $conn->exec("INSERT INTO $tableName2 VALUES( '20' )");
    
    // return the last sequence number if sequence name is provided
    $lastSeq1 = $conn->lastInsertId($sequenceName);
    
    // defaults to $tableName2 -- because it returns the last inserted id value
    $lastRow = $conn->lastInsertId();
        
    // providing a table name in lastInsertId should return an empty string
    $lastSeq2 = $conn->lastInsertId($tableName2);
    
    echo "Last sequence number = $lastSeq1\n";
    echo "Last inserted ID     = $lastRow\n";
    echo "Last inserted ID when a table name is supplied = $lastSeq2\n";

    // One table, two sequences    
    $tableName = 'seqtable';
    $sequence1 = 'sequence1';
    $sequence2 = 'sequenceNeg1';
    $stmt = $conn->query("IF OBJECT_ID('$sequence1', 'SO') IS NOT NULL DROP SEQUENCE $sequence1");
    $stmt = $conn->query("IF OBJECT_ID('$sequence2', 'SO') IS NOT NULL DROP SEQUENCE $sequence2");
    $sql = "CREATE TABLE $tableName (ID INT IDENTITY(1,1), SeqNumInc INTEGER NOT NULL PRIMARY KEY, SomeNumber INT)";
    $stmt = $conn->query($sql);
    $sql = "CREATE SEQUENCE $sequence1 AS INTEGER START WITH 1 INCREMENT BY 1 MINVALUE 1 MAXVALUE 100";
    $stmt = $conn->query($sql);

    $sql = "CREATE SEQUENCE $sequence2 AS INTEGER START WITH 200 INCREMENT BY -1 MINVALUE 101 MAXVALUE 200";
    $stmt = $conn->query($sql);
    $ret = $conn->exec("INSERT INTO $tableName VALUES( NEXT VALUE FOR $sequence1, 20 )");
    $ret = $conn->exec("INSERT INTO $tableName VALUES( NEXT VALUE FOR $sequence2, 180 )");
    $ret = $conn->exec("INSERT INTO $tableName VALUES( NEXT VALUE FOR $sequence1, 40 )");
    $ret = $conn->exec("INSERT INTO $tableName VALUES( NEXT VALUE FOR $sequence2, 160 )");
    $ret = $conn->exec("INSERT INTO $tableName VALUES( NEXT VALUE FOR $sequence1, 60 )");
    $ret = $conn->exec("INSERT INTO $tableName VALUES( NEXT VALUE FOR $sequence2, 140 )");
    
    // return the last sequence number of 'sequence1'
    $lastSeq1 = $conn->lastInsertId($sequence1);

    // return the last sequence number of 'sequenceNeg1'
    $lastSeq2 = $conn->lastInsertId($sequence2);

    // providing a table name in lastInsertId should return an empty string
    $lastSeq3 = $conn->lastInsertId($tableName);
    
    echo "Last sequence number of sequence1    = $lastSeq1\n";
    echo "Last sequence number of sequenceNeg1 = $lastSeq2\n";
    echo "Last sequence number when a table name is supplied = $lastSeq3\n";

    $stmt = $conn->query("DROP TABLE $tableName1");
    $stmt = $conn->query("DROP TABLE $tableName2");
    $stmt = $conn->query("DROP SEQUENCE $sequenceName");
    $stmt = $conn->query("DROP TABLE $tableName");
    $stmt = $conn->query("DROP SEQUENCE $sequence1");
    $stmt = $conn->query("DROP SEQUENCE $sequence2");
    
    unset($stmt);
    unset($conn);
} catch (Exception $e) {
    echo "Exception $e\n";
}

?>
```

Die erwartete Ausgabe lautet:

```
Last sequence number = 3
Last inserted ID     = 1
Last inserted ID when a table name is supplied =

Last sequence number of sequence1    = 3
Last sequence number of sequenceNeg1 = 198
Last sequence number when a table name is supplied = 

```

## <a name="see-also"></a>Weitere Informationen  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
