---
title: Abrufen einer einzelnen Zeile mit IRow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
author: rothja
ms.author: jroth
ms.openlocfilehash: b5573fe1fef39f29329e373323f5f8aaf15f2c58
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055958"
---
# <a name="fetching-a-single-row-with-irow"></a>Abrufen einer einzelnen Zeile mit IRow
  Die Implementierung der **IRow** -Schnittstelle im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird vereinfacht, um die Leistung zu verbessern. **IRow** lässt den direkten Zugriff auf Spalten eines einzelnen Zeilenobjekts zu. Wenn Sie vorab wissen, dass das Ergebnis einer Befehlsausführung genau eine Zeile erzeugt, dann lassen sich mit **IRow** die Spalten dieser Zeile abrufen. Wenn das Resultset mehrere Zeilen umfasst, macht **IRow** nur die erste Zeile verfügbar.  
  
 Die **IRow**-Implementierung lässt keine Navigation in der Zeile zu. Mit folgender Ausnahme wird auf jede Spalte der Zeile nur ein einziges Mal zugegriffen: Einmal kann zur Ermittlung der Spaltenbreite auf eine Spalte zugegriffen werden, und dann kann nochmals zum Abruf der Daten auf die Spalte zugegriffen werden.  
  
> [!NOTE]  
>  **IRow::Open** unterstützt nur das Öffnen von Objekten des Typs DBGUID_STREAM und DBGUID_NULL.  
  
 IID_IRow muss übergeben werden, um ein Zeilenobjekt mithilfe der **ICommand::Execute**-Methode zu erhalten. Die **IMultipleResults**-Schnittstelle muss zur Behandlung mehrerer Resultsets verwendet werden. **IMultipleResults** unterstützt **IRow** und **IRowset**. **IRowset** wird für Massenvorgänge verwendet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von IRow::GetColumns](using-irow-getcolumns.md)  
  
-   [Abrufen von BLOB-Daten mit IRow](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](rowsets.md)  
  
  
