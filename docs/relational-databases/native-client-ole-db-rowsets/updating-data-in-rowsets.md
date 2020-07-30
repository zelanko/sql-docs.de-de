---
title: Aktualisieren von Daten in Rowsets (Native Client OLE DB-Anbieter)
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 34a2aeb4a6b971e196dd876a8bade429afddc792
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87393800"
---
# <a name="updating-data-in-rowsets-in-sql-server-native-client"></a>Aktualisieren von Daten in Rowsets in SQL Server Native Client
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter aktualisiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten, wenn ein Consumer ein änderbares Rowset aktualisiert, das diese Daten enthält. Ein modifizierbares Rowset wird erstellt, wenn der Consumer entweder für die **IRowsetChange**-Schnittstelle oder die **IRowsetUpdate**-Schnittstelle Unterstützung anfordert.  
  
 Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Native Client OLE DB vom Anbieter änderbaren Rowsets verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cursor zur Unterstützung des Rowsets. Die Rowseteigenschaft DBPROP_LOCKMODE ändert das Parallelitätskontrollverhalten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bei Cursorn und bestimmt das Verhalten für den Zeilenabruf bei Rowsets sowie die Fehlergenerierung in Bezug auf die Datenintegrität in aktualisierbaren Rowsets.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die Zeilen Synchronisierung vor oder nach einem Update.  
  
> [!NOTE]  
>  IRowChange::SetColumns ist verfügbar, um die Werte mindestens einer benannten Spalte eines Zeilenobjekts festzulegen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aktualisieren von Daten in SQL Server-Cursorn](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Erneutes Synchronisieren von Zeilen](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
