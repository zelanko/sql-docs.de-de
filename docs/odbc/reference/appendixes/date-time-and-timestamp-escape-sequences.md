---
title: Datum, Uhrzeit und Zeitstempel-Escape-Sequenzen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC]
- escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC]
ms.assetid: 67b7dee0-e5b1-4469-a626-0c7767852b80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6cbcdac00b4cd7497f53c9f3a13f4f7303b5154
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284342"
---
# <a name="date-time-and-timestamp-escape-sequences"></a>Datums-, Uhrzeit- und Zeitstempel-Escapesequenzen
ODBC definiert Escapesequenzen für Datums-, Uhrzeit- und Zeitstempelliterale. Die Syntax dieser Escapesequenzen ist wie folgt:  
  
```  
  
{d 'value'}  
{t 'value'}  
{ts 'value'}  
```  
  
 In der BNF-Notation ist die Syntax wie folgt:  
  
```  
  
      ODBC-date-time-escape ::=  
     ODBC-date-escape  
     | ODBC-time-escape  
     | ODBC-timestamp-escapeODBC-date-escape ::=  
     ODBC-esc-initiator d 'date-value' ODBC-esc-terminatorODBC-time-escape ::=  
     ODBC-esc-initiator t 'time-value' ODBC-esc-terminatorODBC-timestamp-escape ::=  
     ODBC-esc-initiator ts 'timestamp-value' ODBC-esc-terminatorODBC-esc-initiator ::= {  
ODBC-esc-terminator ::= }  
date-value ::=   
     years-value date-separator months-value date-separator days-valuetime-value ::=   
     hours-value time-separator minutes-value time-separatorseconds-valuetimestamp-value ::= date-value timestamp-separator time-valuedate-separator ::= -  
time-separator ::= :  
timestamp-separator ::=  
     (The blank character)years-value ::= digit digit digit digitmonths-value ::= digit digitdays-value ::= digit digithours-value ::= digit digitminutes-value ::= digit digitseconds-value ::= digit digit[.digit...]  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Die Literalescape-Escapesequenzen datum, zeit und zeitstempel werden unterstützt, wenn die Datentypen Datum, Uhrzeit und Zeitstempel von der Datenquelle unterstützt werden. Eine Anwendung sollte **SQLGetTypeInfo** aufrufen, um zu bestimmen, ob diese Datentypen unterstützt werden.
