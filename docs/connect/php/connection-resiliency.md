---
title: Resilienz von Verbindungen im Leerlauf
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: a2361c8a2e8cbc709d50a9139678a08e2e850e2d
ms.sourcegitcommit: 7d4a3fc0f2622cbc6930d792be4a9b3fcac4c4b6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58305918"
---
# <a name="idle-connection-resiliency"></a>Resilienz von Verbindungen im Leerlauf
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Verbindungsresilienz](../odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) geht es darum, eine unterbrochene Verbindung des im Leerlauf, bestimmte Einschränkungen erneut hergestellt werden kann. Wenn Sie eine Verbindung mit Microsoft SQL Server ein Fehler auftritt, kann resilienz von Verbindungen der Client automatisch versuchen, die Verbindung wiederherzustellen. Resilienz von Verbindungen ist eine Eigenschaft der Datenquelle. nur SQLServer 2014 und höher und Azure SQL-Datenbank unterstützen die resilienz von Verbindungen.

Verbindungsresilienz wird implementiert, mit zwei Verbindungsschlüsselwörter, die Verbindungszeichenfolgen hinzugefügt werden können: **ConnectRetryCount** und **ConnectRetryInterval**.

|Schlüsselwort|Werte|Default|und Beschreibung|
|-|-|-|-|
|**ConnectRetryCount**| Ganze Zahl zwischen 0 und 255 (inklusiv)|1|Die maximale Anzahl von versuchen, eine unterbrochene Verbindung, bevor aufgegeben wird wiederherzustellen. Standardmäßig wird eine einzelne versucht, eine Verbindung, wenn in einem wiederherzustellen. Ein Wert von 0 bedeutet, dass keine erneute Verbindung versucht wird.|
|**ConnectRetryInterval**| Ganze Zahl zwischen 1 und 60 (inklusiv)|1| Die Zeit in Sekunden zwischen den versuchen, eine Verbindung wiederherzustellen. Die Anwendung versucht, sofort nach der Erkennung einer fehlerhaften Verbindungs erneut eine Verbindung herzustellen, und klicken Sie dann wartet **ConnectRetryInterval** Sekunden, bevor Sie es erneut zu versuchen. Dieses Schlüsselwort wird ignoriert, wenn **ConnectRetryCount** ist gleich 0.

Wenn das Produkt der **ConnectRetryCount** multipliziert **ConnectRetryInterval** ist größer als **LoginTimeout**, und klicken Sie dann der Client nicht versuchen mehr, sobald eine Verbindung  **LoginTimeout** erreicht wird; andernfalls wird es weiterhin, bis eine Verbindung zu testen **ConnectRetryCount** erreicht ist.

#### <a name="remarks"></a>Remarks

Verbindungsresilienz gilt, wenn die Verbindung im Leerlauf befindet. Fehler auftreten, während der Ausführung einer Transaktion, z. B. Versuche der verbindungswiederherstellung – nicht ausgelöst wird schlägt sie fehl, da sonst zu erwarten wäre. Die folgenden Situationen, bekannt als Sitzungsstatus nicht behoben werden kann, löst keine erneute Verbindung Versuche:

* Temporäre Tabellen 
* Globale und lokale Cursor
* Kontext und der angegebenen Sitzung Transaktion Transaktionssperren
* Anwendungssperren
* EXECUTE AS / Sicherheitskontext wiederherstellen
* OLE-Automatisierung behandelt
* Vorbereitete XML-handles
* Ablaufverfolgungsflags

## <a name="example"></a>Beispiel

Der folgende Code eine Verbindung mit einer Datenbank her und führt eine Abfrage. Die Verbindung unterbrochen wird, von der Sitzung zu beenden und eine neue Abfrage über die unterbrochene Verbindung versucht wird. In diesem Beispiel wird die [AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx)-Beispieldatenbank verwendet.

In diesem Beispiel geben wir einen zwischengespeicherten Cursor vor dem Unterbrechen der Verbindungs an. Wenn wir einen zwischengespeicherten Cursor nicht angeben, würde die Verbindung nicht wiederhergestellt werden, da es aktiver serverseitige Cursor gäbe und folglich die Verbindung nicht im Leerlauf, wenn in einem. Allerdings in diesem Fall können wir vor dem Unterbrechen der Verbindungs, um den Cursor vacate sqlsrv_free_stmt() aufrufen, und die Verbindung wurde erfolgreich wiederhergestellt werden sollen.

```php
<?php
// This function breaks the connection by determining its session ID and killing it.
// A separate connection is used to break the main connection because a session
// cannot kill itself. The sleep() function ensures enough time has passed for KILL
// to finish ending the session.
function BreakConnection( $conn, $conn_break )
{
    $stmt1 = sqlsrv_query( $conn, "SELECT @@SPID" );
    if ( sqlsrv_fetch( $stmt1 ) )
    {
        $spid=sqlsrv_get_field( $stmt1, 0 );
    }

    $stmt2 = sqlsrv_prepare( $conn_break, "KILL ".$spid );
    sqlsrv_execute( $stmt2 );
    sleep(1);
}

// Connect to the local server using Windows authentication and specify
// AdventureWorks as the database in use. Specify values for
// ConnectRetryCount and ConnectRetryInterval as well.
$databaseName = 'AdventureWorks2014';
$serverName = '(local)';
$connectionInfo = array( "Database"=>$databaseName, "ConnectRetryCount"=>10, "ConnectRetryInterval"=>10 );

$conn = sqlsrv_connect( $serverName, $connectionInfo );
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}

// A separate connection that will be used to break the main connection $conn
$conn_break = sqlsrv_connect( $serverName, array( "Database"=>$databaseName) );

// Create a statement to retrieve the contents of a table
$stmt1 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Employee",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt1 === false )
{
     echo "Error in statement 1.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 1 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt1 );
    echo $rowcount." rows in result set.\n";
}

// Now break the connection $conn
BreakConnection( $conn, $conn_break );

// Create another statement. The connection will be reestablished.
$stmt2 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Department",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt2 === false )
{
     echo "Error in statement 2.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 2 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt2 );
    echo $rowcount." rows in result set.\n";
}

sqlsrv_close( $conn );
sqlsrv_close( $conn_break );
?>
```
Erwartete Ausgabe:
```
Statement 1 successful.
290 rows in result set.
Statement 2 successful.
16 rows in result set.
```

## <a name="see-also"></a>Weitere Informationen
[Verbindungsresilienz im Windows ODBC-Treiber](../odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)
