---
title: 'Gewusst wie: Deaktivieren mehrerer aktiver Resultsets'
description: Erfahren Sie, wie Sie die Unterstützung mehrerer aktiver Resultsets deaktivieren, wenn Sie die Microsoft-Treiber für PHP für SQL Server verwenden.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- multiple active result sets, disabling
- MARS, disabling
ms.assetid: 1912ad05-d0a4-40ff-8888-0d85bb36a807
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 11ca08618f0b8d7675e8ec74ec259d4225d44aba
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92080619"
---
# <a name="how-to-disable-multiple-active-resultsets-mars"></a>Vorgehensweise: Deaktivieren von Multiple Active Resultsets (MARS)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Wenn Sie eine Verbindung mit einer SQL Server-Datenquelle herstellen müssen, die Multiple Active Resultsets (MARS) nicht ermöglicht, können Sie die Verbindungsoption „MultipleActiveResultSets“ verwenden, um MARS zu deaktivieren oder zu aktivieren.  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-disable-mars-support"></a>Gehen Sie wie folgt vor, um die MARS-Unterstützung zu deaktivieren:  
  
-   Verwenden Sie die folgende Verbindungsoption:  
  
    ```  
    'MultipleActiveResultSets'=>false  
    ```  
  
    Wenn Ihre Anwendung versucht, eine Abfrage über eine Verbindung auszuführen, die ein geöffnetes aktives Resultset enthält, gibt der zweite Abfrageversuch die folgende Fehlerinformation zurück:  
  
    Die Verbindung kann diesen Vorgang nicht verarbeiten, da für eine Anweisung noch Ergebnisse ausstehen.  Rufen Sie entweder alle Ergebnisse auf, brechen Sie die Anweisung ab oder geben Sie sie frei, um die Verbindung anderen Abfragen zur Verfügung zu stellen. Weitere Informationen über die Verbindungsoption MultipleActiveResultSets finden Sie unter [Connection Options](../../connect/php/connection-options.md).  
  
## <a name="sqlsrv-example"></a>SQLSRV-Beispiel  
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
  
## <a name="pdo_sqlsrv-example"></a>PDO_SQLSRV-Beispiel  
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
  
