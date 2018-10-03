---
title: Verwenden von „IMultipleResults“ zur Verarbeitung mehrerer Resultsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e160733e01c3df2063a57d61bb8178438d383e1a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069933"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Verwenden von 'IMultipleResults' zur Verarbeitung mehrerer Resultsets
  Consumer verwenden die **IMultipleResults** Schnittstelle zum Verarbeiten von zurückgegebenen Ergebnisse [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befehlsausführung für Native Client OLE DB-Anbieter. Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter sendet einen Befehl zur Ausführung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt die Anweisungen aus und gibt die Ergebnisse zurück.  
  
 Ein Client muss alle Ergebnisse der Befehlsausführung verarbeiten. Da die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befehlsausführung für Native Client OLE DB-Anbieter kann mehrere Rowsetobjekte als Ergebnisse generiert werden soll, verwenden Sie die **IMultipleResults** Schnittstelle, um sicherzustellen, dass die Anwendung den Datenabruf abgeschlossen ist. die vom Client initiierten Roundtrip.  
  
 Die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung generiert mehrere Rowsets, von denen einige Zeilendaten aus der Tabelle **OrderDetails** und einige Ergebnisse der COMPUTE BY-Klausel enthalten:  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Wenn ein Consumer einen Befehl ausführt, der diesen Text enthält, und ein Rowset als Schnittstelle für die zurückgegebenen Ergebnisse anfordert, wird nur der erste Satz Zeilen zurückgegeben. Der Consumer kann alle Zeilen im zurückgegebenen Rowset verarbeiten. Aber wenn die DBPROP_MULTIPLECONNECTIONS-Datenquelleneigenschaft auf festgelegt ist VARIANT_FALSE und MARS nicht für die Verbindung aktiviert ist, können keine anderen Befehle für das Sitzungsobjekt ausgeführt werden (die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird nicht erstellt, eine andere Verbindung), bis der Befehl abgebrochen wird. Wenn MARS nicht, für die Verbindung aktiviert ist der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt DB_E_OBJECTOPEN-Fehler zurück, wenn DBPROP_MULTIPLECONNECTIONS VARIANT_FALSE lautet, und E_FAIL, wenn eine aktive Transaktion vorhanden ist.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt DB_E_OBJECTOPEN Verwendung gestreamt Output-Parameter, und die Anwendung alle zurückgegebenen Ausgabeparameterwerte vor dem Aufruf nicht verbraucht hat auch **IMultipleResults:: GetResults**  um das nächste Resultset abzurufen. Wenn MARS nicht aktiviert ist, und die Verbindung ist das Ausführen eines Befehls, der kein Rowset produziert wird, oder, erzeugt ein Rowset, das kein Servercursor ist, ausgelastet und die DBPROP_MULTIPLECONNECTIONS-Datenquelleneigenschaft auf VARIANT_TRUE festgelegt ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erstellt zusätzliche Verbindungen um gleichzeitige Befehlsobjekte zu unterstützen, wenn eine Transaktion aktiv ist, in diesem Fall gibt einen Fehler. Transaktionen und Sperren werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Verbindungsbasis verwaltet. Wenn eine zweite Verbindung hergestellt wird, nutzt der Befehl auf den anderen Verbindungen Sperren nicht gemeinsam. Es muss darauf geachtet werden, dass ein Befehl einen anderen nicht blockiert, indem er Zeilen gesperrt hält, die von einem anderen Befehl angefordert werden. Wenn MARS aktiviert ist, können mehrere Befehle für die Verbindungen aktiv sein, und bei der Verwendung expliziter Transaktionen nutzen die Befehle alle eine gemeinsame Transaktion.  
  
 Der Consumer kann den Befehl abbrechen, indem er [ISSAbort::Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md) verwendet oder alle Verweise auf das Befehlsobjekt und das abgeleitete Rowset freigibt.  
  
 Die Verwendung von **IMultipleResults** in allen Instanzen ermöglicht es, alle Rowsets durch Befehlsausführung zu erstellen, und gestattet es Consumern zu ermitteln, wann die Befehlsausführung abgebrochen und ein Sitzungsobjekt zur Verwendung durch andere Befehle freigegeben werden sollte.  
  
> [!NOTE]  
>  Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursor verwenden, erstellt die Befehlsausführung den Cursor. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt den Erfolg oder Fehler der Cursorerstellung zurück. Der Roundtrip zur Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist damit nach der Rückkehr der Befehlsausführung abgeschlossen. Jeder Aufruf von **GetNextRows** wird dann zum Roundtrip. Auf diese Weise können mehrere Befehlsobjekte vorhanden sein, und jedes verarbeitet ein Rowset, das das Ergebnis eines Abrufs vom Servercursor ist. Weitere Informationen finden Sie unter [Rowsets und SQL Server-Cursor](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle](commands.md)  
  
  
