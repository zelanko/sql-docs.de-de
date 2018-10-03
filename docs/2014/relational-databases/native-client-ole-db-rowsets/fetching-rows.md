---
title: Abrufen von Zeilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- IRowset interface
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 5e6dbe36-b682-464d-adfa-8e886f9bd452
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21a66754a9259dadcb8788d6afef4947f9a69ad1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057830"
---
# <a name="fetching-rows"></a>Abrufen von Zeilen
  Die **IRowset**-Schnittstelle ist die grundlegende Rowset-Schnittstelle. Die **IRowset**-Schnittstelle stellt Methoden zum sequenziellen Abrufen von Zeilen, zum Kopieren der Daten aus diesen Zeilen und zum Verwalten der Zeilen bereit. Consumer verwenden die Methoden in **IRowset** für alle grundlegenden Rowsetvorgänge. Dazu gehört das Abrufen und erneute Freigeben von Zeilen und das Einlesen von Spaltenwerten.  
  
 Wenn ein Consumer einen Schnittstellenzeiger für ein Rowset erhält, besteht der erste Schritt normalerweise darin, mithilfe der Methode **IRowsetInfo::GetProperties** die Funktionen des Rowsets zu ermitteln. Auf diese Weise werden Informationen über die durch das Rowset verfügbar gemachten Schnittstellen zurückgegeben sowie über andere Möglichkeiten des Rowsets, die nicht als eigentliche Schnittstellen zu betrachten sind, wie beispielsweise die maximale Anzahl aktiver Zeilen und die Anzahl der Zeilen, die gleichzeitig ausstehende Updates aufweisen können.  
  
 Der nächste, vom Consumer auszuführende Schritt besteht darin, die Charakteristika – oder Metadaten – der Spalten im Rowset zu ermitteln. Dafür verwendet er die Methode **IColumnsInfo** zum Abrufen einfacher Informationen über die Spalten oder die Methode **IColumnsRowset** für ausführlichere Informationen. Die Methode **GetColumnInfo** gibt die folgenden Informationen zurück:  
  
-   Die Anzahl der Spalten im Resultset.  
  
-   Ein Array von DBCOLUMNINFO-Strukturen; eines pro Spalte.  
  
     Die Reihenfolge der Strukturen entspricht der Reihenfolge, in der die Spalten im Rowset erscheinen. Jede DBCOLUMNINFO-Struktur enthält Spaltenmetadaten wie den Spaltennamen, die Ordnungszahl der Spalte, maximal mögliche Länge eines Werts in der Spalte, Datentyp, Genauigkeit und Länge der Spalte.  
  
-   Den Zeiger auf einen Speicher für alle Zeichenfolgenwerte innerhalb eines einzelnen Zuordnungsblocks.  
  
 Der Consumer bestimmt, welche Spalten erforderlich sind, entweder auf der Grundlage der Metadaten oder basierend auf den Textbefehl, mit dem das Rowset generiert wurde. Die Ordnungszahlen der benötigten Spalten werden dabei entweder über die Reihenfolge der von **IColumnsInfo** zurückgegebenen Spalteninformationen oder ausgehend von den Ordnungszahlen in dem von **IColumnsRowset** zurückgegebenen Spaltenmetadatenrowset bestimmt.  
  
 Die **IColumnsInfo**-Schnittstelle und die **IColumnsRowset**-Schnittstelle werden verwendet, um Informationen über die Spalten im Rowset zu extrahieren. Die **IColumnsInfo**-Schnittstelle gibt eine beschränkte Menge von Informationen zurück, während **IColumnsRowset** alle Metadaten bereitstellt.  
  
