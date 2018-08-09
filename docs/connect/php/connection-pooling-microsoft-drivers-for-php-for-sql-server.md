---
title: Verbindungspooling (Microsoft-Treiber für PHP für SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02db1d891f02dce9912d4cdcf78ca0166eab9c32
ms.sourcegitcommit: ef7f2540ba731cc6a648005f2773d759df5c6405
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39415479"
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>Verbindungspooling (Microsoft Drivers for PHP for SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Folgende wichtige Punkte sollten Sie für das Verbindungspooling in [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]beachten:  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] verwendet ODBC-Verbindungspooling.  
  
-   Das Verbindungspooling ist in Windows standardmäßig aktiviert. In Linux und MacOS Verbindungen werden in einem Pool zusammengefasste nur dann, wenn Verbindungspooling für ODBC aktiviert ist (siehe [aktivieren/deaktivieren Verbindungspooling](#enablingdisabling-connection-pooling)). Wenn Verbindungspooling aktiviert ist, und Sie mit einem Server verbinden, versucht der Treiber eine gepoolte Verbindung verwendet wird, bevor sie eine neue Ressourcengruppe erstellt. Falls im Pool keine äquivalente Verbindung gefunden wird, wird eine neue Verbindung erstellt und dem Pool hinzugefügt. Basierend auf einem Vergleich der Verbindungszeichenfolgen, ermittelt der Treiber  ob die Verbindungen äquivalent sind.  
  
-   Wenn eine Verbindung aus dem Pool verwendet wird, wird der Verbindungsstatus zurückgesetzt.  
  
-   Das Schließen der Verbindung gibt die Verbindung an den Pool zurück.  
  
Weitere Informationen zum Verbindungspooling finden Sie unter [Treiber-Manager-Verbindungspooling](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="enablingdisabling-connection-pooling"></a>Aktivieren/Deaktivieren von Verbindungspooling
### <a name="windows"></a>Windows
Sie können den Treiber zwingen, eine neue Verbindung zu erstellen (anstatt nach einer äquivalenten Verbindung im Verbindungspool zu suchen), indem Sie den Wert des *ConnectionPooling*-Attributs in der Verbindungszeichenfolge auf **false** (oder 0) festlegen.  
  
Falls das *ConnectionPooling*-Attribut aus der Verbindungszeichenfolge weggelassen oder auf **true** (oder 1) festgelegt wird, erstellt der Treiber nur dann eine neue Verbindung, wenn es keine äquivalente Verbindung im Verbindungspool gibt.  
  
Weitere Informationen zu weiteren Verbindungsattributen finden Sie unter [Connection Options](../../connect/php/connection-options.md).  
### <a name="linux-and-macos"></a>Linux und macOS
Die *ConnectionPooling* Attribut kann nicht zum Aktivieren/Deaktivieren Sie die Verbindungs-pooling verwendet werden. 

Verbindungspooling kann aktiviert/deaktiviert werden durch Bearbeiten der Konfigurationsdatei "Odbcinst.ini". Der Treiber sollte neu geladen werden, damit die Änderungen wirksam werden.

Festlegen von `Pooling` zu `Yes` und eine Positive `CPTimeout` Wert in der Datei "Odbcinst.ini" ermöglicht Verbindungspooling. 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
  
Die Datei "odbcinst.ini" sollte es sich mindestens um etwa wie im folgenden Beispiel aussehen:

```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
Description=Microsoft ODBC Driver 13 for SQL Server
Driver=/opt/microsoft/msodbcsql/lib64/libmsodbcsql-13.1.so.3.0
UsageCount=1
CPTimeout=120
```

Festlegen von `Pooling` zu `No` in der "Odbcinst.ini"-Datei zwingt den Treiber aus, um eine neue Verbindung zu erstellen.
```
[ODBC]
Pooling=No
```

## <a name="remarks"></a>Remarks
- Unter Linux oder MacOS werden alle Verbindungen gepoolt werden sollen, wenn in der Datei "Odbcinst.ini" aktiviert ist. Dies bedeutet, dass die Verbindungsoption ConnectionPooling hat keine Auswirkungen. Legen Sie zum Deaktivieren des Poolings, Pooling = No in der Datei "Odbcinst.ini", und Laden Sie die Treiber erneut.
  - UnixODBC < = 2.3.4 (Linux und MacOS) möglicherweise nicht ordnungsgemäße Diagnoseinformationen, z. B. Fehlermeldungen, Warnungen und informativen Meldungen zurück
  - aus diesem Grund SQLSRV und PDO_SQLSRV-Treiber ordnungsgemäß Abrufen von long-Daten (z. B. Xml, binär) als Zeichenfolgen möglicherweise nicht. Long-Daten können als Streams als problemumgehung abgerufen werden. SQLSRV finden Sie im Beispiel unten.

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


## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Gewusst wie: Herstellen einer Verbindung mithilfe der Windows-Authentifizierung](../../connect/php/how-to-connect-using-windows-authentication.md)

[Gewusst wie: Herstellen einer Verbindung mithilfe der SQL Server-Authentifizierung](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  
