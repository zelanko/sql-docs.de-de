---
title: Aktualisieren von Daten in Rowsets | Microsoft-Dokumentation
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
ms.openlocfilehash: 3fed7625eb909327688d7777291b28c7a102dbf6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300221"
---
# <a name="updating-data-in-rowsets"></a>Aktualisieren von Daten in Rowsets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter aktualisiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten, wenn ein Consumer ein veränderbares Rowset aktualisiert, das diese Daten enthält. Ein modifizierbares Rowset wird erstellt, wenn der Consumer entweder für die **IRowsetChange**-Schnittstelle oder die **IRowsetUpdate**-Schnittstelle Unterstützung anfordert.  
  
 Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] systemeigenen OLE DB-Anbieter-modifizierbaren Rowsets verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cursor, um das Rowset zu unterstützen. Die Rowseteigenschaft DBPROP_LOCKMODE ändert das Parallelitätskontrollverhalten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bei Cursorn und bestimmt das Verhalten für den Zeilenabruf bei Rowsets sowie die Fehlergenerierung in Bezug auf die Datenintegrität in aktualisierbaren Rowsets.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt die Zeilensynchronisierung vor oder nach einer Aktualisierung.  
  
> [!NOTE]  
>  IRowChange::SetColumns ist verfügbar, um die Werte mindestens einer benannten Spalte eines Zeilenobjekts festzulegen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aktualisieren von Daten in SQL Server-Cursorn](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Erneutes Synchronisieren von Zeilen](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
