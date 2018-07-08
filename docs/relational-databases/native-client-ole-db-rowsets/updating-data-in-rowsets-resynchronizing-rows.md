---
title: Erneutes Synchronisieren von Zeilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 285ecb57e573e13816cda0d8f24f03f608b4cdaa
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413877"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Aktualisieren von Daten in Rowsets – erneutes Synchronisieren von Zeilen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt **IRowsetResynch** auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur cursorunterstützten Rowsets. **IRowsetResynch** ist nicht bei Bedarf verfügbar. Der Consumer muss die Schnittstelle vor dem Öffnen des Rowsets anfordern.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Daten in Rowsets](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
