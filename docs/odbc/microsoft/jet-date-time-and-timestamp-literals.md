---
title: 'Jet: Datums-, Uhrzeit-und Zeitstempel Literale | Microsoft-Dokumentation'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 372b7c1dab1ad8ff000fb88729c3b02e05d4a21c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299934"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: Datums-, Zeit- und Zeitstempelliterale
Für maximale Interoperabilität sollten Anwendungen Datums Literale im kanonischen ODBC-Format mithilfe der escapeklausel-Syntax übergeben:  
  
-   Für Datums Literale {d '*value*'}, wobei *Valu*e das Format "yyyy-mm-dd" hat.  
  
-   Für Zeit Literale {t '*value*'}, wobei *Valu*e im Format ' HH: mm: SS ' liegt.  
  
 Für Zeitstempel-Literale {TS '*value*'}, wobei *Valu*e das Format ' yyyy-mm-dd hh: mm: SS [. f...] ' aufweist.
