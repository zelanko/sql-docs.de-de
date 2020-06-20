---
title: Erneutes Synchronisieren von Zeilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: rothja
ms.author: jroth
ms.openlocfilehash: 47c628ae583f3e635f422d5146f64508372a1114
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011205"
---
# <a name="resynchronizing-rows"></a>Erneutes Synchronisieren von Zeilen
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt **IRowsetResynch** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur für Cursor unterstützte Rowsets. **IRowsetResynch** ist nicht bedarfsgesteuert verfügbar. Der Consumer muss die Schnittstelle vor dem Öffnen des Rowsets anfordern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren von Daten in Rowsets](updating-data-in-rowsets.md)  
  
  
