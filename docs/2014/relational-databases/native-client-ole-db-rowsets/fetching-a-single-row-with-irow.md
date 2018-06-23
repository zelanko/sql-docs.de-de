---
title: Abrufen einer einzelnen Zeile mit IRow | Microsoft Docs
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
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eef27a6cbd6ee793cd227c2cf6e6570e1d04b004
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150346"
---
# <a name="fetching-a-single-row-with-irow"></a>Abrufen einer einzelnen Zeile mit IRow
  Die **IRow** -schnittstellenimplementierung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wurde vereinfacht, um die Leistung zu steigern. **IRow** ermöglicht den direkten Zugriff auf Spalten eines einzelnen Zeilenobjekts. Wenn Sie vorab wissen, dass das Ergebnis einer befehlsausführung genau eine Zeile erzeugt **IRow** werden die Spalten dieser Zeile abgerufen. Wenn das Resultset mehrere Zeilen umfasst **IRow** nur die erste Zeile verfügbar.  
  
 Die **IRow** -Implementierung lässt keine Navigation in der Zeile. Mit folgender Ausnahme wird auf jede Spalte der Zeile nur ein einziges Mal zugegriffen: Einmal kann zur Ermittlung der Spaltenbreite auf eine Spalte zugegriffen werden, und dann kann nochmals zum Abruf der Daten auf die Spalte zugegriffen werden.  
  
> [!NOTE]  
>  **IRow:: Open** unterstützt nur Typs DBGUID_STREAM und DBGUID_NULL von Objekten, die geöffnet werden.  
  
 Um ein Zeilenobjekt mithilfe erhalten **ICommand:: Execute** Methode IID_IRow übergeben werden muss. Die **IMultipleResults** Schnittstelle muss verwendet werden, um mehrere Resultsets verarbeiten. **IMultipleResults** unterstützt **IRow** und **IRowset**. **IRowset** für Massenvorgänge verwendet wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von IRow::GetColumns](using-irow-getcolumns.md)  
  
-   [Abrufen von BLOB-Daten mit IRow](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](rowsets.md)  
  
  