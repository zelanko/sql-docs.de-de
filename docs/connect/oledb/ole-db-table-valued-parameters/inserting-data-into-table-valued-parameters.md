---
title: Einfügen von Daten in Tabellenwertparameter | Microsoft-Dokumentation
description: Mithilfe von OLE DB-Treiber für SQL Server zum Einfügen von Daten in Tabellenwertparameter
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, inserting data into
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: c1edbe7d411e06e477db016db62b4245e0893aee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801157"
---
# <a name="inserting-data-into-table-valued-parameters"></a>Einfügen von Daten in Tabellenwertparameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server unterstützt zwei Modelle, mit deren Hilfe der Consumer Daten für Tabellenwertparameter-Zeilen angeben kann: ein Push- und ein Pullmodell. Ein Beispiel zur Veranschaulichung des Pullmodells finden Sie unter [Programmierbeispiele für SQL Server-Daten](https://msftdpprodsamples.codeplex.com/).  
  
> [!NOTE]  
>  Eine Tabellenwertparameter-Spalte muss entweder nicht standardmäßige oder standardmäßige Werte in allen Zeilen aufweisen. Es ist nicht möglich, dass Standardwerte nur in einigen Zeilen vorhanden sind. Daher sind in Tabellenwertparameter-Bindungen die einzigen für Tabellenwertparameter-Rowsetspaltendaten zugelassenen Statuswerte DBSTATUS_S_ISNULL und DBSTATUS_S_OK. DBSTATUS_S_DEFAULT führt zu einem Fehler, und der gebundene Statuswert wird auf DBSTATUS_E_BADSTATUS festgelegt.  
  
## <a name="push-model-loads-all-table-valued-paremeter-data-in-memory"></a>Pushmodell (lädt alle Tabellenwertparameter-Daten im Arbeitsspeicher)  
 Das Pushmodell ähnelt der Verwendung von Parametersätzen (das heißt, dem DBPARAMS-Parameter in ICommand::Execute). Das Pushmodell wird nur dann verwendet, wenn Tabellenwertparameter-Rowsetobjekte ohne benutzerdefinierte Implementierung von IRowset-Schnittstellen verwendet werden. Die Verwendung des Pushmodells ist empfehlenswert, wenn die Anzahl der Zeilen im Tabellenwertparameter-Rowset gering ist und die Arbeitsspeicherauslastung für die Anwendung daher nicht allzu hoch ist. Diese Vorgehensweise ist einfacher als die des Pullmodells, da neben den aktuellen gängigen Funktionen in typischen OLE DC-Anwendungen keine zusätzlichen Funktionen der Consumeranwendung erforderlich sind.  
  
 Es wird vorausgesetzt, dass der Consumer vor der Ausführung eines Befehls alle Tabellenwertparameter-Daten für den Anbieter bereitstellt. Zum Bereitstellen der Daten füllt der Consumer ein Tabellenwertparameter-Rowsetobjekt für den Tabellenwertparameter auf. Das Tabellenwertparameter-Rowsetobjekt macht Vorgänge zum Einfügen, Festlegen und Löschen verfügbar, mit denen der Consumer die Tabellenwertparameter-Daten bearbeiten kann. Der Anbieter ruft die Daten zum Zeitpunkt der Ausführung von diesem Tabellenwertparameter-Rowsetobjekt ab.  
  
 Wenn ein Tabellenwertparameter-Rowsetobjekt für den Consumer bereitgestellt wird, kann dieser es als Rowsetobjekt verarbeiten. Der Consumer kann die jeweiligen Informationen für jede Spalte (Typ, maximale Länge, Genauigkeit und Dezimalstellen) mithilfe der Methode der Schnittstelle IColumnsInfo:: GetColumnInfo oder IColumnsRowset:: GetColumnsRowset abrufen. Der Consumer erstellt anschließend einen Accessor, um die Bindungen für die Daten anzugeben. Der nächste Schritt besteht darin, Zeilen mit Daten in das Tabellenwertparameter-Rowset einzufügen. Dies kann mithilfe von IRowsetChange:: InsertRow erfolgen. IRowsetChange:: SetData oder IRowsetChange:: DeleteRows kann auch für das Tabellenwertparameter-Rowsetobjekt verwendet werden, wenn Sie die Daten bearbeiten müssen. Tabellenwertparameter-Rowsetobjekte weisen einen Verweiszähler auf, ähnlich wie Datenstromobjekte.  
  
 Wenn IColumnsRowset:: GetColumnsRowset verwendet wird, werden nachfolgende Aufrufe von Methoden der IRowset:: GetNextRows, IRowset:: GetData und IRowset:: ReleaseRows für Rowsetobjekte der Ergebnisspalte.  
  
 Nachdem der OLE DB-Treiber für SQL Server mit der Befehlsausführung begonnen hat, werden die Tabellenwertparameter von diesem Tabellenwertparameter-Rowsetobjekt abgerufen und an den Server gesendet.  
  
 Das Pushmodell erfordert nur minimale Arbeitsschritte seitens des Consumers, es benötigt jedoch mehr Arbeitsspeicher als das Pullmodell, da sich alle Tabellenwertparameter-Daten zum Zeitpunkt der Ausführung im Arbeitsspeicher befinden müssen.  
  
