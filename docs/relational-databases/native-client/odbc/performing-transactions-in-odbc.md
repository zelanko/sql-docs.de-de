---
title: Transaktionen in ODBC | Microsoft-Dokumentation
description: ODBC verwaltet Transaktionen auf der Verbindungs Ebene und führt einen Commit oder Rollback für alle abgeschlossenen Arbeiten aus, entweder im Autocommit-Modus oder im manuellen Commit-Modus.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 175bc304e1a2127873c54da79fd921995af17714
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84950237"
---
# <a name="performing-transactions-in-odbc"></a>Ausführen von Transaktionen in ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Transaktionen in ODBC werden auf der Verbindungsebene verwaltet. Wenn eine Anwendung eine Transaktion abschließt, führt sie für alle abgeschlossenen Arbeiten einen Commit oder Rollback über alle Anweisungshandles dieser Verbindung aus. Anwendungen müssen zum Ausführen eines Commits oder eines Rollbacks für eine Transaktion keine COMMIT- oder ROLLBACK-Anweisung übermitteln, sondern [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) aufrufen.  
  
 Eine Anwendung ruft [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) auf, um zwischen den beiden ODBC-Modi für die Verwaltung von Transaktionen zu wechseln:  
  
-   Autocommit-Modus  
  
     Für jede erfolgreich ausgeführte Anweisung wird automatisch ein Commit ausgeführt. Im Autocommit-Modus sind keine anderen Funktionen für die Verwaltung von Transaktionen erforderlich.  
  
-   Manualcommit-Modus  
  
     Alle ausgeführten Anweisungen sind in einer Transaktion enthalten, bis diese durch Aufrufen von **SQLEndTran**ausdrücklich beendet wird.  
  
 Der Autocommit-Modus ist der Standardtransaktionsmodus für ODBC. Beim Herstellen einer Verbindung befindet sich diese zunächst im Autocommit-Modus, bis **SQLSetConnectAttr** aufgerufen wird, um durch Deaktivieren des Autocommit-Modus in den Manualcommit-Modus zu wechseln. Wenn eine Anwendung Autocommit deaktiviert, startet die nächste an die Datenbank gesendete Anweisung eine Transaktion. Die Transaktion bleibt dann so lange aktiv, bis die Anwendung **SQLEndTran** mit der Option SQL_COMMIT oder mit der Option SQL_ROLLBACK aufruft. Der Befehl, der an die Datenbank nach **SQLEndTran** gesendet wird, startet die nächste Transaktion.  
  
 Wenn eine Anwendung vom Manualcommit- in den Autocommit-Modus wechselt, führt der Treiber für alle derzeit für die Verbindung geöffneten Transaktionen einen Commit aus.  
  
 ODBC-Anwendungen dürfen keine Transact-SQL-Transaktionsanweisungen, wie BEGIN TRANSACTION, COMMIT TRANSACTION oder ROLLBACK TRANSACTION, verwenden, da dies zu einem unbestimmten Verhalten des Treibers führen kann. Eine ODBC-Anwendung muss im Autocommit-Modus ausgeführt werden und darf keine Funktionen oder Anweisungen für die Verwaltung von Transaktionen verwenden oder im Manualcommit-Modus ausgeführt werden und die ODBC-Funktion **SQLEndTran** zum Ausführen eines Commits oder eines Rollbacks für Transaktionen verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Transaktionen &#40;ODBC-&#41;](https://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
