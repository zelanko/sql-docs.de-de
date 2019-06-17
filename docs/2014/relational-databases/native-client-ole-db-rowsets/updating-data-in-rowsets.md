---
title: Aktualisieren von Daten in Rowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f68e4f2be641d6c6aeaf8bbbfcc8cad81ab1a39a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62938681"
---
# <a name="updating-data-in-rowsets"></a>Aktualisieren von Daten in Rowsets
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter aktualisiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten, wenn ein Consumer ein Modifizierbares Rowset aktualisiert, die die Daten enthält. Ein modifizierbares Rowset wird erstellt, wenn der Consumer entweder für die **IRowsetChange**-Schnittstelle oder die **IRowsetUpdate**-Schnittstelle Unterstützung anfordert.  
  
 Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter modifizierbare Rowsets verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Cursor zur Unterstützung des Rowsets. Die Rowseteigenschaft DBPROP_LOCKMODE ändert das Parallelitätskontrollverhalten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bei Cursorn und bestimmt das Verhalten für den Zeilenabruf bei Rowsets sowie die Fehlergenerierung in Bezug auf die Datenintegrität in aktualisierbaren Rowsets.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die zeilensynchronisierung vor oder nach einem Update.  
  
> [!NOTE]  
>  IRowChange::SetColumns ist verfügbar, um die Werte mindestens einer benannten Spalte eines Zeilenobjekts festzulegen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aktualisieren von Daten in SQL Server-Cursorn](updating-data-in-sql-server-cursors.md)  
  
-   [Erneutes Synchronisieren von Zeilen](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](rowsets.md)  
  
  
