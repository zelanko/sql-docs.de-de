---
title: Cursor-Transaktionsisolationsstufe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fef68bfdb62527f7b631b8d7433e095eba4d1c88
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118560"
---
# <a name="cursor-transaction-isolation-level"></a>Transaktionsisolationsstufen von Cursorn
  Das komplette Sperrverhalten von Cursorn basiert auf der Interaktion zwischen Parallelitätsattributen und der vom Client festgelegten Transaktionsisolationsstufe. ODBC-Clients legen die Transaktionsisolationsstufe mithilfe der [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION oder SQL_COPT_SS_TXN_ISOLATION-Attribut. Das Transaktionssperrverhalten einer bestimmten Cursorumgebung wird durch die Kombination des Sperrverhaltens der Parallelitätseinstellung mit den Optionen für die Transaktionsisolationsstufen bestimmt.  
  
 Die folgenden cursortransaktionsisolationsstufen werden von unterstützt die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber:  
  
-   Read Committed (SQL_TXN_READ_COMMITTED)  
  
-   Read Uncommitted (SQL_TXN_READ_UNCOMMITTED)  
  
-   Repeatable Read (SQL_TXN_REPEATABLE_READ) lesen Sie  
  
-   Serializable (SQL_TXN_SERIALIZABLE)  
  
-   Momentaufnahme (SQL_TXN_SS_SNAPSHOT)  
  
 Beachten Sie, dass der ODBC-API zusätzliche Transaktionsisolationsstufen gibt, aber diese nicht, indem unterstützt werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber.  
  
## <a name="see-also"></a>Siehe auch  
 [Cursoreigenschaften](cursor-properties.md)  
  
  
