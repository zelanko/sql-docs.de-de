---
title: 'Gewusst wie: Abrufen von Eingabe-/Ausgabeparametern mit dem SQLSRV-Treiber'
description: In diesem Thema wird beschrieben, wie Eingabe- und Ausgabeparameter mithilfe von gespeicherten Prozeduren und dem Microsoft SQLSRV-Treiber für PHP für SQL Server abgerufen werden können.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedure support
ms.assetid: 9a7c5f60-67f9-4968-a3a8-c256ee481da2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ce35c6c0b3025a328c71de657fd1e89358379be
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680685"
---
# <a name="how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver"></a>Gewusst wie: Abrufen von Eingabe- und Ausgabeparametern mit dem SQLSRV-Treiber
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Thema wird veranschaulicht, wie der SQLSRV-Treiber verwendet wird, um eine gespeicherte Prozedur aufzurufen, in der ein Parameter als Eingabe-/Ausgabeparameter definiert wurde, und wie die Ergebnisse abgerufen werden. Beim Abrufen eines Ausgabe- oder Eingabe-/Ausgabeparameters müssen alle von der gespeicherten Prozedur zurückgegebenen Ergebnisse verarbeitet werden, bevor auf den Wert des zurückgegebenen Parameters zugegriffen werden kann.  
  
> [!NOTE]  
>  Variablen, die auf **NULL**, **DateTime**oder Streamtypen aktualisiert oder initialisiert werden, können nicht als Ausgabeparameter verwendet werden.  
  
## <a name="example-1"></a>Beispiel 1
Im folgenden Beispiel wird eine gespeicherte Prozedur aufgerufen, die genommene Urlaubsstunden von den verfügbaren Urlaubsstunden eines bestimmten Mitarbeiters subtrahiert. Die Variable, die die genommenen Urlaubsstunden darstellt, *$vacationHrs*, wird an die gespeicherte Prozedur als Eingabeparameter übergeben. Nach der Aktualisierung der verfügbaren Urlaubsstunden verwendet die gespeicherte Prozedur den gleichen Parameter, um die Anzahl der verbleibenden Urlaubsstunden zurückzugeben.  
  
> [!NOTE]  
> Initialisieren von *$vacationHrs* auf 4 setzt den Rückgabetyp „PHPTYPE auf“ „Integer“ zurück. Um Datentypintegrität sicherzustellen, sollten Eingabe-/Ausgabeparameter vor dem Aufruf der gespeicherten Prozedur initialisiert oder der gewünschte Typ für PHPTYPE angegeben werden. Informationen zum Angeben des PHPTYPE finden Sie unter [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
Da die gespeicherte Prozedur zwei Ergebnisse zurückgibt, muss [sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md) aufgerufen werden, nachdem die gespeicherte Prozedur ausgeführt wurde, um den Wert des Ausgabeparameters verfügbar zu machen. Nach dem Aufruf von **sqlsrv_next_result** enthält $*vacationHrs* den Wert des Ausgabeparameters, der von der gespeicherten Prozedur zurückgegeben wird.  
  
> [!NOTE]  
> Die Verwendung kanonischer Syntax stellt die empfohlene Vorgehensweise für das Abrufen gespeicherter Prozeduren dar. Weitere Informationen zur kanonischen Syntax finden Sie unter [Aufrufen einer gespeicherten Prozedur](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md).  
  
Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
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
  
/* Drop the stored procedure if it already exists. */  
$tsql_dropSP = "IF OBJECT_ID('SubtractVacationHours', 'P') IS NOT NULL  
                DROP PROCEDURE SubtractVacationHours";  
$stmt1 = sqlsrv_query( $conn, $tsql_dropSP);  
if( $stmt1 === false )  
{  
     echo "Error in executing statement 1.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Create the stored procedure. */  
$tsql_createSP = "CREATE PROCEDURE SubtractVacationHours  
                        @EmployeeID int,  
                        @VacationHrs smallint OUTPUT  
                  AS  
                  UPDATE HumanResources.Employee  
                  SET VacationHours = VacationHours - @VacationHrs  
                  WHERE EmployeeID = @EmployeeID;  
                  SET @VacationHrs = (SELECT VacationHours  
                                      FROM HumanResources.Employee  
                                      WHERE EmployeeID = @EmployeeID)";  
  
$stmt2 = sqlsrv_query( $conn, $tsql_createSP);  
if( $stmt2 === false )  
{  
     echo "Error in executing statement 2.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*--------- The next few steps call the stored procedure. ---------*/  
  
/* Define the Transact-SQL query. Use question marks (?) in place of  
the parameters to be passed to the stored procedure */  
$tsql_callSP = "{call SubtractVacationHours( ?, ?)}";  
  
/* Define the parameter array. By default, the first parameter is an  
INPUT parameter. The second parameter is specified as an INOUT  
parameter. Initializing $vacationHrs to 8 sets the returned PHPTYPE to  
integer. To ensure data type integrity, output parameters should be  
initialized before calling the stored procedure, or the desired  
PHPTYPE should be specified in the $params array.*/  
  
$employeeId = 4;  
$vacationHrs = 8;  
$params = array(   
                 array($employeeId, SQLSRV_PARAM_IN),  
                 array(&$vacationHrs, SQLSRV_PARAM_INOUT)  
               );  
  
/* Execute the query. */  
$stmt3 = sqlsrv_query( $conn, $tsql_callSP, $params);  
if( $stmt3 === false )  
{  
     echo "Error in executing statement 3.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Display the value of the output parameter $vacationHrs. */  
sqlsrv_next_result($stmt3);  
echo "Remaining vacation hours: ".$vacationHrs;  
  
/*Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_free_stmt( $stmt3);  
sqlsrv_close( $conn);  
?>  
```  

> [!NOTE]
> Wenn beim Binden eines Eingabe-/Ausgabeparameters an einen bigint-Typ der Wert außerhalb des Bereichs einer [ganzen Zahl](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md) liegt, müssen Sie SQLSRV_SQLTYPE_BIGINT als SQL-Feldtyp angeben. Andernfalls kann dies zu einer Ausnahme des Typs „Wert außerhalb des gültigen Bereichs“ führen.

## <a name="example-2"></a>Beispiel 2
In diesem Codebeispiel wird das Binden eines großen bigint-Werts als Eingabe-/Ausgabeparameter veranschaulicht.  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"testDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Assume the stored procedure spTestProcedure exists, which retrieves a bigint value of some large number
// e.g. 9223372036854
$bigintOut = 0;
$outSql = "{CALL spTestProcedure (?)}";
$stmt = sqlsrv_prepare($conn, $outSql, array(array(&$bigintOut, SQLSRV_PARAM_INOUT, null, SQLSRV_SQLTYPE_BIGINT)));
sqlsrv_execute($stmt);
echo "$bigintOut\n";   // Expect 9223372036854

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```

## <a name="see-also"></a>Weitere Informationen  
[Vorgehensweise: Angeben der Parameterrichtung mit dem SQLSRV-Treiber](../../connect/php/how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)

[Vorgehensweise: Abrufen von Eingabe-/Ausgabeparametern mit dem SQLSRV-Treiber](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)

[Abrufen von Daten](../../connect/php/retrieving-data.md)  
  
