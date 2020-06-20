---
title: Kommunikation mit SQL Server (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: rothja
ms.author: jroth
ms.openlocfilehash: c41ac2dcce9c5bdbdd351148d16bcaa8f067d22f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021198"
---
# <a name="communicating-with-sql-server-odbc"></a>Kommunikation mit SQL Server (ODBC)
  Damit eine ODBC-Anwendung mit einer Instanz von kommunizieren [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann, muss Sie Umgebungs-und Verbindungs Handles zuordnen und eine Verbindung mit der Datenquelle herstellen. Nach dem Herstellen einer Verbindung kann die Anwendung Abfragen an den Server senden und Resultsets verarbeiten. Wenn die Anwendung die Datenquelle nicht mehr benötigt, wird die Verbindung mit der Datenquelle getrennt und das Verbindungshandle freigegeben. Wenn die Anwendung alle Verbindungshandles freigegeben hat, wird das Umgebungshandle freigegeben.  
  
 Eine Anwendung kann mit beliebig vielen Datenquellen eine Verbindung herstellen. Die Anwendung kann eine Kombination aus Treibern und Datenquellen, denselben Treiber und eine Kombination aus Datenquellen oder auch denselben Treiber und mehrere Verbindungen mit derselben Datenquelle verwenden.  
  
 Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Beispiele auf der Seite [SQL Server Downloads](https://go.microsoft.com/fwlink/?LinkId=62796) auf MSDN herunterladen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Zuordnen eines Umgebungshandles](allocating-an-environment-handle.md)  
  
-   [Zuordnen eines Verbindungshandles](allocating-a-connection-handle.md)  
  
-   [SQL Server Native Client ODBC-Datenquellen](../../integration-services/connection-manager/data-sources.md)  
  
-   [Herstellen einer Verbindung mit einer Datenquelle &#40;ODBC-&#41;](connecting-to-a-data-source-odbc.md)  
  
-   [Trennen der Verbindung mit einer Datenquelle](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC-&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)  
  
  
