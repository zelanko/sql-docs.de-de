---
title: 'Jet: Date, Time und Timestampliterale | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2325cd7e4a10e91f351aa2107c64c0978b843fa6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825838"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: Datums-, Zeit- und Zeitstempelliterale
Für eine optimale Interoperabilität sollten Anwendungen Datumsliterale im kanonischen ODBC-Format mithilfe der Syntax der Escape-Klausel übergeben:  
  
-   Für Datumsliterale {d '*Wert*"}, wobei *w*e hat das Format"jjjj-mm-Dd"  
  
-   Für Time-Literale {t '*Wert*"}, wobei *w*e hat das Format"hh: mm:"  
  
 Für zeitstempelliterale {ts'*Wert*"}, wobei *w*e hat das Format" jjjj-mm-tt hh: mm: [. f...] ".
