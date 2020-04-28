---
title: Escapesequenzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5d9589230183b198cb7d59cf9739dab75625441e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298710"
---
# <a name="escape-sequences"></a>Escapesequenzen
ODBC definiert Escapesequenzen mit der Standard Grammatik für Datums-, Uhrzeit-, timestamp-und DateTime-Intervall Literale, skalare Funktionsaufrufe, **wie** Prädikat-Escapezeichen, äußere Joins und Prozedur Aufrufe. Interoperable Anwendungen sollten diese Sequenzen verwenden, wann immer dies möglich ist.  
  
 Um festzustellen, ob ein Treiber die Escapesequenzen für Datums-, Uhrzeit-, Timestamp-oder DateTime-Intervall Literale unterstützt, ruft eine Anwendung **SQLGetTypeInfo**auf. Wenn die Datenquelle einen Datums-, Uhrzeit-, Timestamp-oder DateTime-Intervall Datentyp unterstützt, muss Sie auch die entsprechende Escapesequenz unterstützen. Um zu ermitteln, ob die anderen Escapesequenzen unterstützt werden, ruft eine Anwendung **SQLGetInfo**auf.  
  
 Weitere Informationen finden Sie unter Escapesequenzen [in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)weiter unten in diesem Abschnitt.
