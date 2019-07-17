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
ms.openlocfilehash: 1bb7f0fb02049b6d2f1897c4f495035aee2858f6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085493"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: Datums-, Zeit- und Zeitstempelliterale
Für eine optimale Interoperabilität sollten Anwendungen Datumsliterale im kanonischen ODBC-Format mithilfe der Syntax der Escape-Klausel übergeben:  
  
-   Für Datumsliterale {d '*Wert*"}, wobei *w*e hat das Format"jjjj-mm-Dd"  
  
-   Für Time-Literale {t '*Wert*"}, wobei *w*e hat das Format"hh: mm:"  
  
 Für zeitstempelliterale {ts'*Wert*"}, wobei *w*e hat das Format" jjjj-mm-tt hh: mm: [. f...] ".
