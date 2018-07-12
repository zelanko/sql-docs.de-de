---
title: Durchführen verteilter Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac35e6d366834e2d75e2aacd8311bd3f0ace1f5f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411509"
---
# <a name="performing-distributed-transactions"></a>Durchführen verteilter Transaktionen
  Microsoft Distributed Transaction Coordinator (MS DTC) ermöglicht es Anwendungen, Transaktionen über zwei oder mehr Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu erweitern. Außerdem können Anwendungen an von Transaktions-Managern verwalteten Transaktionen teilnehmen, die den Standard Open Group DTP XA erfüllen.  
  
 Normalerweise werden alle transaktionsverwaltungsbefehle gesendet, über die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber an den Server. Die Anwendung startet eine Transaktion, durch den Aufruf [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) mit der Autocommit-Modus deaktiviert. Die Anwendung führt anschließend die Updates, die mit der Transaktion aus und ruft [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) mit der Option SQL_COMMIT oder SQL_ROLLBACK-Option.  
  
 Bei Verwendung von MS DTC wird MS DTC zum Transaktions-Manager, und **SQLEndTran**wird von der Anwendung nicht mehr verwendet.  
  
 Wenn der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC Driver in einer verteilten Transaktion eingetragen ist und dann in einer zweiten verteilten Transaktion eingetragen wird, wird er von der ursprünglichen verteilten Transaktion übernommen und in die neue Transaktion eingetragen. Weitere Informationen finden Sie in der [DTC-Programmierreferenz](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Transaktionen &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
