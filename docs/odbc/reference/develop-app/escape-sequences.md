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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298710"
---
# <a name="escape-sequences"></a>Escapesequenzen
ODBC definiert Escapesequenzen, die Standardgrammatik für Datums-, Uhrzeit-, Zeitstempel- und **LIKE** Datumszeitintervallliterale, skalare Funktionsaufrufe, LIKE-Prädikat-Escapezeichen, äußere Verknüpfungen und Prozeduraufrufe enthalten. Interoperable Anwendungen sollten diese Sequenzen nach Möglichkeit verwenden.  
  
 Um zu ermitteln, ob ein Treiber die Escapesequenzen für Datums-, Uhrzeit-, Zeitstempel- oder Datumszeitintervallliterale unterstützt, ruft eine Anwendung **SQLGetTypeInfo**auf. Wenn die Datenquelle einen Datentyp für Datums-, Uhrzeit-, Zeitstempel- oder Datumszeitintervalle unterstützt, muss sie auch die entsprechende Escapesequenz unterstützen. Um zu bestimmen, ob die anderen Escapesequenzen unterstützt werden, ruft eine Anwendung **SQLGetInfo**auf.  
  
 Weitere Informationen finden Sie unter [Escape-Sequenzen in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md), weiter unten in diesem Abschnitt.
