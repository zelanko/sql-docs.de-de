---
title: 'Gewusst wie: Angeben von PHP-Datentypen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data types
- streaming data
ms.assetid: fee6e6b8-aad9-496b-84a2-18d2950470a4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ae00c01e962da05015a5132608915fc9d70258f4
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67936399"
---
# <a name="how-to-specify-php-data-types"></a>Gewusst wie: Festlegen von PHP-Datentypen
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Wenn Sie den PDO_SQLSRV-Treiber verwenden, können Sie mittels „PDOStatement::bindColumn“ und „PDOStatement::bindParam“ den PHP-Datentyp festlegen, wenn Sie Daten vom Server abrufen. Weitere Informationen finden Sie unter [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md) und [PDOStatement::bindParam](../../connect/php/pdostatement-bindparam.md) .  
  
Die folgenden Schritten zeigen zusammenfassend, wie PHP-Datentypen beim Abruf vom Server mit dem SQLSRV-Treiber festgelegt werden:  
  
1.  Richten Sie eine Transact-SQL-Abfrage mit [sqlsrv_query](../../connect/php/sqlsrv-query.md) oder der Kombination aus [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)/[sqlsrv_execute](../../connect/php/sqlsrv-execute.md) ein, und führen Sie sie aus.  
  
2.  Stellen Sie eine Datenzeile für das Lesen mit [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)bereit.  
  
3.  Verwenden Sie [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) , um die Felddaten einer ausgegebenen Zeile mit dem gewünschten, im dritten optionalen Parameter festgelegten PHP-Datentyp abzurufen. Falls der optionale dritte Parameter nicht festgelegt ist, werden die Daten laut den PHP-Standarddatentypen zurückgegeben. Informationen zu den PHP-Standarddatentypen finden Sie unter [Default PHP Data Types](../../connect/php/default-php-data-types.md).  
  
    Informationen zu den Konstanten, die zur Festlegung der PHP-Datentypen verwendet werden, finden Sie im PHPTYPEs-Abschnitt von [Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
## <a name="example"></a>Beispiel  
Im folgenden Beispiel werden Zeilen von der *Production.ProductReview* -Tabelle der AdventureWorks-Datenbank abgerufen. In jeder ausgegebenen Zeile wird das *ReviewDate*-Feld als Zeichenfolge und das *Comments*-Feld als Stream abgerufen. Die Streamdateien werden mit der PHP [fpassthru](https://php.net/manual/en/function.fpassthru.php) -Funktion dargestellt.  
  
Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "SELECT ReviewerName,   
                ReviewDate,  
                Rating,   
                Comments   
         FROM Production.ProductReview   
         WHERE ProductID = ?   
         ORDER BY ReviewDate DESC";  
  
/* Set the parameter value. */  
$productID = 709;  
$params = array( $productID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data. The first and third fields are  
retrieved according to their default types, strings. The second field  
is retrieved as a string with 8-bit character encoding. The fourth  
field is retrieved as a stream with 8-bit character encoding.*/  
while ( sqlsrv_fetch( $stmt))  
{  
   echo "Name: ".sqlsrv_get_field( $stmt, 0 )."\n";  
   echo "Date: ".sqlsrv_get_field( $stmt, 1,   
                       SQLSRV_PHPTYPE_STRING( SQLSRV_ENC_CHAR))."\n";  
   echo "Rating: ".sqlsrv_get_field( $stmt, 2 )."\n";  
   echo "Comments: ";  
   $comments = sqlsrv_get_field( $stmt, 3,   
                            SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));  
   fpassthru( $comments);  
   echo "\n";   
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Im Beispiel sorgt der Abruf des zweiten Feldes (*ReviewDate*) als Zeichenfolge für die Millisekunden-Genauigkeit des SQL Server-Datentyps DATETIME. Standardmäßig wird der SQL Server-Datentyp DATETIME als PHP-DateTime-Objekt abgerufen, wobei die Millisekunden-Genauigkeit verloren geht.  
  
Das vierte Feld (*Comments*) wird zu Vorführungszwecken als Stream abgerufen. Standardmäßig wird der SQL Server-Datentyp „nvarchar(3850)“ als eine Zeichenfolge abgerufen. Dies ist für die meisten Situationen akzeptabel.   
  
> [!NOTE]  
> Die [sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md) -Funktion bietet eine Möglichkeit, Feldinformationen inklusive Feldtypinformationen zu erhalten bevor eine Abfrage durchgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
[Abrufen von Daten](../../connect/php/retrieving-data.md)

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)

[Vorgehensweise: Abrufen von Ausgabeparametern mit dem SQLSRV-Treiber](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)

[Vorgehensweise: Abrufen von Eingabe- und Ausgabeparametern mit dem SQLSRV-Treiber](../../connect/php/how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)  
  
