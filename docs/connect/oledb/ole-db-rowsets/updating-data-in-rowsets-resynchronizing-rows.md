---
title: Neusynchronisierung von Zeilen | Microsoft-Dokumentation
description: Erneutes Synchronisieren von Zeilen mithilfe OLE DB Treibers für SQL Server
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
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 2f1ea1a563e986914c5fe820740776da129c3b28
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994173"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Aktualisieren von Daten in Rowsets – Erneutes Synchronisieren von Zeilen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server unterstützt **IRowsetResynch** nur für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Cursor unterstützte Rowsets. **IRowsetResynch** ist nicht bedarfsgesteuert verfügbar. Der Consumer muss die Schnittstelle vor dem Öffnen des Rowsets anfordern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren von Daten in Rowsets](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
