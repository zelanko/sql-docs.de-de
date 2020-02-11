---
title: Referenz zur ODBC-Dienstanbieter Schnittstelle (SPI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 88053620fa413c50a8faff4cc47cbbe1457249f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073832"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>ODBC-Dienstanbieterschnittstelle – Referenz
In der Regel hat ODBC eine Anwendungsprogrammierschnittstelle (Application Programming Interface, API) definiert. Die Funktionen in der API können von Anwendungen aufgerufen werden, und Sie sollten innerhalb des Treiber-Managers und des Treibers implementiert werden.  
  
 Durch das Hinzufügen des Treiber fähigen Verbindungspooling-Features führt ODBC die Service Provider Interface (SPI) ein. Die Funktionen in der SPI werden für die Kommunikation zwischen dem Treiber-Manager und dem Treiber verwendet. SPI-Funktionen werden vom Treiber implementiert. der Treiber-Manager macht keine SPI-Funktionen für Anwendungen verfügbar. Anwendungen sollten diese Funktionen nicht direkt aufzurufen.  
  
 Fügen Sie sqlspi. h für die ODBC-Treiberentwicklung ein.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Sqlcleanupconnectionpoolid](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [Sqlgetpoolid](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [Sqlpoolconnect](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [Sqlrateconnetction](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [Sqlsetconnectattrfordbcinfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [Sqlsetconnectinfo](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [Sqlsetdriverconnectinfo](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Entwickeln von Verbindungs Pool Informationen in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Verbindungspooling des Treiber-Managers](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
