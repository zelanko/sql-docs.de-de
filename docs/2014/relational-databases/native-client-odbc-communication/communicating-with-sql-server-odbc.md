---
title: Kommunikation mit SQLServer (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a701075067b89e40d8dfe44bf9dccfb3240960f1
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414379"
---
# <a name="communicating-with-sql-server-odbc"></a>Kommunikation mit SQL Server (ODBC)
  Für eine ODBC-Anwendung für die Kommunikation mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], muss es Umgebung zuordnen und verarbeitet und eine Verbindung mit der Datenquelle herstellen. Nach dem Herstellen einer Verbindung kann die Anwendung Abfragen an den Server senden und Resultsets verarbeiten. Wenn die Anwendung die Datenquelle nicht mehr benötigt, wird die Verbindung mit der Datenquelle getrennt und das Verbindungshandle freigegeben. Wenn die Anwendung alle Verbindungshandles freigegeben hat, wird das Umgebungshandle freigegeben.  
  
 Eine Anwendung kann mit beliebig vielen Datenquellen eine Verbindung herstellen. Die Anwendung kann eine Kombination aus Treibern und Datenquellen, denselben Treiber und eine Kombination aus Datenquellen oder auch denselben Treiber und mehrere Verbindungen mit derselben Datenquelle verwenden.  
  
 Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Beispiele von der [SQL Server-Downloads](http://go.microsoft.com/fwlink/?LinkId=62796) -Seite auf MSDN.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Zuordnen eines Umgebungshandles](allocating-an-environment-handle.md)  
  
-   [Zuordnen eines Verbindungshandles](allocating-a-connection-handle.md)  
  
-   [SQL Server Native Client ODBC-Datenquellen](../../integration-services/connection-manager/data-sources.md)  
  
-   [Herstellen einer Verbindung mit einer Datenquelle &#40;ODBC&#41;](connecting-to-a-data-source-odbc.md)  
  
-   [Trennen der Verbindung mit einer Datenquelle](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)  
  
  
