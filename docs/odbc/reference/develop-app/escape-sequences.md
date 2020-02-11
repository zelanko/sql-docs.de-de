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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d73282cde4d0598d7e6a35ac6273935626b96969
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001372"
---
# <a name="escape-sequences"></a>Escapesequenzen
ODBC definiert Escapesequenzen mit der Standard Grammatik für Datums-, Uhrzeit-, timestamp-und DateTime-Intervall Literale, skalare Funktionsaufrufe, **wie** Prädikat-Escapezeichen, äußere Joins und Prozedur Aufrufe. Interoperable Anwendungen sollten diese Sequenzen verwenden, wann immer dies möglich ist.  
  
 Um festzustellen, ob ein Treiber die Escapesequenzen für Datums-, Uhrzeit-, Timestamp-oder DateTime-Intervall Literale unterstützt, ruft eine Anwendung **SQLGetTypeInfo**auf. Wenn die Datenquelle einen Datums-, Uhrzeit-, Timestamp-oder DateTime-Intervall Datentyp unterstützt, muss Sie auch die entsprechende Escapesequenz unterstützen. Um zu ermitteln, ob die anderen Escapesequenzen unterstützt werden, ruft eine Anwendung **SQLGetInfo**auf.  
  
 Weitere Informationen finden Sie unter Escapesequenzen [in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)weiter unten in diesem Abschnitt.
