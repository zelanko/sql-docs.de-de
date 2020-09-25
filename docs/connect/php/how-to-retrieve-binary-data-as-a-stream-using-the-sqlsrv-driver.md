---
title: Abrufen von Binärdaten als Stream mithilfe des SQLSRV-Treibers
description: In diesem Thema wird beschrieben, wie Binärdaten als Datenstrom abgerufen werden können, wenn der Microsoft SQLSRV-Treiber für PHP für SQL Server verwendet wird.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, as a binary stream
- streaming data
ms.assetid: cd8d6382-abe6-48ee-9d10-4e6c52c0cb9a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d509eaf083cf7a16e83506ecf54d99daa8883a62
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680625"
---
# <a name="how-to-retrieve-binary-data-as-a-stream-using-the-sqlsrv-driver"></a>Vorgehensweise: Abrufen von Binärdaten als Stream mithilfe des SQLSRV-Treibers
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Das Abrufen von Daten als Stream ist nur im SQLSRV-Treiber von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] und nicht im PDO_SQLSRV-Treiber verfügbar.  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] nutzt PHP-Streams zum Abrufen großer Binärdatenmengen vom Server. Dieses Thema veranschaulicht, wie Binärdaten als Stream abgerufen werden.  
  
Verwenden der Streams zum Abrufen von Binärdaten, z. B. Bildern, verzichtet auf die Verwendung großer Mengen Skriptspeicher, indem nur Datenblöcke und nicht ganze Objekte in den Skriptspeicher geladen werden.  
  
## <a name="example"></a>Beispiel  
Im folgenden Beispiel werden Binärdaten, z. B. ein Bild, aus der *Production.ProductPhoto* -Tabelle der AdventureWorks-Datenbank abgerufen. Das Bild wird als Stream abgerufen und im Browser angezeigt.  
  
Das Abrufen von Bilddaten als Stream erfolgt mithilfe von [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) und [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) mit einem binären Stream als Rückgabetyp. Der Rückgabetyp wird unter Verwendung der Konstanten **SQLSRV_PHPTYPE_STREAM** angegeben. Informationen zu **sqlsrv**-Konstanten finden Sie unter [Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Wenn das Beispiel über den Browser ausgeführt wird, werden alle Ausgaben im Browser geschrieben.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "SELECT LargePhoto   
         FROM Production.ProductPhoto   
         WHERE ProductPhotoID = ?";  
  
/* Set the parameter values and put them in an array. */  
$productPhotoID = 70;  
$params = array( $productPhotoID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data.  
The return data is retrieved as a binary stream. */  
if ( sqlsrv_fetch( $stmt ) )  
{  
   $image = sqlsrv_get_field( $stmt, 0,   
                      SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_BINARY));  
   header("Content-Type: image/jpg");  
   fpassthru($image);  
}  
else  
{  
     echo "Error in retrieving data.</br>";  
     die(print_r( sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Die Angabe des Rückgabetyps im Beispiel veranschaulicht, wie der PHP-Rückgabetyp als binärer Stream angegeben wird. Technisch gesehen ist dieser im Beispiel nicht erforderlich, weil das *LargePhoto*-Feld den SQL Server-Typ „varbinary(max)“ aufweist und dieser daher standardmäßig als binärer Stream zurückgegeben wird. Informationen zu PHP-Datentypen finden Sie unter [Default PHP Data Types](../../connect/php/default-php-data-types.md). Weitere Informationen zum Angeben von PHP-Rückgabetypen finden Sie unter [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Abrufen von Daten](../../connect/php/retrieving-data.md)

[Abrufen von Daten als Stream mit dem SQLSRV-Treiber](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  
