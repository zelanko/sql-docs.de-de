---
title: Kommunikation mit SQL Server (ODBC) | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a7d903dfdc0e25d3dc305b78f716a7146ce25c1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307787"
---
# <a name="communicating-with-sql-server-odbc"></a>Kommunikation mit SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Damit eine ODBC-Anwendung mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]einer Instanz von kommunizieren kann, muss sie Umgebungs- und Verbindungshandles zuweisen und eine Verbindung mit der Datenquelle herstellen. Nach dem Herstellen einer Verbindung kann die Anwendung Abfragen an den Server senden und Resultsets verarbeiten. Wenn die Anwendung die Datenquelle nicht mehr benötigt, wird die Verbindung mit der Datenquelle getrennt und das Verbindungshandle freigegeben. Wenn die Anwendung alle Verbindungshandles freigegeben hat, wird das Umgebungshandle freigegeben.  
  
 Eine Anwendung kann mit beliebig vielen Datenquellen eine Verbindung herstellen. Die Anwendung kann eine Kombination aus Treibern und Datenquellen, denselben Treiber und eine Kombination aus Datenquellen oder auch denselben Treiber und mehrere Verbindungen mit derselben Datenquelle verwenden.  
  
 Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Beispiele von der [SQL Server-Downloads-Seite](https://go.microsoft.com/fwlink/?LinkId=62796) auf MSDN herunterladen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Zuordnen eines Umgebungshandles](../../relational-databases/native-client-odbc-communication/allocating-an-environment-handle.md)  
  
-   [Zuordnen eines Verbindungshandles](../../relational-databases/native-client-odbc-communication/allocating-a-connection-handle.md)  
  
-   [SQL Server Native Client ODBC-Datenquellen](../../relational-databases/native-client-odbc-communication/sql-server-native-client-odbc-data-sources.md)  
  
-   [Herstellen einer Verbindung mit einer Datenquelle &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-communication/connecting-to-a-data-source-odbc.md)  
  
-   [Trennen der Verbindung mit einer Datenquelle](../../relational-databases/native-client-odbc-communication/disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)  
  
  
