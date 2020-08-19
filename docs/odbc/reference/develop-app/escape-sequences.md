---
description: Escapesequenzen
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
ms.openlocfilehash: 15c06fc08d78422502b8aea87c40ee2821a9620f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429302"
---
# <a name="escape-sequences"></a>Escapesequenzen
ODBC definiert Escapesequenzen mit der Standard Grammatik für Datums-, Uhrzeit-, timestamp-und DateTime-Intervall Literale, skalare Funktionsaufrufe, **wie** Prädikat-Escapezeichen, äußere Joins und Prozedur Aufrufe. Interoperable Anwendungen sollten diese Sequenzen verwenden, wann immer dies möglich ist.  
  
 Um festzustellen, ob ein Treiber die Escapesequenzen für Datums-, Uhrzeit-, Timestamp-oder DateTime-Intervall Literale unterstützt, ruft eine Anwendung **SQLGetTypeInfo**auf. Wenn die Datenquelle einen Datums-, Uhrzeit-, Timestamp-oder DateTime-Intervall Datentyp unterstützt, muss Sie auch die entsprechende Escapesequenz unterstützen. Um zu ermitteln, ob die anderen Escapesequenzen unterstützt werden, ruft eine Anwendung **SQLGetInfo**auf.  
  
 Weitere Informationen finden Sie unter Escapesequenzen [in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)weiter unten in diesem Abschnitt.
