---
title: Transaktionen in ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b146a3f4a3331ddcfc7606825a0300b986f1a116
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049679"
---
# <a name="transactions-in-odbc"></a>Transaktionen in ODBC
  Transaktionen in ODBC werden auf der Verbindungsebene verwaltet. Wenn eine Anwendung eine Transaktion abschließt, führt sie für alle abgeschlossenen Arbeiten einen Commit oder Rollback über alle Anweisungshandles dieser Verbindung aus. Anwendungen müssen zum Ausführen eines Commits oder eines Rollbacks für eine Transaktion keine COMMIT- oder ROLLBACK-Anweisung übermitteln, sondern [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) aufrufen.  
  
 Eine Anwendung ruft [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) auf, um zwischen den beiden ODBC-Modi für die Verwaltung von Transaktionen zu wechseln:  
  
-   Autocommit-Modus  
  
     Für jede erfolgreich ausgeführte Anweisung wird automatisch ein Commit ausgeführt. Im Autocommit-Modus sind keine anderen Funktionen für die Verwaltung von Transaktionen erforderlich.  
  
-   Manualcommit-Modus  
  
     Alle ausgeführten Anweisungen sind in einer Transaktion enthalten, bis diese durch Aufrufen von **SQLEndTran**ausdrücklich beendet wird.  
  
 Der Autocommit-Modus ist der Standardtransaktionsmodus für ODBC. Beim Herstellen einer Verbindung befindet sich diese zunächst im Autocommit-Modus, bis **SQLSetConnectAttr** aufgerufen wird, um durch Deaktivieren des Autocommit-Modus in den Manualcommit-Modus zu wechseln. Wenn eine Anwendung Autocommit deaktiviert, startet die nächste an die Datenbank gesendete Anweisung eine Transaktion. Die Transaktion bleibt dann so lange aktiv, bis die Anwendung **SQLEndTran** mit der Option SQL_COMMIT oder mit der Option SQL_ROLLBACK aufruft. Der Befehl, der an die Datenbank nach **SQLEndTran** gesendet wird, startet die nächste Transaktion.  
  
 Wenn eine Anwendung vom Manualcommit- in den Autocommit-Modus wechselt, führt der Treiber für alle derzeit für die Verbindung geöffneten Transaktionen einen Commit aus.  
  
 ODBC-Anwendungen dürfen keine Transact-SQL-Transaktionsanweisungen, wie BEGIN TRANSACTION, COMMIT TRANSACTION oder ROLLBACK TRANSACTION, verwenden, da dies zu einem unbestimmten Verhalten des Treibers führen kann. Eine ODBC-Anwendung muss im Autocommit-Modus ausgeführt werden und darf keine Funktionen oder Anweisungen für die Verwaltung von Transaktionen verwenden oder im Manualcommit-Modus ausgeführt werden und die ODBC-Funktion **SQLEndTran** zum Ausführen eines Commits oder eines Rollbacks für Transaktionen verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Transaktionen &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  