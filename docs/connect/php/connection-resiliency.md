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
manager: v-mabarw
ms.openlocfilehash: 3edba0cde94d8661eed053319142ce7f84a70613
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265168"
---
# <a name="idle-connection-resiliency"></a>Resilienz von Verbindungen im Leerlauf
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Die [verbindungsresilienz](../odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) ist das Prinzip, dass eine Verbindung mit einem unterbrochenen Leerlauf innerhalb bestimmter Einschränkungen wieder hergestellt werden kann. Wenn eine Verbindung mit Microsoft SQL Server fehlschlägt, kann der Client automatisch versuchen, die Verbindung wiederherzustellen. Die verbindungsresilienz ist eine Eigenschaft der Datenquelle. nur SQL Server 2014 und höher und Azure SQL-Datenbank unterstützen Verbindungs Resilienz.

Verbindungsresilienz wird mit zwei Verbindungs Schlüsselwörtern implementiert, die Verbindungs Zeichenfolgen hinzugefügt werden können: **connectretrycount** und **connectretryinterval**.

|Schlüsselwort|Werte|Default|und Beschreibung|
|-|-|-|-|
|**ConnectRetryCount**| Ganze Zahl von 0 bis 255|1|Die maximale Anzahl von versuchen, eine unterbrochene Verbindung wiederherzustellen, bevor Sie den Wert aufgibt. Standardmäßig wird ein einziger Versuch unternommen, eine Verbindung wiederherzustellen, wenn Sie beschädigt ist. Der Wert 0 bedeutet, dass keine erneute Verbindung versucht wird.|
|**ConnectRetryInterval**| Ganze Zahl von 1 bis 60|1| Die Zeit (in Sekunden) zwischen den versuchen, eine Verbindung wiederherzustellen. Die Anwendung versucht, die Verbindung sofort nach dem Erkennen einer unterbrochenen Verbindung wiederherzustellen, und wartet dann **connectretryinterval** Sekunden, bevor Sie den Vorgang wiederholen. Dieses Schlüsselwort wird ignoriert, wenn **connectretrycount** gleich 0 ist.

Wenn das Produkt von **connectretrycount** multipliziert mit **connectretryinterval** größer als **LoginTimeout**ist, versucht der Client, eine Verbindung herzustellen, nachdem **LoginTimeout** erreicht wurde. Andernfalls wird weiterhin versucht, erneut eine Verbindung herzustellen, bis **connectretrycount** erreicht ist.

#### <a name="remarks"></a>Remarks

Verbindungsresilienz gilt, wenn sich die Verbindung im Leerlauf befindet. Fehler, die beim Ausführen einer Transaktion auftreten, führen z. b. keine erneuten Verbindungsversuche aus, da Sie andernfalls nicht erwartungsgemäß erwartet werden. In den folgenden Situationen, die als nicht wiederherstellbare Sitzungs Zustände bezeichnet werden, werden keine erneuten Verbindungsversuche auslöst:

* Temporäre Tabellen
* Globale und lokale Cursor
* Transaktions-und Sitzungs Ebene-Transaktions Sperren
* Anwendungssperren
* EXECUTE AS/REVERT Security Context
* OLE-Automatisierungs Handles
* Vorbereitete XML-Handles
* Ablaufverfolgungsflags

## <a name="example"></a>Beispiel

Der folgende Code stellt eine Verbindung mit einer-Datenbank her und führt eine Abfrage aus. Die Verbindung wird unterbrochen, indem die Sitzung abgebrochen wird, und es wird versucht, mithilfe der unterbrochenen Verbindung eine neue Abfrage auszuführen. In diesem Beispiel wird die [AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx)-Beispieldatenbank verwendet.

In diesem Beispiel geben wir einen gepufferten Cursor an, bevor die Verbindung unterbrochen wird. Wenn wir keinen gepufferten Cursor angeben, wird die Verbindung nicht wieder hergestellt, da es einen aktiven serverseitigen Cursor gäbe und die Verbindung daher nicht im Leerlauf ist, wenn Sie beschädigt ist. In diesem Fall könnten wir jedoch sqlsrv_free_stmt () vor dem Trennen der Verbindung zum Verlassen des Cursors aufzurufen, und die Verbindung wird erfolgreich wieder hergestellt.

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
