---
title: Durchführen verteilter Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa5c6b607fa7523380950ecd89f9cae20ffc6f21
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63228950"
---
# <a name="performing-distributed-transactions"></a>Durchführen verteilter Transaktionen
  Microsoft Distributed Transaction Coordinator (MS DTC) ermöglicht es Anwendungen, Transaktionen über zwei oder mehr Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zu erweitern. Außerdem können Anwendungen an von Transaktions-Managern verwalteten Transaktionen teilnehmen, die den Standard Open Group DTP XA erfüllen.  
  
 Normalerweise werden alle Transaktionsverwaltungsbefehle durch den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Native Client-ODBC-Treiber an den Server gesendet. Die Anwendung startet eine Transaktion, durch den Aufruf [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) mit der Autocommit-Modus deaktiviert. Die Anwendung führt anschließend die Updates durch, aus denen die Transaktion besteht, und ruft [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) entweder mit der SQL_COMMIT-Option oder der SQL_ROLLBACK-Option auf.  
  
 Bei Verwendung von MS DTC wird MS DTC zum Transaktions-Manager, und **SQLEndTran**wird von der Anwendung nicht mehr verwendet.  
  
 Wenn der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC Driver in einer verteilten Transaktion eingetragen ist und dann in einer zweiten verteilten Transaktion eingetragen wird, wird er von der ursprünglichen verteilten Transaktion übernommen und in die neue Transaktion eingetragen. Weitere Informationen finden Sie in der [DTC-Programmierreferenz](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Transaktionen &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
