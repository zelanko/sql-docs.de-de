---
title: 'Gewusst wie: Deaktivieren von Multiple Active Resultsets (MARS) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- multiple active result sets, disabling
- MARS, disabling
ms.assetid: 1912ad05-d0a4-40ff-8888-0d85bb36a807
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a438c1d077de0559a950458755a68ac08a1de089
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66796116"
---
# <a name="how-to-disable-multiple-active-resultsets-mars"></a>Vorgehensweise: Deaktivieren von Multiple Active Resultsets (MARS)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Wenn Sie eine Verbindung mit einer SQL Server-Datenquelle herstellen müssen, die Multiple Active Resultsets (MARS) nicht ermöglicht, können Sie die Verbindungsoption „MultipleActiveResultSets“ verwenden, um MARS zu deaktivieren oder zu aktivieren.  
  
## <a name="procedure"></a>Verfahren  
  
#### <a name="to-disable-mars-support"></a>Gehen Sie wie folgt vor, um die MARS-Unterstützung zu deaktivieren:  
  
-   Verwenden Sie die folgende Verbindungsoption:  
  
    ```  
    'MultipleActiveResultSets'=>false  
    ```  
  
    Wenn Ihre Anwendung versucht, eine Abfrage über eine Verbindung auszuführen, die ein geöffnetes aktives Resultset enthält, gibt der zweite Abfrageversuch die folgende Fehlerinformation zurück:  
  
    Die Verbindung kann diesen Vorgang nicht verarbeiten, da für eine Anweisung noch Ergebnisse ausstehen.  Rufen Sie entweder alle Ergebnisse auf, brechen Sie die Anweisung ab oder geben Sie sie frei, um die Verbindung anderen Abfragen zur Verfügung zu stellen. Weitere Informationen über die Verbindungsoption MultipleActiveResultSets finden Sie unter [Connection Options](../../connect/php/connection-options.md).  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel zeigt die Vorgehensweise zum Deaktivieren der MARS-Unterstützung, unter Verwendung des SQLSRV-Treibers der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'MultipleActiveResultSets'=> false);  
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
Das folgende Beispiel zeigt die Vorgehensweise zum Deaktivieren der MARS-Unterstützung, unter Verwendung des PDO_SQLSRV-Treibers der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
```  
<?php  
// Connect to the local server using Windows Authentication and AdventureWorks database  
$serverName = "(local)";   
$database = "AdventureWorks";  
  
try {  
   $conn = new PDO(" sqlsrv:server=$serverName ; Database=$database ; MultipleActiveResultSets=false ", NULL, NULL);   
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );   
}  
  
catch( PDOException $e ) {  
   die( "Error connecting to SQL Server" );   
}  
  
$conn = null;   
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Verbinden mit dem Server](../../connect/php/connecting-to-the-server.md)  
  
