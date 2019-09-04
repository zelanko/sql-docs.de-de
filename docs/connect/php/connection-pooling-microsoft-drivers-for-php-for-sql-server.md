---
title: Verbindungspooling (Microsoft-Treiber für PHP für SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 13e1075cd25fa352543837afa31ff2a3d540704f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015121"
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>Verbindungspooling (Microsoft Drivers for PHP for SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Folgende wichtige Punkte sollten Sie für das Verbindungspooling in [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]beachten:  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] verwendet ODBC-Verbindungspooling.  
  
-   Das Verbindungspooling ist in Windows standardmäßig aktiviert. Unter Linux und macOS werden Verbindungen nur in einem Pool zusammengefasst, wenn Verbindungspooling für ODBC aktiviert ist (siehe [Aktivieren/Deaktivieren von Verbindungspooling](#enablingdisabling-connection-pooling)). Wenn das Verbindungspooling aktiviert ist und Sie eine Verbindung mit einem Server herstellen, versucht der Treiber, eine gepoolte Verbindung zu verwenden, bevor eine neue erstellt wird. Falls im Pool keine äquivalente Verbindung gefunden wird, wird eine neue Verbindung erstellt und dem Pool hinzugefügt. Basierend auf einem Vergleich der Verbindungszeichenfolgen, ermittelt der Treiber  ob die Verbindungen äquivalent sind.  
  
-   Wenn eine Verbindung aus dem Pool verwendet wird, wird der Verbindungsstatus zurückgesetzt.  
  
-   Das Schließen der Verbindung gibt die Verbindung an den Pool zurück.  
  
Weitere Informationen zum Verbindungspooling finden Sie unter [Treiber-Manager-Verbindungspooling](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="enablingdisabling-connection-pooling"></a>Aktivieren/Deaktivieren von Verbindungspooling
### <a name="windows"></a>Windows
Sie können den Treiber zwingen, eine neue Verbindung zu erstellen (anstatt nach einer äquivalenten Verbindung im Verbindungspool zu suchen), indem Sie den Wert des *ConnectionPooling*-Attributs in der Verbindungszeichenfolge auf **false** (oder 0) festlegen.  
  
Falls das *ConnectionPooling*-Attribut aus der Verbindungszeichenfolge weggelassen oder auf **true** (oder 1) festgelegt wird, erstellt der Treiber nur dann eine neue Verbindung, wenn es keine äquivalente Verbindung im Verbindungspool gibt.  
  
Weitere Informationen zu weiteren Verbindungsattributen finden Sie unter [Connection Options](../../connect/php/connection-options.md).  
### <a name="linux-and-macos"></a>Linux und macOS
Das *ConnectionPooling* -Attribut kann nicht verwendet werden, um Verbindungspooling zu aktivieren bzw. zu deaktivieren. 

Das Verbindungspooling kann aktiviert bzw. deaktiviert werden, indem Sie die Konfigurationsdatei "Odbcinst. ini" bearbeiten. Der Treiber sollte erneut geladen werden, damit die Änderungen wirksam werden.

Wenn `Pooling` Sie `Yes` auf und einen `CPTimeout` positiven Wert in der Datei "Odbcinst. ini" festlegen, wird das Verbindungspooling ermöglicht. 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
  
Die Datei "Odbcinst. ini" sollte in etwa wie in diesem Beispiel aussehen:

```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
Description=Microsoft ODBC Driver 13 for SQL Server
Driver=/opt/microsoft/msodbcsql/lib64/libmsodbcsql-13.1.so.3.0
UsageCount=1
CPTimeout=120
```

Wenn `Pooling` Sie `No` in der Datei "Odbcinst. ini" auf festlegen, zwingt den Treiber, eine neue Verbindung zu erstellen.
```
[ODBC]
Pooling=No
```

## <a name="remarks"></a>Bemerkungen
- Unter Linux oder macOS werden alle Verbindungen in einem Pool zusammengefasst, wenn Pooling in der Datei "Odbcinst. ini" aktiviert ist. Dies bedeutet, dass die ConnectionPooling-Verbindungs Option keine Auswirkung hat. Um das Pooling zu deaktivieren, legen Sie in der Datei "Odbcinst. ini" Pooling = Nein fest, und laden Sie die Treiber erneut
  - unixodbc < = 2.3.4 (Linux und macOS) gibt möglicherweise keine ordnungsgemäßen Diagnoseinformationen zurück, wie z. b. Fehlermeldungen, Warnungen und informative Meldungen.
  - aus diesem Grund können sqlsrv-und PDO_SQLSRV-Treiber möglicherweise lange Daten (z. b. XML, Binary) nicht ordnungsgemäß als Zeichen folgen abrufen. Lange Daten können als Datenströme als Problem Umgehung abgerufen werden. Weitere Informationen finden Sie im folgenden Beispiel für sqlsrv.

```
<?php
$connectionInfo = array("Database"=>"test", "UID"=>"username", "PWD"=>"password");

$conn1 = sqlsrv_connect("servername", $connectionInfo);

$longSample = str_repeat("a", 8500);
$xml1 = 
'<ParentXMLTag>
  <ChildTag01>'.$longSample.'</ChildTag01>
</ParentXMLTag>';

// Create table and insert xml string into it
sqlsrv_query($conn1, "CREATE TABLE xml_table (field xml)");
sqlsrv_query($conn1, "INSERT into xml_table values ('$xml1')");

// retrieve the inserted xml
$column1 = getColumn($conn1);

// return the connection to the pool
sqlsrv_close($conn1);

// This connection is from the pool
$conn2 = sqlsrv_connect("servername", $connectionInfo);
$column2 = getColumn($conn2);

sqlsrv_query($conn2, "DROP TABLE xml_table");
sqlsrv_close($conn2);

function getColumn($conn)
{
    $tsql = "SELECT * from xml_table";
    $stmt = sqlsrv_query($conn, $tsql);
    sqlsrv_fetch($stmt);
    // This might fail in Linux and macOS
    // $column = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR));
    // The workaround is to fetch it as a stream
    $column = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));
    sqlsrv_free_stmt($stmt);
    return ($column);
}
?>
```


## <a name="see-also"></a>Weitere Informationen  
[Gewusst wie: Herstellen einer Verbindung mithilfe der Windows-Authentifizierung](../../connect/php/how-to-connect-using-windows-authentication.md)

[Gewusst wie: Herstellen einer Verbindung mithilfe der SQL Server-Authentifizierung](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  
