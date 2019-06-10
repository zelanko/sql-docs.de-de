---
title: Verwenden von „IMultipleResults“ zur Verarbeitung mehrerer Resultsets | Microsoft-Dokumentation
description: Verwenden von „IMultipleResults“ zur Verarbeitung mehrerer Resultsets
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: a8a2b76946245021683f3224f67070dce04c3ed0
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66768586"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Verwenden von 'IMultipleResults' zur Verarbeitung mehrerer Resultsets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Consumer verwenden die **IMultipleResults**-Schnittstelle, um Ergebnisse zu verarbeiten, die von einer Befehlsausführung des OLE DB-Treibers für SQL Server zurückgegeben wurden. Wenn der OLE DB-Treiber für SQL Server einen Befehl zur Ausführung übergibt, führt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Anweisungen aus und gibt Ergebnisse zurück.  
  
 Ein Client muss alle Ergebnisse der Befehlsausführung verarbeiten. Da die Befehlsausführung des OLE DB-Treibers für SQL Server mehrere Rowset-Objekte als Ergebnis generieren kann, verwenden Sie die **IMultipleResults**-Schnittstelle, um sicherzustellen, dass das Abrufen der Anwendungsdaten den vom Client initiierten Roundtrip vollständig durchläuft.  
  
 Die folgende [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung generiert mehrere Rowsets, von denen einige Zeilendaten aus der Tabelle **OrderDetails** und einige Ergebnisse der COMPUTE BY-Klausel enthalten:  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Wenn ein Consumer einen Befehl ausführt, der diesen Text enthält, und ein Rowset als Schnittstelle für die zurückgegebenen Ergebnisse anfordert, wird nur der erste Satz Zeilen zurückgegeben. Der Consumer kann alle Zeilen im zurückgegebenen Rowset verarbeiten. Wenn jedoch die DBPROP_MULTIPLECONNECTIONS-Datenquelleneigenschaft auf VARIANT_FALSE festgelegt ist und MARS nicht für die Verbindung aktiviert ist, können keine anderen Befehle für das Sitzungsobjekt ausgeführt werden (der OLE DB-Treiber für SQL Server stellt keine weitere Verbindung her), bis der Befehl abgebrochen wird. Wenn MARS nicht für die Verbindung aktiviert ist, gibt der OLE DB-Treiber für SQL Server den DB_E_OBJECTOPEN-Fehler zurück, wenn DBPROP_MULTIPLECONNECTIONS auf VARIANT_FALSE lautet, und E_FAIL, wenn es eine aktive Transaktion gibt.  
  
 Der OLE DB-Treiber für SQL Server gibt auch dann DB_E_OBJECTOPEN zurück, wenn er einen Ausgabeparameter-Stream verwendet und die Anwendung nicht alle zurückgegebenen Ausgabeparameterwerte verarbeitet hat, bevor das nächste Resultset mit **IMultipleResults::GetResults** abgerufen wird. Wenn MARS nicht aktiviert und die Verbindung mit der Ausführung eines Befehls ausgelastet ist, der kein Rowset oder ein Rowset, der kein Servercursor ist, generiert, und die DBPROP_MULTIPLECONNECTIONS-Datenquelleneigenschaft auf VARIANT_TRUE festgelegt ist, stellt der OLE DB-Treiber für SQL Server zusätzliche Verbindungen her, um gleichzeitige Befehlsobjekte zu unterstützen, sofern keine Transaktion aktiv ist. Im letzteren Fall würde er einen Fehler zurückgeben. Transaktionen und Sperren werden von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf Verbindungsbasis verwaltet. Wenn eine zweite Verbindung hergestellt wird, nutzt der Befehl auf den anderen Verbindungen Sperren nicht gemeinsam. Es muss darauf geachtet werden, dass ein Befehl einen anderen nicht blockiert, indem er Zeilen gesperrt hält, die von einem anderen Befehl angefordert werden. Wenn MARS aktiviert ist, können mehrere Befehle für die Verbindungen aktiv sein, und bei der Verwendung expliziter Transaktionen nutzen die Befehle alle eine gemeinsame Transaktion.  
  
 Der Consumer kann den Befehl abbrechen, indem er [ISSAbort::Abort](../../oledb/ole-db-interfaces/issabort-abort-ole-db.md) verwendet oder alle Verweise auf das Befehlsobjekt und das abgeleitete Rowset freigibt.  
  
 Die Verwendung von **IMultipleResults** in allen Instanzen ermöglicht es, alle Rowsets durch Befehlsausführung zu erstellen, und gestattet es Consumern zu ermitteln, wann die Befehlsausführung abgebrochen und ein Sitzungsobjekt zur Verwendung durch andere Befehle freigegeben werden sollte.  
  
> [!NOTE]  
>  Wenn Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursor verwenden, erstellt die Befehlsausführung den Cursor. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt den Erfolg oder Fehler der Cursorerstellung zurück. Der Roundtrip zur Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist damit nach der Rückkehr der Befehlsausführung abgeschlossen. Jeder Aufruf von **GetNextRows** wird dann zum Roundtrip. Auf diese Weise können mehrere Befehlsobjekte vorhanden sein, und jedes verarbeitet ein Rowset, das das Ergebnis eines Abrufs vom Servercursor ist. Weitere Informationen finden Sie unter [Rowsets und SQL Server-Cursor](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../oledb/ole-db-commands/commands.md)  
  
  
