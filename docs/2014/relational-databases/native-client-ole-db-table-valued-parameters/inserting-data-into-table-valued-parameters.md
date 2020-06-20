---
title: Einfügen von Daten in Tabellenwertparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, inserting data into
ms.assetid: 9c1a3234-4675-40d3-b473-8df06208f880
author: rothja
ms.author: jroth
ms.openlocfilehash: f8685b5180d4c8dc91d0199030ecd04fdcbec994
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039015"
---
# <a name="inserting-data-into-table-valued-parameters"></a>Einfügen von Daten in Tabellenwertparameter
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt zwei Modelle für den Consumer, um Daten für Tabellenwert Parameter-Zeilen anzugeben: ein Push-Modell und ein Pull-Modell. Ein Beispiel zur Veranschaulichung des Pullmodells finden Sie unter [Programmierbeispiele für SQL Server-Daten](https://msftdpprodsamples.codeplex.com/).  
  
> [!NOTE]  
>  Eine Tabellenwertparameter-Spalte muss entweder nicht standardmäßige oder standardmäßige Werte in allen Zeilen aufweisen. Es ist nicht möglich, dass Standardwerte nur in einigen Zeilen vorhanden sind. Daher sind in Tabellenwertparameter-Bindungen die einzigen für Tabellenwertparameter-Rowsetspaltendaten zugelassenen Statuswerte DBSTATUS_S_ISNULL und DBSTATUS_S_OK. DBSTATUS_S_DEFAULT führt zu einem Fehler, und der gebundene Statuswert wird auf DBSTATUS_E_BADSTATUS festgelegt.  
  
## <a name="push-model-loads-all-table-valued-paremeter-data-in-memory"></a>Pushmodell (lädt alle Tabellenwertparameter-Daten im Arbeitsspeicher)  
 Das Pushmodell ähnelt der Verwendung von Parametersätzen (das heißt, dem DBPARAMS-Parameter in ICommand::Execute). Das Pushmodell wird nur dann verwendet, wenn Tabellenwertparameter-Rowsetobjekte ohne benutzerdefinierte Implementierung von IRowset-Schnittstellen verwendet werden. Die Verwendung des Pushmodells ist empfehlenswert, wenn die Anzahl der Zeilen im Tabellenwertparameter-Rowset gering ist und die Arbeitsspeicherauslastung für die Anwendung daher nicht allzu hoch ist. Diese Vorgehensweise ist einfacher als die des Pullmodells, da neben den aktuellen gängigen Funktionen in typischen OLE DC-Anwendungen keine zusätzlichen Funktionen der Consumeranwendung erforderlich sind.  
  
 Es wird vorausgesetzt, dass der Consumer vor der Ausführung eines Befehls alle Tabellenwertparameter-Daten für den Anbieter bereitstellt. Zum Bereitstellen der Daten füllt der Consumer ein Tabellenwertparameter-Rowsetobjekt für den Tabellenwertparameter auf. Das Tabellenwertparameter-Rowsetobjekt macht Vorgänge zum Einfügen, Festlegen und Löschen verfügbar, mit denen der Consumer die Tabellenwertparameter-Daten bearbeiten kann. Der Anbieter ruft die Daten zum Zeitpunkt der Ausführung von diesem Tabellenwertparameter-Rowsetobjekt ab.  
  
 Wenn ein Tabellenwertparameter-Rowsetobjekt für den Consumer bereitgestellt wird, kann dieser es als Rowsetobjekt verarbeiten. Der Consumer kann mithilfe der Schnittstellenmethoden „IColumnsInfo::GetColumnInfo“ oder „IColumnsRowset::GetColumnsRowset“ die Typinformationen für jede Spalte (Typ, maximale Länge, Genauigkeit und Dezimalstellen) abfragen. Der Consumer erstellt anschließend einen Accessor, um die Bindungen für die Daten anzugeben. Der nächste Schritt besteht darin, Zeilen mit Daten in das Tabellenwertparameter-Rowset einzufügen. Hierzu können Sie IRowsetChange::InsertRow verwenden. Die Schnittstellen „IRowsetChange::SetData“ und „IRowsetChange::DeleteRows“ können auch für das Rowsetobjekt für Tabellenwertparameter verwendet werden, wenn Sie die Daten bearbeiten müssen. Tabellenwertparameter-Rowsetobjekte weisen einen Verweiszähler auf, ähnlich wie Datenstromobjekte.  
  
 Wenn IColumnsRowset::GetColumnsRowset verwendet wird, werden die Methoden „IRowset::GetNextRows“, „IRowset::GetData“ und „IRowset::ReleaseRows“ für das Rowsetobjekt der Ergebnisspalte aufgerufen.  
  
 Nachdem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter mit dem Ausführen des Befehls begonnen hat, werden die Tabellenwert Parameter-Werte aus diesem Tabellenwert Parameter-Rowsetobjekt abgerufen und an den Server gesendet.  
  
 Das Pushmodell erfordert nur minimale Arbeitsschritte seitens des Consumers, es benötigt jedoch mehr Arbeitsspeicher als das Pullmodell, da sich alle Tabellenwertparameter-Daten zum Zeitpunkt der Ausführung im Arbeitsspeicher befinden müssen.  
  
## <a name="pull-model-obtaining-table-valued-parameter-data-on-demand-from-the-consumer"></a>Pullmodell (Abrufen von Tabellenwertparameter-Daten bei Bedarf vom Consumer)  
 Das Pullmodell ist für zwei Szenarien nützlich:  
  
-   Zum Streamen von Zeilen.  
  
-   Wenn ein Rowset von einem anderen Anbieter als Tabellenwertparameter-Wert verwendet wird.  
  
 Im Pullmodell stellt der Consumer nach Bedarf Daten für den Anbieter bereit. Verwenden Sie diesen Ansatz, wenn Ihre Anwendung zahlreiche Dateneinfügungen aufweist und die Tabellenwertparameter-Rowsetdaten zu einer hohen Speicherauslastung führen würden. Wenn mehrere OLE DB-Anbieter verwendet werden, ermöglicht das Consumer-Pullmodell dem Consumer, ein beliebiges Rowsetobjekt als Tabellenwertparameter-Wert bereitzustellen.  
  
 Um das Pullmodell verwenden zu können, müssen Consumer ihre eigene Implementierung eines Rowsetobjekts bereitstellen. Beim Verwenden des Pullmodells mit Rowsets für Tabellenwertparameter (CLSID_ROWSET_TVP) muss der Consumer das Rowsetobjekt für Tabellenwertparameter aggregieren, das der Anbieter mithilfe der Methoden „ITableDefinitionWithConstraints::CreateTableWithConstraints“ oder „IOpenRowset::OpenRowset“ verfügbar macht. Das Consumerobjekt soll nur die IRowset-Schnittstellenimplementierung überschreiben. Sie müssen die folgenden Funktionen überschreiben:  
  
-   IRowset::GetNextRows  
  
-   IRowset::AddRefRows  
  
-   IRowset::GetData  
  
-   IRowset::ReleaseRows  
  
-   IRowset::RestartPosition  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter liest jeweils eine oder mehrere Zeilen vom Rowsetobjekt des Consumers gleichzeitig, um das Streamingverhalten für Tabellenwertparameter zu unterstützen. Ein Beispiel: Dem Benutzer liegen die Tabellenwertparameter-Rowsetdaten auf einem Datenträger (nicht im Speicher) vor, und er implementiert die Funktion zum Lesen von Daten vom Datenträger, wenn dies für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erforderlich ist.  
  
 Der Consumer kommuniziert das Datenformat an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Native Client OLE DB-Anbieter, indem er IAccessor:: deateaccessor für das Tabellenwert Parameter-Rowsetobjekt verwendet. Beim Lesen der Daten vom Consumerpuffer überprüft der Anbieter, ob alle schreibbaren, nicht standardmäßigen Spalten über mindestens ein Accessorhandle verfügbar sind, und verwendet die entsprechenden Handles zum Lesen der Spaltendaten. Um Mehrdeutigkeit zu vermeiden, sollte eine 1:1-Entsprechung zwischen einer Tabellenwertparameter-Rowset-Spalte und einer Bindung vorliegen. Doppelte Bindungen zur gleichen Spalte führen zu einem Fehler. Es wird außerdem davon ausgegangen, dass jeder Accessor über das Element *iOrdinal* von DBBindings in der Sequenz verfügt. Die Anzahl der Aufrufe von entspricht der Anzahl der Accessoren pro Zeile, und die Reihenfolge der Aufrufe basiert auf der Reihenfolge des *iOrdinal*-Werts von den niedrigeren zu den höheren Werten.  
  
 Es wird davon ausgegangen, dass der Anbieter die meisten der Schnittstellen implementiert, die vom Tabellenwertparameter-Rowsetobjekt verfügbar gemacht werden. Der Consumer implementiert ein Rowset-Objekt mit minimalen Schnittstellen (IRowset). Aufgrund von "blinder" Aggregation werden die verbleibenden obligatorischen Rowsetobjektschnittstellen von Tabellenwertparameter-Rowsetobjekten implementiert.  
  
 Für jedes beliebige Rowsetobjekt, wie Rowsetobjekte, die für einen beliebigen OLE DB-Anbieter abgerufen werden, muss das vom Consumer bereitgestellt Rowset alle erforderlichen Rowsetobjektschnittstellen wie in der OLE DB-Spezifikation angegeben implementieren.  
  
 Zum Zeitpunkt der Ausführung erfolgt ein Rückruf des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters an das Rowsetobjekt, um Zeilen abzurufen und Spaltendaten zu lesen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwert Parameter &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
