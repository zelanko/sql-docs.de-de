---
title: zu Sqlsrv_server_info | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_server_info
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_server_info
- sqlsrv_server_info
ms.assetid: ef6fe2b7-d267-4379-b948-5626c4684367
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 878ea8dde5e6cbccf4d87e4a3b4b98fbf06f557b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37983605"
---
# <a name="sqlsrvserverinfo"></a>sqlsrv_server_info
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt Informationen über den Server zurück. Eine Verbindung muss hergestellt werden, bevor Sie diese Funktion aufrufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_server_info( resource $conn)  
```  
  
#### <a name="parameters"></a>Parameter  
*$conn*: Die Verbindungsressource, durch die der Client und der Server verbunden sind.  
  
## <a name="return-value"></a>Rückgabewert  
Ein assoziatives Array mit den folgenden Schlüsseln:  
  
|Key|und Beschreibung|  
|-------|---------------|  
|CurrentDatabase|Die Datenbank, die derzeit das Ziel darstellt.|  
|SQLServerVersion|Die Version von SQL Server.|  
|SQLServerName|Der Name des Servers.|  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel schreibt Server-Informationen an die Konsole, wenn das Beispiel über die Befehlszeile ausgeführt wird.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
$server_info = sqlsrv_server_info( $conn);  
if( $server_info )  
{  
      foreach( $server_info as $key => $value)  
      {  
             echo $key.": ".$value."\n";  
      }  
}  
else  
{  
      echo "Error in retrieving server info.\n";  
      die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  
