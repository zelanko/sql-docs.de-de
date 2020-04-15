---
title: Erstellen einer verteilten Transaktion | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f21ea9b7146b2907a09688f5189d6d9ae4f3f26a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303697"
---
# <a name="create-a-distributed-transaction"></a>Erstellen einer verteilten Transaktion

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->


Eine verteilte Transaktion kann auf unterschiedliche Weise für verschiedene Microsoft SQL-Systeme erstellt werden.

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>ODBC-Treiber ruft den MSDTC für SQL Server lokal auf

Der Microsoft Distributed Transaction Coordinator (MSDTC) _distribute_ ermöglicht Anwendungen das Erweitern [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]oder Verteilen einer Transaktion auf zwei oder mehr Instanzen von . Die verteilte Transaktion funktioniert auch dann, wenn die beiden Instanzen auf separaten Computern gehostet werden.

MSDTC ist für Microsoft SQL Server lokal installiert, jedoch nicht für den Azure SQL-Datenbank-Clouddienst von Microsoft verfügbar.

MSDTC wird vom SQL Server Native Client-Treiber für Open Database Connectivity (ODBC) aufgerufen, wenn Ihr C++-Programm eine verteilte Transaktion verwaltet. Der Native Client ODBC-Treiber verfügt über einen Transaktions-Manager, der mit dem DTP-XA-Standard (Open Group Distributed Transaction Processing) kompatibel ist. Diese Konformität ist von MSDTC erforderlich. In der Regel werden alle Transaktionsverwaltungsbefehle über diesen Native Client ODBC-Treiber gesendet. Der Ablauf ist wie folgt:

1. Ihre C++ Native Client ODBC-Anwendung startet eine Transaktion, indem sie [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)aufruft, wobei der Autocommit-Modus deaktiviert ist.

2. Die Anwendung aktualisiert einige Daten auf SQL Server X auf Computer A.

3. Die Anwendung aktualisiert einige Daten auf SQL Server Y auf Computer B.
    - Wenn eine Aktualisierung auf SQL Server Y fehlschlägt, werden alle nicht festgeschriebenen Updates auf beiden SQL Server-Instanzen zurückgesetzt.

4. Schließlich beendet die Anwendung die Transaktion, indem sie [SQLEndTran _(1)_](../../../relational-databases/native-client-odbc-api/sqlendtran.md)aufruft, entweder mit der Option SQL_COMMIT oder SQL_ROLLBACK.

_(1)_ MSDTC kann ohne ODBC aufgerufen werden. In einem solchen Fall wird MSDTC zum Transaktions-Manager, und die Anwendung verwendet **SQLEndTran**nicht mehr .

### <a name="only-one-distributed-transaction"></a>Nur eine verteilte Transaktion

Angenommen, Ihre C++-Native Client ODBC-Anwendung wird in einer verteilten Transaktion eingetragen. Als Nächstes wird die Anwendung in eine zweite verteilte Transaktion eingeschrieben. In diesem Fall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verlässt der Native Client ODBC-Treiber die ursprüngliche verteilte Transaktion und wird in die neue verteilte Transaktion aufgenommen.

Weitere Informationen finden Sie in der [DTC-Programmierreferenz](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\)).

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>Alternative für SQL-Datenbank in der Cloud

MSDTC wird weder für Azure SQL-Datenbank noch für Azure SQL Data Warehouse unterstützt.

Eine verteilte Transaktion kann jedoch für SQL-Datenbank erstellt werden, indem Das Programm "C" die .NET-Klasse [System.Transactions.TransactionScope](/dotnet/api/system.transactions.transactionscope)verwendet.

### <a name="other-programming-languages"></a>Andere Programmiersprachen

Die folgenden anderen Programmiersprachen bieten möglicherweise keine Unterstützung für verteilte Transaktionen mit dem SQL-Datenbankdienst:

- Native C++-Code, die ODBC-Treiber verwenden
- Verknüpfter Server mit Transact-SQL
- JDBC-Treiber

## <a name="see-also"></a>Siehe auch

[Durchführen von Transaktionen (ODBC)](performing-transactions-in-odbc.md)
