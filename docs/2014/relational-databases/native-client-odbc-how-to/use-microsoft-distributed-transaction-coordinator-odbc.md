---
title: Verwenden von Microsoft Distributed Transaction Coordinator (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a938b49a5497aa81b48cb4032286e9d748acceb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048125"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>Verwenden von Microsoft Distributed Transaction Coordinator (ODBC)
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>So aktualisieren Sie zwei oder mehr SQL Server mit MS DTC  
  
1.  Stellen Sie mit der MS DTC OLE-Funktion DtcGetTransactionManager eine Verbindung mit MS DTC her. Informationen zu MS DTC finden Sie unter Microsoft Distributed Transaction Coordinator.  
  
2.  Nennen Sie SQL driverconnect einmal für jede Microsoft SQL Server Verbindung, die Sie einrichten möchten.  
  
3.  Rufen Sie die MS DTC OLE-Funktion ITransactionDispenser::BeginTransaction auf, um eine MS DTC-Transaktion zu starten und ein Transaction-Objekt zu erhalten, das diese Transaktion repräsentiert.  
  
4.  Rufen Sie [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) mindestens einmal für jede ODBC-Verbindung auf, die Sie in der MS DTC-Transaktion auflisten möchten. Der zweite [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)-Parameter muss SQL_ATTR_ENLIST_IN_DTC lauten, und der dritte Parameter muss das Transaktionsobjekt (aus Schritt 3) sein.  
  
5.  Rufen Sie [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) einmal für jeden SQL Server auf, den Sie aktualisieren möchten.  
  
6.  Rufen Sie MS DTC OLE-Funktion ITransaction::Commit auf, um ein Commit für die MS DTC-Transaktion auszuführen. Das Transaction-Objekt ist nicht mehr gültig.  
  
 Um eine Reihe von MS DTC-Transaktionen auszuführen, wiederholen Sie die Schritte 3 bis 6.  
  
 Um den Verweis auf das Transaction-Objekt freizugeben, rufen Sie die MS DTC OLE-Funktion ITransaction::Return auf.  
  
 Wenn Sie eine ODBC-Verbindung mit einer MS DTC-Transaktion und dieselbe Verbindung dann mit einer lokalen SQL Server-Transaktion verwenden möchten, rufen Sie [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) mit SQL_DTC_DONE auf.  
  
> [!NOTE]  
>  Sie können [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) und [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) auch nacheinander für jeden SQL Server aufrufen, statt sie gemäß dem Vorschlag in den Schritten 4 und 5 aufzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Transaktionen &#40;ODBC-&#41;](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
