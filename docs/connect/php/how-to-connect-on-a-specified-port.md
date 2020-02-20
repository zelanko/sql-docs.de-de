---
title: 'Gewusst wie: Verbinden über einen angegebenen Port | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: af055a73904bb8feec92fb2afe93df064a09ab23
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015052"
---
# <a name="how-to-connect-on-a-specified-port"></a>Gewusst wie: Verbinden über einen angegebenen Port
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Thema wird beschrieben, wie über einen angegebenen Port mit der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]eine Verbindung zu SQL Server hergestellt wird.  
  
### <a name="to-connect-on-a-specified-port"></a>Verbinden über einen angegebenen Port  
  
1.  Stellen Sie sicher, dass der Port, auf den der Server konfiguriert ist, Verbindungen akzeptiert. Weitere Informationen zum Konfigurieren eines Servers, sodass er Verbindungen auf einem angegebenen Port annimmt, finden Sie unter [ Konfigurieren eines Servers für das Überwachen eines bestimmten TCP-Ports](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
2.  Fügen Sie den gewünschten Port dem *$serverName*-Parameter der [sqlsrv_connect](../../connect/php/sqlsrv-connect.md)-Funktion hinzu. Trennen Sie den Servernamen und den Port durch ein Komma. Beispielsweise verwenden die folgenden Codezeilen die SQLSRV-Treiber, um zu veranschaulichen, wie die Verbindung mit einem Server namens *myServer* über Port 1521 hergestellt wird:  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    Die folgenden Codezeilen verwenden den PDO_SQLSRV-Treiber, um zu veranschaulichen, wie die Verbindung mit einem Server namens *myServer* über Port 1521 hergestellt wird:  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
[Verbinden mit dem Server](../../connect/php/connecting-to-the-server.md)

[Programmierhandbuch für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Getting Started with the Microsoft Drivers for PHP for SQL Server (Erste Schritte mit dem Microsoft-Treiber für PHP für SQL Server)](../../connect/php/getting-started-with-the-php-sql-driver.md)

[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[Referenz zum Treiber PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
