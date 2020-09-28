---
title: Erneutes Synchronisieren von Zeilen (OLE DB-Treiber)
description: Für die Aktualisierung von Daten in Rowsets unterstützt der OLE DB-Treiber für SQL Server nur IRowsetResynch für Rowsets, die vom SQL Server-Cursor unterstützt werden.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 65ae67a91fc7fb5f3caaa341dbfcb00dc2e5d796
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859965"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Aktualisieren von Daten in Rowsets – Erneutes Synchronisieren von Zeilen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Im OLE DB-Treiber für SQL ist **IRowsetResynch** nur bei durch Cursor unterstützten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Rowsets verfügbar. **IRowsetResynch** ist nicht bedarfsgesteuert verfügbar. Der Consumer muss die Schnittstelle vor dem Öffnen des Rowsets anfordern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren von Daten in Rowsets](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
