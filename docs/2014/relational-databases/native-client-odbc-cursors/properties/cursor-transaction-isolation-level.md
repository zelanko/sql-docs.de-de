---
title: Isolationsstufe für Cursor Transaktion | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9c183af3a8db4ad9e08f15083462806244aa8187
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705558"
---
# <a name="cursor-transaction-isolation-level"></a>Transaktionsisolationsstufen von Cursorn
  Das komplette Sperrverhalten von Cursorn basiert auf der Interaktion zwischen Parallelitätsattributen und der vom Client festgelegten Transaktionsisolationsstufe. ODBC-Clients legen die Transaktions Isolationsstufe mithilfe der Attribute [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION oder SQL_COPT_SS_TXN_ISOLATION fest. Das Transaktionssperrverhalten einer bestimmten Cursorumgebung wird durch die Kombination des Sperrverhaltens der Parallelitätseinstellung mit den Optionen für die Transaktionsisolationsstufen bestimmt.  
  
 Die folgenden Cursor Transaktions Isolations Stufen werden vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt:  
  
-   Read Committed (SQL_TXN_READ_COMMITTED)  
  
-   Read Uncommitted (SQL_TXN_READ_UNCOMMITTED)  
  
-   Repeatable Read (SQL_TXN_REPEATABLE_READ) lesen Sie  
  
-   Serializable (SQL_TXN_SERIALIZABLE)  
  
-   Momentaufnahme (SQL_TXN_SS_SNAPSHOT)  
  
 Beachten Sie, dass die ODBC-API zusätzliche Transaktions Isolations Stufen angibt. Diese werden jedoch von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber nicht unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cursoreigenschaften](cursor-properties.md)  
  
  
