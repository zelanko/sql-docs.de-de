---
title: Vergleichbarkeit für ' irowsetfind ' | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability [ODBC]
ms.assetid: 7d148b56-9bbe-4e55-b31f-43f115705402
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9aa8cb118a84bca1d37bdd409055b21d1d11552
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63233029"
---
# <a name="comparability-for-irowsetfind"></a>Vergleichbarkeit für 'IRowsetFind'
  Für die date/time-Typen unterstützt IRowsetFind die folgenden Vergleiche:  
  
-   LT  
  
-   LE  
  
-   EQ  
  
-   GE  
  
-   GT  
  
-   NE  
  
-   IGNORE  
  
 Bei dem Versuch eines anderen Vergleichs wird DB_E_BADCOMPAREOP zurückgegeben. Dieses Verhalten stimmt mit der OLE DB-Spezifikation überein.  
  
## <a name="see-also"></a>Siehe auch  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](date-and-time-improvements-ole-db.md)  
  
  
