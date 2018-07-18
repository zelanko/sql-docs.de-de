---
title: Aktualisieren von Daten in Rowsets | Microsoft Docs
description: Aktualisieren von Daten in Rowsets, die mithilfe von OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, updating data
- OLE DB Driver for SQL Server, data updates
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 009c6023dc1905ac724287790c1b26a4bfcf87d3
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689903"
---
# <a name="updating-data-in-rowsets"></a>Aktualisieren von Daten in Rowsets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server-Updates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Daten, wenn ein Consumer ein Modifizierbares Rowset aktualisiert, die die Daten enthält. Ein Modifizierbares Rowset wird erstellt, wenn der Consumer Unterstützung für entweder fordert die **IRowsetChange** oder **IRowsetUpdate** Schnittstelle.  
  
 Alle OLE DB-Treiber für SQL Server modifizierbare Rowsets verwenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Cursor zur Unterstützung des Rowsets. Die Rowseteigenschaft DBPROP_LOCKMODE ändert das Parallelitätskontrollverhalten von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bei Cursorn und bestimmt das Verhalten für den Zeilenabruf bei Rowsets sowie die Fehlergenerierung in Bezug auf die Datenintegrität in aktualisierbaren Rowsets.  
  
 Der OLE DB-Treiber für SQL Server unterstützt die zeilensynchronisierung vor oder nach einem Update.  
  
> [!NOTE]  
>  IRowChange::SetColumns ist verfügbar, um die Werte mindestens einer benannten Spalte eines Zeilenobjekts festzulegen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aktualisieren von Daten in SQL Server-Cursorn](../../oledb/ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Erneutes Synchronisieren von Zeilen](../../oledb/ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
