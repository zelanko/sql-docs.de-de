---
title: Aktualisieren von Daten in Rowsets | Microsoft-Dokumentation
description: Aktualisieren von Daten in Rowsets mit dem OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, updating data
- OLE DB Driver for SQL Server, data updates
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: pelopes
ms.openlocfilehash: e19128d6defa2c154cc8bddbcc4bcaa761b58a2b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015337"
---
# <a name="updating-data-in-rowsets"></a>Aktualisieren von Daten in Rowsets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server aktualisiert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Daten, wenn ein Consumer ein modifizierbares Rowset aktualisiert, das diese Daten enthält. Ein modifizierbares Rowset wird erstellt, wenn der Consumer entweder für die **IRowsetChange**-Schnittstelle oder die **IRowsetUpdate**-Schnittstelle Unterstützung anfordert.  
  
 Alle vom OLE DB-Treiber für SQL Server modifizierbaren Rowsets verwenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursor zur Unterstützung des Rowsets. Die Rowseteigenschaft DBPROP_LOCKMODE ändert das Parallelitätskontrollverhalten von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bei Cursorn und bestimmt das Verhalten für den Zeilenabruf bei Rowsets sowie die Fehlergenerierung in Bezug auf die Datenintegrität in aktualisierbaren Rowsets.  
  
 Der OLE DB-Treiber für SQL Server unterstützt die Zeilensynchronisierung vor oder nach einem Update.  
  
> [!NOTE]  
>  IRowChange::SetColumns ist verfügbar, um die Werte mindestens einer benannten Spalte eines Zeilenobjekts festzulegen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aktualisieren von Daten in SQL Server-Cursorn](../../oledb/ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Erneutes Synchronisieren von Zeilen](../../oledb/ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
