---
title: Erneutes Synchronisieren von Zeilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 44e31275a6eb3ab728d1a9d7280a3d77404f7248
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300253"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Aktualisieren von Daten in Rowsets – Erneutes Synchronisieren von Zeilen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **IRowsetResynch** nur für Cursor-unterstützte Rowsets. **IRowsetResynch** ist nicht bedarfsgesteuert verfügbar. Der Consumer muss die Schnittstelle vor dem Öffnen des Rowsets anfordern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren von Daten in Rowsets](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
