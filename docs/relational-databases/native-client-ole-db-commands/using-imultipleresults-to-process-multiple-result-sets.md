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
ms.openlocfilehash: a9ad3e29da828e22a656b151659062149a65bf42
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242272"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets-in-sql-server-native-client"></a>Verwenden von IMultipleResults zum Verarbeiten mehrerer Resultsets in SQL Server Native Client
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Consumer verwenden die **IMultipleResults** -Schnittstelle zum Verarbeiten von Ergebnissen, die von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Befehlsausführung des Native Client OLE DB Anbieters zurückgegeben werden. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter einen Befehl zur Ausführung übermittelt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt die Anweisungen aus und gibt alle Ergebnisse zurück.  
  
 Ein Client muss alle Ergebnisse der Befehlsausführung verarbeiten. Da die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Befehlsausführung des Native Client OLE DB-Anbieters mehrere Rowsetobjekte als Ergebnisse generieren kann, verwenden Sie die **IMultipleResults** -Schnittstelle, um sicherzustellen, dass das Abrufen von Anwendungsdaten den vom Client initiierten Roundtrip abschließt.  
  
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
  
 Wenn ein Consumer einen Befehl ausführt, der diesen Text enthält, und ein Rowset als Schnittstelle für die zurückgegebenen Ergebnisse anfordert, wird nur der erste Satz Zeilen zurückgegeben. Der Consumer kann alle Zeilen im zurückgegebenen Rowset verarbeiten. Wenn die DBPROP_MULTIPLECONNECTIONS-Datenquellen Eigenschaft jedoch auf VARIANT_FALSE festgelegt ist und Mars für die Verbindung nicht aktiviert ist, können keine weiteren Befehle für das Sitzungs Objekt ausgeführt werden (der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erstellt keine weitere Verbindung), bis der Befehl abgebrochen wird. Wenn Mars für die Verbindung nicht aktiviert ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt der Native Client OLE DB-Anbieter einen DB_E_OBJECTOPEN Fehler zurück, wenn DBPROP_MULTIPLECONNECTIONS VARIANT_FALSE ist, und gibt E_FAIL zurück, wenn eine aktive Transaktion vorhanden ist.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt DB_E_OBJECTOPEN auch bei Verwendung von gestreuten Ausgabeparametern zurück, und die Anwendung hat nicht alle zurückgegebenen Ausgabeparameter Werte verarbeitet, bevor **IMultipleResults:: GetResults** aufgerufen wird, um das nächste Resultset abzurufen. Wenn Mars nicht aktiviert ist und die Verbindung mit dem Ausführen eines Befehls, der kein Rowset erzeugt, oder eines Rowsets, das kein Server Cursor ist, ausgelastet ist und die DBPROP_MULTIPLECONNECTIONS Datenquellen Eigenschaft auf VARIANT_TRUE festgelegt ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt der Native Client-OLE DB Anbieter zusätzliche Verbindungen zur Unterstützung gleichzeitiger Befehls Objekte, es sei denn, eine Transaktion ist aktiv. in diesem Fall wird ein Fehler zurückgegeben Transaktionen und Sperren werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Verbindungsbasis verwaltet. Wenn eine zweite Verbindung hergestellt wird, nutzt der Befehl auf den anderen Verbindungen Sperren nicht gemeinsam. Es muss darauf geachtet werden, dass ein Befehl einen anderen nicht blockiert, indem er Zeilen gesperrt hält, die von einem anderen Befehl angefordert werden. Wenn MARS aktiviert ist, können mehrere Befehle für die Verbindungen aktiv sein, und bei der Verwendung expliziter Transaktionen nutzen die Befehle alle eine gemeinsame Transaktion.  
  
 Der Consumer kann den Befehl abbrechen, indem er [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) verwendet oder alle Verweise auf das Befehlsobjekt und das abgeleitete Rowset freigibt.  
  
 Die Verwendung von **IMultipleResults** in allen Instanzen ermöglicht es, alle Rowsets durch Befehlsausführung zu erstellen, und gestattet es Consumern zu ermitteln, wann die Befehlsausführung abgebrochen und ein Sitzungsobjekt zur Verwendung durch andere Befehle freigegeben werden sollte.  
  
> [!NOTE]  
>  Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursor verwenden, erstellt die Befehlsausführung den Cursor. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt den Erfolg oder Fehler der Cursorerstellung zurück. Der Roundtrip zur Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist damit nach der Rückkehr der Befehlsausführung abgeschlossen. Jeder Aufruf von **GetNextRows** wird dann zum Roundtrip. Auf diese Weise können mehrere Befehlsobjekte vorhanden sein, und jedes verarbeitet ein Rowset, das das Ergebnis eines Abrufs vom Servercursor ist. Weitere Informationen finden Sie unter [Rowsets und SQL Server-Cursor](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
