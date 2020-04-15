---
title: Intervallliterale Syntax | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3387b07a8e769206a6a495addff4287000691fec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290570"
---
# <a name="interval-literal-syntax"></a>Syntax von Intervallliteralen
Die folgende Syntax wird für Intervallliterale in ODBC verwendet.  
  
 *intervall-literal ::= INTERVAL* [+*&#124;*-] *intervall-string interval-qualifier*  
  
 *interval-string* ::= *Anführungszeichen* , *Jahr-Monat-Literal* &#124; *Tag-Zeit-Literal-Anführungszeichen* *quote*  
  
 *Jahr-Monats-Literal* ::= *Jahreswert* &#124; [*Jahreswert* -] *Monatswert*  
  
 *Day-Time-Literal* ::= *Day-Time-Intervall* &#124; *Zeitintervall*  
  
 *Tageszeitintervall* ::= *Tage-Wert* [*Stundenwert* [:*Minuten-Wert*[:*Sekunden-Wert*]]]  
  
 *Zeitintervall* ::= *Stundenwert* [:*Minuten-Wert* [:*Sekundenwert* ] ]  
  
 &#124; *Minutenwert* [:*Sekundenwert* ]  
  
 &#124; *Sekunden-Wert*  
  
 *Jahreswert* ::= *Datumszeitwert*  
  
 *Monatswert* ::= *Datumszeitwert*  
  
 *days-Wert* ::= *Datumszeitwert*  
  
 *Stundenwert* ::= *Datumszeitwert*  
  
 *Minuten-Wert* ::= *Datumszeitwert*  
  
 *Sekundenwert* ::= *Sekunden-Ganzzahlwert* [.[ *Sekunden-Fraktion*] ]  
  
 *Sekunden-Ganzzahlwert* ::= *nicht signierte Ganzzahl*  
  
 *Sekunden-Fraktion* ::= *nicht signierte Ganzzahl*  
  
 *datumsweise::=* *nicht signierte Ganzzahl*  
  
 *Intervall-Qualifizierer* ::= *Startfeld* zum *Endfeld* &#124; *Single-Datetime-Feld*  
  
 *Startfeld* ::= *nicht-zweites Datum-Time-Feld* [(*intervallführendes Feld -Präzision* )]  
  
 *Endfeld* ::= *nicht-zweite-Datetime-Feld* &#124; SECOND[(*intervall-fractional-seconds-precision*)]  
  
 *Single-Datetime-Feld* ::= *nicht-zweites-Datumsuhr-Feld* [(*Intervall-führende-Feld-Präzision*)] &#124; SECOND[(*interval-leading-field-precision* [, (*interval-fractional-seconds-precision*)]  
  
 *datumszeitliches Feld* ::= *nicht-zweites Datum-Uhrzeitfeld* &#124; ZWEITE  
  
 *Nicht-zweites-Datumszeitfeld* ::= JAHR &#124; MONAT &#124; TAG &#124; Stunde &#124; MINUTE  
  
 *intervall-fractional-seconds-precision* ::= *unsigned-integer*  
  
 *intervall-führende Feldgenauigkeit* ::= *unsigniert-ganzzahlig*  
  
 *Zitat* ::= '  
  
 *unsigned-integer* ::= *ziffer...*
