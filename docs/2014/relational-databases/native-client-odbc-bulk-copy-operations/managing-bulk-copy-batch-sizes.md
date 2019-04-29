---
title: Verwalten von Batchgrößen für das Massenkopieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07f87bf0f231419e4f1345369211ba6ceebf1d12
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199171"
---
# <a name="managing-bulk-copy-batch-sizes"></a>Verwalten von Batchgrößen für das Massenkopieren
  Der Hauptzweck eines Batches in Massenkopiervorgängen besteht darin, den Umfang einer Transaktion zu definieren. Wenn keine Batchgröße festgelegt ist, wird der gesamte Massenkopiervorgang von den Massenkopierfunktionen als eine einzige Transaktion behandelt. Ist eine Batchgröße festgelegt, stellt jeder Batch eine Transaktion dar, für die nach Beendigung des Batches ein Commit ausgeführt wird.  
  
 Wenn ein Massenkopiervorgang ohne festgelegte Batchgröße ausgeführt wird und ein Fehler auftritt, wird für den gesamten Massenkopiervorgang ein Rollback durchgeführt. Das Wiederherstellen eines Massenkopiervorgangs mit langer Laufzeit kann einige Zeit in Anspruch nehmen. Wenn eine Batchgröße festgelegt wird, wird jeder Batch als Transaktion betrachtet und ein Commit für jeden Batch ausgeführt. Wenn ein Fehler auftritt, muss nur für den letzten ausstehenden Batch ein Rollback ausgeführt werden.  
  
 Die Batchgröße kann auch den Sperrenaufwand beeinflussen. Beim Durchführen eines Massenkopiervorgangs für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], der TABLOCK-Hinweis kann angegeben werden, mithilfe von [Bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) , eine Tabellensperre statt Zeilensperren abzurufen. Die einzelne Tabellensperre kann mit minimalem Aufwand für einen ganzen Massenkopiervorgang aufrechterhalten werden. Wird TABLOCK nicht festgelegt, werden Sperren für einzelne Zeilen errichtet und der Aufwand zur Aufrechterhaltung aller Sperren für die Dauer des Massenkopiervorgangs kann die Leistung beeinträchtigen. Da die Sperren nur für die Dauer der Transaktion aufrechterhalten werden, wird dieses Problem durch Angabe einer Batchgröße behoben, indem ein Commit ausgeführt wird, mit dem die aktuellen Sperren freigegeben werden.  
  
 Die Anzahl der Zeilen, die zu einem Batch gehören, kann sich erheblich auf die Leistung auswirken, wenn die Zeilenzahl für das Massenkopieren groß ist. Die Empfehlungen für die Batchgröße hängen vom Typ des auszuführenden Massenkopiervorgangs ab.  
  
-   Bei einem Massenkopiervorgang in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geben Sie den TABLOCK-Massenkopierhinweis an und legen eine große Batchgröße fest.  
  
-   Wenn TABLOCK nicht angegeben wird, beschränken Sie Batchgrößen auf unter 1.000 Zeilen.  
  
 Beim Massenkopieren aus einer Datendatei, entspricht die Batchgröße durch Aufrufen von **Bcp_control** mit der BCPBATCH-Option vor dem Aufruf [Bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md). Beim Massenkopieren aus Programmvariablen mit [Bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) und [Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), wird die Batchgröße durch Aufrufen von gesteuert [Bcp_batch](../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) nach dem Aufruf [Bcp_ Sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x* -Mal ab, wobei *x* ist die Anzahl der Zeilen in einem Batch.  
  
 Batches sind nicht nur für das Festlegen der Größe einer Transaktion relevant, sondern wirken sich auch auf den Zeitpunkt aus, an dem Zeilen über das Netzwerk an den Server gesendet werden. Funktionen zum Massenkopieren normalerweise zwischengespeichert, die Zeilen aus **Bcp_sendrow** bis ein Netzwerkpaket gefüllt ist, und klicken Sie dann das volle Paket an den Server gesendet. Wenn eine Anwendung ruft **Bcp_batch**, allerdings wird das aktuelle Paket an den Server unabhängig davon, ob es aufgefüllt wurde gesendet. Eine sehr niedrige Batchgröße kann die Leistung herabsetzen, wenn dadurch viele teilweise aufgefüllte Pakete an den Server gesendet werden. Zum Beispiel der Aufruf **Bcp_batch** nach jeder **Bcp_sendrow** bewirkt, dass jede Zeile in einem einzelnen Paket gesendet werden, und, es sei denn, die Zeilen sehr umfangreich sind, verschwendet in jedem Paket Platz. Die Standardgröße von Netzwerkpaketen für SQL Server beträgt 4 KB, obwohl eine Anwendung durch Aufrufen die Größe geändert werden kann [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) angeben des SQL_ATTR_PACKET_SIZE-Attributs.  
  
 Ein anderer Nebeneffekt von Batches ist, dass jeder Batch als ausstehendes Resultset bis zum Abschluss mit berücksichtigt wird **Bcp_batch**. Wenn keine anderen Vorgänge für ein Verbindungshandle auszuführen versucht werden, während ein Batch aussteht, ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber gibt einen Fehler mit SQLState = "HY000" und der Zeichenfolge mit einer Fehlermeldung:  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)   
 [Massenimport und -export von Daten &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
