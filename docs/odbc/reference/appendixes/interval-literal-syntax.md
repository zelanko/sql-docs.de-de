---
title: Intervall Literal-Syntax | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], interval
- interval literals [ODBC]
- ODBC literals [ODBC], interval
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d477dbc6b54d7ebd82b7e2ef8611f5f6dd807e83
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188814"
---
# <a name="interval-literal-syntax"></a>Syntax von Intervallliteralen
Die folgende Syntax wird für Intervall-Literale in ODBC verwendet.  
  
 *Intervall-Literals:: = Intervall* [+ *&#124;* -] *Interval-Zeichenfolge Intervall-Qualifizierer*  
  
 *interval-string* ::= *quote* { *year-month-literal* &#124; *day-time-literal* } *quote*  
  
 *year-month-literal* ::= *years-value* &#124; [*years-value* -] *months-value*  
  
 *day-time-literal* ::= *day-time-interval* &#124; *time-interval*  
  
 *Tag-Zeitintervall* :: = *Wert Tage* [*Stundenwert* [:*Minutenwert*[:*Sekundenwert*]]]  
  
 *Zeitintervall* :: = *Stundenwert* [:*Minutenwert* [:*Sekundenwert* ]]  
  
 &#124;*Minutenwert* [:*Sekundenwert* ]  
  
 &#124; *seconds-value*  
  
 *years-value* ::= *datetime-value*  
  
 *months-value* ::= *datetime-value*  
  
 *days-value* ::= *datetime-value*  
  
 *Wert für die Stunden* :: = *Datetime-Wert*  
  
 *minutes-value* ::= *datetime-value*  
  
 *Wert für die Sekunden* :: = *Sekunden Ganzzahlwert* [. [ *Sekundenbruchteils*]]  
  
 *seconds-integer-value* ::= *unsigned-integer*  
  
 *seconds-fraction* ::= *unsigned-integer*  
  
 *datetime-value* ::= *unsigned-integer*  
  
 *interval-qualifier* ::= *start-field* TO *end-field* &#124; *single-datetime-field*  
  
 *Start-Feld* :: = *nicht-Sekunde-Datetime-Feld* [(*Intervall führende-Feld-mit einfacher Genauigkeit* )]  
  
 *end-field* ::= *non-second-datetime-field* &#124; SECOND[(*interval-fractional-seconds-precision*)]  
  
 *Single-Datetime-Feld* :: = *nicht-Sekunde-Datetime-Feld* [(*Intervall führende-Feld-mit einfacher Genauigkeit*)] &#124; zweite [(*Intervall führende-Feld-mit einfacher Genauigkeit*  [, (*Intervall--Sekunden-sekundenbruchteilgenauigkeit*)]  
  
 *datetime-field* ::= *non-second-datetime-field* &#124; SECOND  
  
 *nicht-Sekunde-Datetime-Feld* :: = Jahr &#124; Monat &#124; Tag &#124; Stunde &#124; MINUTE  
  
 *interval-fractional-seconds-precision* ::= *unsigned-integer*  
  
 *interval-leading-field-precision* ::= *unsigned-integer*  
  
 *Anführungszeichen* :: = '  
  
 *nicht signierte Ganzzahl* :: = *Ziffer...*
