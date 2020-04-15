---
title: 'Jet: Datum, Uhrzeit und Zeitstempelliteral | Microsoft Docs'
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299934"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: Datums-, Zeit- und Zeitstempelliterale
Für maximale Interoperabilität sollten Anwendungen Datumsliterale im canonischen ODBC-Format mithilfe der Escape-Klausel-Syntax übergeben:  
  
-   Für Datumsliterale,*value*Wert ''' ,, wobei *valu*e in der Form "yyyy-mm-dd" ist  
  
-   Für Zeitliterale, wert *"*, wobei *valu*e in der Form "hh:mm:ss" ist  
  
 Für Zeitstempelliterale 'ts '*Wert*'', wobei *valu*e in der Form "yyyy-mm-dd hh:mm:ss[.f...]" ist.
