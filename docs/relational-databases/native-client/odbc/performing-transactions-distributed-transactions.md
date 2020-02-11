---
title: Erstellen verteilter Transaktionen | Microsoft-Dokumentation
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b01e47f81f153b73c8a57d23c9a75fc8b57ef66
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761068"
---
# <a name="create-a-distributed-transaction"></a>Erstellen einer verteilten Transaktion

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->


Eine verteilte Transaktion kann für verschiedene Microsoft SQL-Systeme auf unterschiedliche Weise erstellt werden.

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>Der ODBC-Treiber ruft MSDTC für SQL Server lokal auf.

Mit dem Microsoft Distributed Transaction Coordinator (MSDTC) können Anwendungen eine Transaktion __ auf zwei oder mehr Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ausweiten oder verteilen. Die verteilte Transaktion funktioniert auch dann, wenn die beiden Instanzen auf separaten Computern gehostet werden.

MSDTC wird für Microsoft SQL Server lokal installiert, ist aber für den Azure SQL-Datenbank-clouddienst von Microsoft nicht verfügbar.

MSDTC wird vom SQL Server Native Client Driver for Open Database Connectivity (ODBC) aufgerufen, wenn das C++-Programm eine verteilte Transaktion verwaltet. Der Native Client-ODBC-Treiber verfügt über einen Transaktions-Manager, der mit dem "Open Group verteilte Transaction Processing (DTP) XA"-Standard kompatibel ist. Diese Konformität ist für MSDTC erforderlich. Normalerweise werden alle Transaktions Verwaltungs Befehle über diesen Native Client-ODBC-Treiber gesendet. Der Ablauf ist wie folgt:

1. Ihre C++ Native Client-ODBC-Anwendung startet eine Transaktion durch Aufrufen von [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), während der Autocommit-Modus ausgeschaltet ist.

2. Die Anwendung aktualisiert einige Daten auf SQL Server X auf Computer A.

3. Die Anwendung aktualisiert einige Daten auf SQL Server Y auf Computer B.
    - Wenn ein Update auf SQL Server Y fehlschlägt, wird für alle Updates, für die kein Commit ausgeführt wurde, in beiden SQL Server Instanzen ein Rollback ausgeführt

4. Schließlich beendet die Anwendung die Transaktion durch Aufrufen von [SQLEndTran _(1)_](../../../relational-databases/native-client-odbc-api/sqlendtran.md), entweder mit der Option SQL_COMMIT oder SQL_ROLLBACK.

_(1)_ MSDTC kann ohne ODBC aufgerufen werden. In einem solchen Fall wird MSDTC zum Transaktions-Manager, und die Anwendung verwendet nicht mehr **SQLEndTran**.

### <a name="only-one-distributed-transaction"></a>Nur eine verteilte Transaktion

Angenommen, Ihre C++ Native Client-ODBC-Anwendung ist in einer verteilten Transaktion eingetragen. Im nächsten Schritt wird die Anwendung in einer zweiten verteilten Transaktion eingetragen. In diesem Fall verlässt der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber die ursprüngliche verteilte Transaktion und trägt in die neue verteilte Transaktion ein.

Weitere Informationen finden Sie in der [DTC-Programmierreferenz](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\)).

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>C#-Alternative für die SQL-Datenbank in der Cloud

MSDTC wird weder für Azure SQL-Datenbank noch für Azure SQL Data Warehouse unterstützt.

Eine verteilte Transaktion kann jedoch für die SQL-Datenbank erstellt werden, indem das c#-Programm die .NET-Klasse [System. Transactions. transaktionscope](/dotnet/api/system.transactions.transactionscope)verwendet.

### <a name="other-programming-languages"></a>Andere Programmiersprachen

Die folgenden anderen Programmiersprachen bieten möglicherweise keine Unterstützung für verteilte Transaktionen mit dem SQL-Datenbankdienst:

- Native C++, die ODBC-Treiber verwenden
- Verbindungs Server mit Transact-SQL
- JDBC-Treiber

## <a name="see-also"></a>Weitere Informationen

[Durchführen von Transaktionen (ODBC)](performing-transactions-in-odbc.md)
