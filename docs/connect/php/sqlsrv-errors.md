---
title: sqlsrv_errors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_errors
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_errors
- sqlsrv_errors
- errors and warnings
ms.assetid: d1fcffec-f34f-46de-9a0e-343f3b5dbae2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08879880e93307a496969b79c3aa05144f7aef62
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015064"
---
# <a name="sqlsrv_errors"></a>sqlsrv_errors
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt erweiterte Informationen über Fehler und/oder Warnungen für den letzten ausgeführten **sqlsrv**-Vorgang zurück.  
  
Die **sqlsrv_errors**-Funktion kann eine Information über Fehler und/oder Warnungen zurückgeben, indem sie diese mit einem der Parameterwerte aufruft, die unten im Abschnitt „Parameter“ angegeben sind.  
  
Standardmäßig werden Warnungen, die bei einem Aufruf einer **sqlsrv** -Funktion generiert werden, als Fehler behandelt. Wenn eine Warnung bei einem Aufruf einer **sqlsrv** -Funktion auftritt, gibt die Funktion „false“ zurück. Jedoch werden Warnungen, die den SQLSTATE-Werten 01000, 01001, 01003 und 01S02 entsprechen, nie als Fehler behandelt.  
  
Die folgende Codezeile deaktiviert das oben genannte Verhalten. Eine Warnung, die durch einen Aufruf einer **sqlsrv** -Funktion generiert wurde, führt nicht dazu, dass die Funktion „false“ zurückgibt:  
  
```  
sqlsrv_configure("WarningsReturnAsErrors", 0);  
```  
  
Die folgende Codezeile aktiviert wieder das Standardverhalten; Warnungen (mit Ausnahmen wie oben beschrieben) werden als Fehler behandelt:  
  
```  
sqlsrv_configure("WarningsReturnAsErrors", 1);  
```  
  
Unabhängig von der Einstellung können Warnungen nur durch Aufrufen von **sqlsrv_errors** abgerufen werden, entweder mit dem Parameterwert **SQLSRV_ERR_ALL** oder **SQLSRV_ERR_WARNINGS** (Einzelheiten finden Sie im Abschnitt „Parameter“).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_errors( [int $errorsAndOrWarnings] )  
```  
  
#### <a name="parameters"></a>Parameter  
*$errorsAndOrWarnings*[OPTIONAL]: Hierbei handelt es sich um eine vordefinierte Konstante. Dieser Parameter kann einen der in der folgenden Tabelle aufgeführten Werte annehmen:  
  
|value|BESCHREIBUNG|  
|---------|---------------|  
|SQLSRV_ERR_ALL|Fehler und Warnungen, die beim letzten **sqlsrv** -Funktionsaufruf generiert wurden, werden zurückgegeben.|  
|SQLSRV_ERR_ERRORS|Fehler und Warnungen aus dem letzten **sqlsrv** -Funktionsaufruf werden zurückgegeben.|  
|SQLSRV_ERR_WARNINGS|Warnungen aus dem letzten **sqlsrv** -Funktionsaufruf werden zurückgegeben.|  
  
Wenn kein Parameterwert angegeben wird, werden Fehler und Warnungen zurückgegeben, die durch den letzten **sqlsrv** -Funktionsaufruf generiert wurden.  
  
## <a name="return-value"></a>Rückgabewert  
Ein **Array** von Arrays oder **NULL**. Jedes **Array** im zurückgegebenen **Array** enthält drei Schlüssel-Wert-Paare. In der folgenden Tabelle wird jeder Schlüssel und dessen Beschreibung aufgelistet.  
  
|Key|Beschreibung|  
|-------|---------------|  
|SQLSTATE|Für Fehler, die aus dem ODBC-Treiber stammen, wird von ODBC der Wert SQLSTATE zurückgegeben Weitere Informationen zu SQLSTATE-Werten für ODBC finden Sie unter [ODBC-Fehlercodes](../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).<br /><br />Für Fehler, die aus den [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]stammen, ein SQLSTATE von IMSSP<br /><br />Für Warnungen, die aus den [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]stammen, ein SQLSTATE von 01SSP|  
|code|Für Fehler, die vom SQL Server stammen, den systemeigenen SQL Server-Fehlercode<br /><br />Für Fehler, die aus dem ODBC-Treiber stammen, wird von ODBC der Fehlercode zurückgegeben<br /><br />Für Fehler, die aus den [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]oder dem [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] -Fehlercode stammen Weitere Informationen finden Sie unter [Handling Errors and Warnings](../../connect/php/handling-errors-and-warnings.md).|  
|message|Eine Beschreibung des Fehlers.|  
  
Auf die Arraywerte kann auch mit den numerischen Schlüsseln 0, 1 und 2 zugegriffen werden. Wenn keine Fehler oder Warnungen auftreten, wird **NULL** zurückgegeben.  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel zeigt auftretende Fehler, die während einer fehlgeschlagene Anweisungsausführung entstehen. (Bei der Anweisung tritt ein Fehler auf, da **InvalidColumName** kein gültiger Spaltenname in der angegebenen Tabelle ist.) Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
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
  
/* Set up a query to select an invalid column name. */  
$tsql = "SELECT InvalidColumnName FROM Sales.SalesOrderDetail";  
  
/* Attempt execution. */  
/* Execution will fail because of the invalid column name. */  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
      if( ($errors = sqlsrv_errors() ) != null)  
      {  
         foreach( $errors as $error)  
         {  
            echo "SQLSTATE: ".$error[ 'SQLSTATE']."\n";  
            echo "code: ".$error[ 'code']."\n";  
            echo "message: ".$error[ 'message']."\n";  
         }  
      }  
}  
  
/* Free connection resources */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  
