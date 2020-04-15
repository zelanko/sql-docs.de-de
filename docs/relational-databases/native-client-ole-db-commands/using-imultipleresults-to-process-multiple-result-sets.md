---
title: IMultipleResults, mehrere Resultsets
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c5e19cef4e00fc1c55e29e51ccea13c2fdb7a0e2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304446"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Verwenden von 'IMultipleResults' zur Verarbeitung mehrerer Resultsets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Consumer verwenden die **IMultipleResults-Schnittstelle,** um Ergebnisse zu verarbeiten, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Ausführung des Befehls "Native Client OLE DB"-Anbieter zurückgegeben werden. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der native Client-OLE-DB-Anbieter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Befehl zur Ausführung übermittelt, führt er die Anweisungen aus und gibt alle Ergebnisse zurück.  
  
 Ein Client muss alle Ergebnisse der Befehlsausführung verarbeiten. Da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Ausführung des Native Client-OLE-DB-Anbieters als Ergebnis Objekte mit mehreren Rowseten generieren kann, verwenden Sie die **IMultipleResults-Schnittstelle,** um sicherzustellen, dass der vom Client initiierte Roundtrip abgeschlossen wird.  
  
 Die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung generiert mehrere Rowsets, von denen einige Zeilendaten aus der Tabelle **OrderDetails** und einige Ergebnisse der COMPUTE BY-Klausel enthalten:  
  
```sql
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Wenn ein Consumer einen Befehl ausführt, der diesen Text enthält, und ein Rowset als Schnittstelle für die zurückgegebenen Ergebnisse anfordert, wird nur der erste Satz Zeilen zurückgegeben. Der Consumer kann alle Zeilen im zurückgegebenen Rowset verarbeiten. Wenn jedoch die DBPROP_MULTIPLECONNECTIONS Datenquelleneigenschaft auf VARIANT_FALSE festgelegt ist und MARS für die Verbindung nicht aktiviert ist, können keine anderen Befehle für das Sitzungsobjekt ausgeführt werden (der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter erstellt keine weitere Verbindung), bis der Befehl abgebrochen wird. Wenn MARS für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht aktiviert ist, gibt der native Client-OLE-DB-Anbieter einen DB_E_OBJECTOPEN Fehler zurück, wenn DBPROP_MULTIPLECONNECTIONS VARIANT_FALSE ist, und gibt E_FAIL zurück, wenn eine aktive Transaktion vorhanden ist.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt auch DB_E_OBJECTOPEN zurück, wenn gestreamte Ausgabeparameter verwendet werden, und die Anwendung hat nicht alle zurückgegebenen Ausgabeparameterwerte verbraucht, bevor **iMultipleResults::GetResults** aufgerufen wurde, um das nächste Resultset abzurufen. Wenn MARS nicht aktiviert ist und die Verbindung mit der Ausführung eines Befehls beschäftigt ist, der kein Rowset erzeugt oder ein Rowset erzeugt, das kein Servercursor ist, und wenn die DBPROP_MULTIPLECONNECTIONS Datenquelleneigenschaft auf VARIANT_TRUE festgelegt ist, erstellt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter zusätzliche Verbindungen, um gleichzeitige Befehlsobjekte zu unterstützen, es sei denn, eine Transaktion ist aktiv, in diesem Fall gibt sie einen Fehler zurück. Transaktionen und Sperren werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Verbindungsbasis verwaltet. Wenn eine zweite Verbindung hergestellt wird, nutzt der Befehl auf den anderen Verbindungen Sperren nicht gemeinsam. Es muss darauf geachtet werden, dass ein Befehl einen anderen nicht blockiert, indem er Zeilen gesperrt hält, die von einem anderen Befehl angefordert werden. Wenn MARS aktiviert ist, können mehrere Befehle für die Verbindungen aktiv sein, und bei der Verwendung expliziter Transaktionen nutzen die Befehle alle eine gemeinsame Transaktion.  
  
 Der Consumer kann den Befehl abbrechen, indem er [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) verwendet oder alle Verweise auf das Befehlsobjekt und das abgeleitete Rowset freigibt.  
  
 Die Verwendung von **IMultipleResults** in allen Instanzen ermöglicht es, alle Rowsets durch Befehlsausführung zu erstellen, und gestattet es Consumern zu ermitteln, wann die Befehlsausführung abgebrochen und ein Sitzungsobjekt zur Verwendung durch andere Befehle freigegeben werden sollte.  
  
> [!NOTE]  
>  Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursor verwenden, erstellt die Befehlsausführung den Cursor. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt den Erfolg oder Fehler der Cursorerstellung zurück. Der Roundtrip zur Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist damit nach der Rückkehr der Befehlsausführung abgeschlossen. Jeder Aufruf von **GetNextRows** wird dann zum Roundtrip. Auf diese Weise können mehrere Befehlsobjekte vorhanden sein, und jedes verarbeitet ein Rowset, das das Ergebnis eines Abrufs vom Servercursor ist. Weitere Informationen finden Sie unter [Rowsets und SQL Server-Cursor](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
