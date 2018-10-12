---
title: Datums- und Uhrzeittypen mittels des SQLSRV-Treibers als Zeichenfolgen abrufen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as strings
ms.assetid: 58a974ea-4daf-4e3b-98ed-9731b9c9250f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29e36f2246556da7a43c3b8335f7a4e3479ae63c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686988"
---
# <a name="how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver"></a>Vorgehensweise: Datums- und Uhrzeittypen mittels des SQLSRV-Treibers als Zeichenfolgen abrufen
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Diese Funktion wurde der Version 1.1 der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] hinzugefügt und ist nur zulässig, wenn der SQLSRV-Treiber für die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]verwendet wird. Es ist ein Fehler die Verbindungsoption „ReturnDatesAsStrings“  mit dem PDO_SQLSRV-Treiber zu verwenden.  
  
Sie können Datums- und Uhrzeittypen(**datetime**, **date**, **time**, **datetime2** und **datetimeoffset**) als Zeichenfolgen abrufen, indem Sie eine Option in der Verbindungszeichenfolge festlegen.  
  
### <a name="to-retrieve-date-and-time-types-as-strings"></a>Datums- und Uhrzeittypen als Zeichenfolgen abrufen  
  
-   Verwenden Sie die folgende Verbindungsoption:  
  
    ```  
    'ReturnDatesAsStrings'=>true  
    ```  
  
    Der Standardwert ist **false**, d. h. dass **datetime**, **Date**, **Time**, **DateTime2**und **DateTimeOffset** -Typen als PHP- **Datetime** -Typen ausgegeben werden.  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel zeigt die Syntax, welche festlegt, dass die Datums- und Uhrzeittypen als Zeichenfolgen abgerufen werden.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings '=> true);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel zeigt, dass Sie verschiedene Datumsangaben als Zeichenfolge abrufen können, sofern Sie beim Abruf UTF-8 spezifizieren. Dies gilt auch, wenn die Verbindung mittels `"ReturnDatesAsStrings" => false` erstellt wurde.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", "ReturnDatesAsStrings" => false);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0, SQLSRV_PHPTYPE_STRING("UTF-8"));  
  
if( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel zeigt, wie Datumsangaben als Zeichenfolgen abgerufen werden können, indem UTF-8 und `"ReturnDatesAsStrings" => true` in der Verbindungszeichenfolge spezifiziert werden.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings'=> true, "CharacterSet" => 'utf-8' );  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel zeigt, wie das Datum als PHP-Typ abgerufen wird. `'ReturnDatesAsStrings'=> false` ist standardmäßig aktiviert.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$date_string = date_format( $date, 'jS, F Y' );  
echo "Date = $date_string\n";  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Abrufen von Daten](../../connect/php/retrieving-data.md)  
  