> [!NOTE]  
>  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 und niedriger gibt die optionale Metadatenspalte DBCOLUMN_COMPUTEMODE, die von **IColumnsInfo::GetColumnsInfo** zurückgegeben wird, DBSTATUS_S_ISNULL an (anstelle der Werte, die angeben, ob die Spalte berechnet ist), da nicht ermittelt werden kann, ob die zugrunde liegende Spalte berechnet ist.  
  
 Die Ordnungszahlen werden verwendet, um eine Bindung an eine Spalte anzugeben. Eine Bindung ist eine Struktur, die einer Spalte ein Element der Struktur des Consumers zuordnet. Die Bindung kann den Datenwert, die Länge und den Statuswert der Spalte binden.  
  
 Ein Satz von Bindungen wird zusammen in einem Accessor erfasst. Dieser wird mit der Methode **IAccessor::CreateAccessor** erstellt. Ein Accessor kann mehrere Bindungen enthalten, sodass die Daten für mehrere Spalten durch einen einzigen Aufruf abgerufen oder festgelegt werden können. Der Consumer kann mehrere Accessoren erstellen, um in verschiedenen Teilen der Anwendung auf verschiedene Verwendungsmuster zu antworten. Er kann Accessoren erstellen und freigeben, solange das Rowset besteht.  
  
 Um Zeilen aus der Datenbank abzurufen, ruft der Consumer eine Methode auf, z.B. **IRowset::GetNextRows** oder **IRowsetLocate::GetRowsAt**. Diese Abrufvorgänge platzieren Zeilendaten vom Server in den Zeilenpuffer des Anbieters. Der Consumer hat keinen Direktzugriff auf den Zeilenpuffer des Anbieters. Der Consumer verwendet **IRowset::GetData**, um die Daten vom Puffer des Anbieters in den Consumerpuffer zu kopieren, und kopiert dann mithilfe von **IRowsetChange::SetData** Änderungen an den Daten vom Consumerpuffer in den Anbieterpuffer zurück.  
  
 Der Consumer ruft die Methode **GetData** auf und übergibt das Handle für eine Zeile, das Handle für einen Accessor und einen Zeiger auf den vom Consumer zugeordneten Puffer. **GetData** konvertiert die Daten und gibt die Spalten zurück, wie in den zum Erstellen des Accessors verwendeten Bindungen angegeben. Der Consumer kann **GetData** mehrere Male für eine Zeile aufrufen und dabei verschiedene Accessoren und Puffer verwenden. Daher kann der Consumer mehrere Kopien derselben Daten erhalten.  
  
 Daten aus Spalten variabler Länge können auf mehrere Arten behandelt werden. Zunächst können solche Spalten an einen endlichen Abschnitt der Struktur des Consumers gebunden werden. Dies verursacht das Abschneiden von Daten, wenn die Länge der Daten die Länge des Puffers überschreitet. Der Consumer kann ermitteln, dass Daten abgeschnitten wurden, indem er den Status DBSTATUS_S_TRUNCATED überprüft. Die zurückgegebene Länge ist immer die wirkliche Länge in Byte, sodass der Consumer auch bestimmen kann, wie viele Daten abgeschnitten wurden.  
  
 Wenn der Consumer das Abrufen oder Aktualisieren der Zeilen abgeschlossen hat, gibt er sie mit der Methode **ReleaseRows** wieder frei. Auf diese Weise werden Ressourcen von der Kopie der Zeilen im Rowset frei, und es wird Platz für neue Zeilen geschaffen. Der Consumer kann den Zyklus des Abrufens oder Erstellens von Zeilen sowie des Zugreifens auf Daten in den Zeilen beliebig wiederholen.  
  
 Wenn der Consumer mit dem Rowset fertig ist, ruft er die Methode **IAccessor::ReleaseAccessor** auf, um, falls nötig, Accessoren freizugeben. Er ruft die Methode **IUnknown::Release** auf allen Schnittstellen auf, die vom Rowset verfügbar gemacht worden sind, um das Rowset wieder freizugeben. Sobald das Rowset freigegeben ist, wird die Freigabe aller verbleibender Zeilen oder vom Consumer verwendeten Accessoren erzwungen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Nächste Abrufposition](fetching-rows-next-fetch-position.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](rowsets.md)  
  
  
