---
title: Durchführen verteilter Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 588fc51619624b59aef4db1a27deff33d75f8b2a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561420"
---
# <a name="performing-transactions---distributed-transactions"></a>Ausführen von Transaktionen – verteilte Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft Distributed Transaction Coordinator (MS DTC) ermöglicht es Anwendungen, Transaktionen über zwei oder mehr Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu erweitern. Außerdem können Anwendungen an von Transaktions-Managern verwalteten Transaktionen teilnehmen, die den Standard Open Group DTP XA erfüllen.  
  
 Normalerweise werden alle transaktionsverwaltungsbefehle gesendet, über die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber an den Server. Die Anwendung startet eine Transaktion, durch den Aufruf [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) mit der Autocommit-Modus deaktiviert. Die Anwendung führt anschließend die Updates, die mit der Transaktion aus und ruft [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) mit der Option SQL_COMMIT oder SQL_ROLLBACK-Option.  
  
 Bei Verwendung von MS DTC wird MS DTC zum Transaktions-Manager, und **SQLEndTran**wird von der Anwendung nicht mehr verwendet.  
  
 Wenn der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC Driver in einer verteilten Transaktion eingetragen ist und dann in einer zweiten verteilten Transaktion eingetragen wird, wird er von der ursprünglichen verteilten Transaktion übernommen und in die neue Transaktion eingetragen. Weitere Informationen finden Sie in der [DTC-Programmierreferenz](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Transaktionen &#40;ODBC&#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