## <a name="pull-model-obtaining-table-valued-parameter-data-on-demand-from-the-consumer"></a>Pullmodell (Abrufen von Tabellenwertparameter-Daten bei Bedarf vom Consumer)  
 Das Pullmodell ist für zwei Szenarien nützlich:  
  
-   Zum Streamen von Zeilen.  
  
-   Wenn ein Rowset von einem anderen Anbieter als Tabellenwertparameter-Wert verwendet wird.  
  
 Im Pullmodell stellt der Consumer nach Bedarf Daten für den Anbieter bereit. Verwenden Sie diesen Ansatz, wenn Ihre Anwendung zahlreiche Dateneinfügungen aufweist und die Tabellenwertparameter-Rowsetdaten zu einer hohen Speicherauslastung führen würden. Wenn mehrere OLE DB-Anbieter verwendet werden, ermöglicht das Consumer-Pullmodell dem Consumer, ein beliebiges Rowsetobjekt als Tabellenwertparameter-Wert bereitzustellen.  
  
 Um das Pullmodell verwenden zu können, müssen Consumer ihre eigene Implementierung eines Rowsetobjekts bereitstellen. Bei Verwendung des Pullmodells mit Tabellenwertparameter-Rowsets (CLSID_ROWSET_TVP) muss der Consumer das Tabellenwertparameter-Rowsetobjekt aggregieren, die der Anbieter verfügbar, über die ITableDefinitionWithConstraints macht:: CreateTableWithConstraints oder der IOpenRowset:: OpenRowset-Methode. Das Consumerobjekt soll nur die IRowset-Schnittstellenimplementierung überschreiben. Sie müssen die folgenden Funktionen überschreiben:  
  
-   IRowset::GetNextRows  
  
-   IRowset::AddRefRows  
  
-   IRowset::GetData  
  
-   IRowset::ReleaseRows  
  
-   IRowset::RestartPosition  
  
 Der OLE DB-Treiber für SQL Server liest jeweils eine oder mehrere Zeilen vom Rowsetobjekt des Consumers gleichzeitig, um das Streamingverhalten für Tabellenwertparameter zu unterstützen. Beispiel: Dem Benutzer liegen die Tabellenwertparameter-Rowsetdaten auf einem Datenträger (nicht im Speicher) vor, und er implementiert die Funktion zum Lesen von Daten vom Datenträger, wenn dies für den OLE DB-Treiber für SQL Server erforderlich ist.  
  
 Der Consumer kommuniziert seine Datenformat, das OLE DB-Treiber für SQL Server IAccessor:: CreateAccessor für das Tabellenwertparameter-Rowsetobjekt mit. Beim Lesen der Daten vom Consumerpuffer überprüft der Anbieter, ob alle schreibbaren, nicht standardmäßigen Spalten über mindestens ein Accessorhandle verfügbar sind, und verwendet die entsprechenden Handles zum Lesen der Spaltendaten. Um Mehrdeutigkeit zu vermeiden, sollte eine 1:1-Entsprechung zwischen einer Tabellenwertparameter-Rowset-Spalte und einer Bindung vorliegen. Doppelte Bindungen zur gleichen Spalte führen zu einem Fehler. Darüber hinaus muss jeder Accessor haben die *iOrdinal* DBBINDING angehört, in der Sequenz. Die Anzahl der Aufrufe von entspricht der Anzahl der Accessoren pro Zeile, und die Reihenfolge der Aufrufe basiert auf der Reihenfolge des *iOrdinal*-Werts von den niedrigeren zu den höheren Werten.  
  
 Es wird davon ausgegangen, dass der Anbieter die meisten der Schnittstellen implementiert, die vom Tabellenwertparameter-Rowsetobjekt verfügbar gemacht werden. Der Consumer implementiert ein Rowset-Objekt mit minimalen Schnittstellen (IRowset). Aufgrund von "blinder" Aggregation werden die verbleibenden obligatorischen Rowsetobjektschnittstellen von Tabellenwertparameter-Rowsetobjekten implementiert.  
  
 Für jedes beliebige Rowsetobjekt, wie Rowsetobjekte, die für einen beliebigen OLE DB-Anbieter abgerufen werden, muss das vom Consumer bereitgestellt Rowset alle erforderlichen Rowsetobjektschnittstellen wie in der OLE DB-Spezifikation angegeben implementieren.  
  
 Zum Zeitpunkt der Ausführung erfolgt ein Rückruf des OLE DB-Treibers für SQL Server an das Rowset-Objekt, um Zeilen abzurufen und Spaltendaten zu lesen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
