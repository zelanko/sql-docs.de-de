---
title: sqlsrv_fetch | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_fetch
apitype: NA
helpviewer_keywords:
- sqlsrv_fetch
- API Reference, sqlsrv_fetch
- retrieving data, as a single field
ms.assetid: a5a640a1-6e7d-452e-8b66-850a4dc2ce89
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 32b095c37f6a0b039e0836da4508ed8cbfe5fd3b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015022"
---
# <a name="sqlsrv_fetch"></a>sqlsrv_fetch
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Macht die nächste Zeile eines Resultsets zum Lesen verfügbar. Verwenden Sie [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md), um Felder einer Zeile zu lesen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_fetch( resource $stmt[, row[, ]offset])  
```  
  
#### <a name="parameters"></a>Parameter  
*$stmt*: Hierbei handelt es sich um eine Anweisungsressource, die einer ausgeführten Anweisung entspricht.  
  
> [!NOTE]  
> Eine Anweisung muss ausgeführt werden, bevor Ergebnisse abgerufen werden können. Informationen zur Ausführung einer Anweisung finden Sie unter [sqlsrv_query](../../connect/php/sqlsrv-query.md) und [sqlsrv_execute](../../connect/php/sqlsrv-execute.md).  
  
*row* [OPTIONAL]: Einer der folgenden Werte, der die Zeile angibt, auf die in einem Resultset zugegriffen werden soll, das einen scrollfähigen Cursor verwendet:  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
Weitere Informationen zu diesen Werten finden Sie unter [Festlegen eines Cursortyps und Zeilenauswahl](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).  
  
*offset* [OPTIONAL]: Dieser Wert wird zusammen mit „SQLSRV_SCROLL_ABSOLUTE“ und „SQLSRV_SCROLL_RELATIVE“ verwendet, um die abzurufende Zeile anzugeben. Der erste Datensatz im Resultset ist „0“.  
  
## <a name="return-value"></a>Rückgabewert  
Wenn die nächste Zeile des Resultsets erfolgreich abgerufen wurde, wird **true** zurückgegeben. Wenn keine weiteren Ergebnisse im Resultset vorhanden sind, wird **NULL** zurückgegeben. Wenn ein Fehler aufgetreten ist, wird **false** zurückgegeben.  
  
## <a name="example"></a>Beispiel  
Im folgenden Beispiel wird **sqlsrv_fetch** verwendet, um eine Zeile von Daten abzurufen, die eine Produktprüfung und den Namen des Bearbeiters enthält. Zum Abrufen von Daten aus dem Resultset wird [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) verwendet. Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up and execute the query. Note that both ReviewerName and  
Comments are of SQL Server type nvarchar. */  
$tsql = "SELECT ReviewerName, Comments   
         FROM Production.ProductReview  
         WHERE ProductReviewID=1";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Make the first row of the result set available for reading. */  
if( sqlsrv_fetch( $stmt ) === false)  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Note: Fields must be accessed in order.  
Get the first field of the row. Note that no return type is  
specified. Data will be returned as a string, the default for  
a field of type nvarchar.*/  
$name = sqlsrv_get_field( $stmt, 0);  
echo "$name: ";  
  
/*Get the second field of the row as a stream.  
Because the default return type for a nvarchar field is a  
string, the return type must be specified as a stream. */  
$stream = sqlsrv_get_field( $stmt, 1,   
                            SQLSRV_PHPTYPE_STREAM( SQLSRV_ENC_CHAR));  
while( !feof( $stream ))  
{   
    $str = fread( $stream, 10000);  
    echo $str;  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Abrufen von Daten](../../connect/php/retrieving-data.md)  

[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  
