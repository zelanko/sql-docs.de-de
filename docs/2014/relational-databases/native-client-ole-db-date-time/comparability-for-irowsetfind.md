---
title: Vergleichbarkeit für IRowsetFind | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability [ODBC]
ms.assetid: 7d148b56-9bbe-4e55-b31f-43f115705402
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e7978cc2cfeaa369d813c07fa618aac3303f767
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011227"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](date-and-time-improvements-ole-db.md)  
  
  
