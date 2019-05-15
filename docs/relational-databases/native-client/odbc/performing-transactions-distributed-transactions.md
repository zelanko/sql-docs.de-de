---
title: Erstellen Sie eine verteilte Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ea6c4886a3c5397777b7a65afe96ab7e1b422bd
ms.sourcegitcommit: 553ecea0427e4d2118ea1ee810f4a73275b40741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65620545"
---
# <a name="create-a-distributed-transaction"></a>Erstellen einer verteilten Transaktions

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->

[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

Eine verteilte Transaktion kann für verschiedene Microsoft SQL-Systeme auf unterschiedliche Weise erstellt werden.

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>ODBC-Treiber ruft MSDTC für SQL Server lokal

Der Microsoft Distributed Transaction Coordinator (MSDTC) ermöglicht Anwendungen das Erweitern oder _verteilen_ eine Transaktion für zwei oder mehr Instanzen des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Die verteilte Transaktion funktioniert auch, wenn die beiden Instanzen auf separaten Computern gehostet werden.

MSDTC ist für Microsoft SQL Server lokal installiert, aber nicht für Cloud-Dienst von Microsoft Azure SQL-Datenbank verfügbar ist.

MSDTC wird aufgerufen, durch den SQL Server Native Client-Treiber für Open Database Connectivity (ODBC), wenn Ihre C++ Programm verwaltet eine verteilte Transaktion. Der Native Client ODBC-Treiber hat einen Transaktions-Manager, der mit der Open Gruppe verteilte Transaktion verarbeitet (DTP) XA-standard kompatibel ist. Diese Kompatibilität ist MSDTC erforderlich. In der Regel werden alle transaktionsverwaltungsbefehle durch diese Native Client ODBC-Treiber gesendet. Die Sequenz lautet wie folgt aus:

1. Ihre C++ Native Client ODBC-Anwendung startet eine Transaktion, durch den Aufruf [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), mit der Autocommit-Modus deaktiviert.

2. Die Anwendung aktualisiert, einige Daten in SQL Server-X auf Computer A.

3. Aktualisiert die Anwendung einige Daten auf dem SQL Server-Y auf Computer B.
    - Wenn ein Update auf dem SQL Server-Y ein Fehler auftritt, werden alle ohne ausgeführten Commit-Updates auf beiden SQL Server-Instanzen ein Rollback ausgeführt.

4. Schließlich die Anwendung beendet die Transaktion durch Aufrufen von [SQLEndTran _(1)_](../../../relational-databases/native-client-odbc-api/sqlendtran.md), mit der Option SQL_COMMIT oder SQL_ROLLBACK-Option.

_(1)_  MSDTC kann aufgerufen werden, ohne zu ODBC. In diesem Fall wird MSDTC der Transaktions-Manager, und die Anwendung nicht mehr verwendet **SQLEndTran**.

### <a name="only-one-distributed-transaction"></a>Nur eine verteilte Transaktion

Nehmen wir an, die Ihre C++ Native Client ODBC-Anwendung in einer verteilten Transaktion eingetragen ist. Als Nächstes wird die Anwendung in einer zweiten verteilten Transaktion eingetragen. In diesem Fall die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber die ursprüngliche verteilte Transaktion lässt und in die neue verteilte Transaktion eingetragen.

Weitere Informationen finden Sie in der [DTC-Programmierreferenz](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\)).

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>C#Alternative zur SQL-Datenbank in der cloud

MSDTC wird für Azure SQL-Datenbank oder Azure SQL Data Warehouse nicht unterstützt.

Eine verteilte Transaktion kann jedoch für SQL-Datenbank erstellt werden, indem Sie Ihre C# Programm verwenden, die Klasse .NET [System.Transactions.TransactionScope](/dotnet/api/system.transactions.transactionscope).

### <a name="other-programming-languages"></a>Andere Programmiersprachen

Die folgenden anderen Programmiersprachen gewährleistet keine Unterstützung für verteilte Transaktionen mit dem SQL-Datenbank-Dienst:

- Native C++ , die ODBC-Treiber verwenden
- Verbindungsserver mithilfe von Transact-SQL
- JDBC-Treiber

## <a name="see-also"></a>Siehe auch

[Durchführen von Transaktionen (ODBC)](performing-transactions-in-odbc.md)
