---
description: Transaktionsisolationsstufen von Cursorn
title: Isolationsstufe für Cursor Transaktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 475ad9fd8965cd74cb46691117df05815d0d2e84
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97473701"
---
# <a name="cursor-transaction-isolation-level"></a>Transaktionsisolationsstufen von Cursorn
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Das komplette Sperrverhalten von Cursorn basiert auf der Interaktion zwischen Parallelitätsattributen und der vom Client festgelegten Transaktionsisolationsstufe. ODBC-Clients legen die Transaktions Isolationsstufe mithilfe der Attribute [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION oder SQL_COPT_SS_TXN_ISOLATION fest. Das Transaktionssperrverhalten einer bestimmten Cursorumgebung wird durch die Kombination des Sperrverhaltens der Parallelitätseinstellung mit den Optionen für die Transaktionsisolationsstufen bestimmt.  
  
 Die folgenden Cursor Transaktions Isolations Stufen werden vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt:  
  
-   Read Committed (SQL_TXN_READ_COMMITTED)  
  
-   Read Uncommitted (SQL_TXN_READ_UNCOMMITTED)  
  
-   Repeatable Read (SQL_TXN_REPEATABLE_READ) lesen Sie  
  
-   Serializable (SQL_TXN_SERIALIZABLE)  
  
-   Momentaufnahme (SQL_TXN_SS_SNAPSHOT)  
  
 Beachten Sie, dass die ODBC-API zusätzliche Transaktions Isolations Stufen angibt. Diese werden jedoch von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber nicht unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cursoreigenschaften](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
