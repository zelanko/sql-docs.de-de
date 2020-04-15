---
title: ODBC Service Provider Interface (SPI)-Referenz | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e9739abd13bf2c4bed1b1b3a31c18c683594705a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298908"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>ODBC-Dienstanbieterschnittstelle – Referenz
Traditionell definierte ODBC eine API (Application Programming Interface). Die Funktionen in der API können von Anwendungen aufgerufen werden und sollten sowohl im Treiber-Manager als auch im Treiber implementiert werden.  
  
 Mit der Treiber-basierten Verbindungspooling-Funktion führt ODBC die Service Provider Interface (SPI) ein. Die Funktionen im SPI werden für die Kommunikation zwischen Treiber-Manager und Treiber verwendet. SPI-Funktionen werden vom Treiber implementiert; Der Treiber-Manager macht SPI-Funktionen nicht für Anwendungen verfügbar. Anwendungen sollten diese Funktionen nicht direkt aufrufen.  
  
 Fügen Sie sqlspi.h für die ODBC-Treiberentwicklung ein.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [SQLPoolConnect](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [SQLSetConnectInfo](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [SQLSetDriverConnectInfo](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Entwickeln der Verbindungspool-Bewusstseinsbildung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Verbindungspooling des Treiber-Managers](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
