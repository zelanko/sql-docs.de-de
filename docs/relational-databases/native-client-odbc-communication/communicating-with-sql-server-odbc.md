---
title: Kommunikation mit SQL Server (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ce03a5f15e03193d708f30377996cca796eeeaa1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73785002"
---
# <a name="communicating-with-sql-server-odbc"></a>Kommunikation mit SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Damit eine ODBC-Anwendung mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kommunizieren kann, muss Sie Umgebungs-und Verbindungs Handles zuordnen und eine Verbindung mit der Datenquelle herstellen. Nach dem Herstellen einer Verbindung kann die Anwendung Abfragen an den Server senden und Resultsets verarbeiten. Wenn die Anwendung die Datenquelle nicht mehr benötigt, wird die Verbindung mit der Datenquelle getrennt und das Verbindungshandle freigegeben. Wenn die Anwendung alle Verbindungshandles freigegeben hat, wird das Umgebungshandle freigegeben.  
  
 Eine Anwendung kann mit beliebig vielen Datenquellen eine Verbindung herstellen. Die Anwendung kann eine Kombination aus Treibern und Datenquellen, denselben Treiber und eine Kombination aus Datenquellen oder auch denselben Treiber und mehrere Verbindungen mit derselben Datenquelle verwenden.  
  
 Sie können native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client-ODBC-Beispiele auf der Seite [SQL Server Downloads](https://go.microsoft.com/fwlink/?LinkId=62796) auf MSDN herunterladen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Zuordnen eines Umgebungshandles](../../relational-databases/native-client-odbc-communication/allocating-an-environment-handle.md)  
  
-   [Zuordnen eines Verbindungshandles](../../relational-databases/native-client-odbc-communication/allocating-a-connection-handle.md)  
  
-   [SQL Server Native Client ODBC-Datenquellen](../../relational-databases/native-client-odbc-communication/sql-server-native-client-odbc-data-sources.md)  
  
-   [Herstellen einer Verbindung mit einer Datenquelle &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-communication/connecting-to-a-data-source-odbc.md)  
  
-   [Trennen der Verbindung mit einer Datenquelle](../../relational-databases/native-client-odbc-communication/disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)  
  
  
