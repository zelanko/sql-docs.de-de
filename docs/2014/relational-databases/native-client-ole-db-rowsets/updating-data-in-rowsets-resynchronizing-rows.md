---
title: Neusynchronisierung von Zeilen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b041dc07afb30fff0c03d96fec9cd8a5d62f965
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63229012"
---
# <a name="resynchronizing-rows"></a>Erneutes Synchronisieren von Zeilen
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt **IRowsetResynch** nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cursor unterstützte Rowsets. **Irowantresynch** ist bei Bedarf nicht verfügbar. Der Consumer muss die Schnittstelle vor dem Öffnen des Rowsets anfordern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren von Daten in Rowsets](updating-data-in-rowsets.md)  
  
  
