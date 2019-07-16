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
ms.openlocfilehash: 6352a5ae894adb09f714a78386bfecfa3ce1df77
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041621"
---
# <a name="interval-literal-syntax"></a>Syntax von Intervallliteralen
Die folgende Syntax wird für Intervall-Literale in ODBC verwendet.  
  
 *Intervall-Literals:: = Intervall* [+ *&#124;* -] *Interval-Zeichenfolge Intervall-Qualifizierer*  
  
 *Interval-Zeichenfolge* :: = *Anführungszeichen* { *Jahr-Monat-Literal* &#124; *Day-Time-Literal* } *Anführungszeichen*  
  
 *Jahr-Monat-Literal* :: = *Jahren-Wert* &#124; [*Jahren-Wert* -] *Monate-Wert*  
  
 *Day-Time-Literal* :: = *Tag-Zeitintervall* &#124; *Zeitintervall*  
  
 *Tag-Zeitintervall* :: = *Wert Tage* [*Stundenwert* [:*Minutenwert*[:*Sekundenwert*]]]  
  
 *Zeitintervall* :: = *Stundenwert* [:*Minutenwert* [:*Sekundenwert* ]]  
  
 &#124;*Minutenwert* [:*Sekundenwert* ]  
  
 &#124; *seconds-value*  
  
 *Der Jahreswert* :: = *Datetime-Wert*  
  
 *Wert für die Monate* :: = *Datetime-Wert*  
  
 *Wert für die Tage* :: = *Datetime-Wert*  
  
 *Wert für die Stunden* :: = *Datetime-Wert*  
  
 *Wert Minuten* :: = *Datetime-Wert*  
  
 *Wert für die Sekunden* :: = *Sekunden Ganzzahlwert* [. [ *Sekundenbruchteils*]]  
  
 *Sekunden Ganzzahlwert* :: = *einer Ganzzahl ohne Vorzeichen*  
  
 *Sekundenbruchteils* :: = *einer Ganzzahl ohne Vorzeichen*  
  
 *DateTime-Wert* :: = *einer Ganzzahl ohne Vorzeichen*  
  
 *Intervall-Qualifizierer* :: = *Start-Feld* für *End-Feld* &#124; *Single-Datetime-Feld*  
  
 *Start-Feld* :: = *nicht-Sekunde-Datetime-Feld* [(*Intervall führende-Feld-mit einfacher Genauigkeit* )]  
  
 *End-Feld* :: = *nicht-Sekunde-Datetime-Feld* &#124; zweite [(*Intervall--Sekunden-sekundenbruchteilgenauigkeit*)]  
  
 *Single-Datetime-Feld* :: = *nicht-Sekunde-Datetime-Feld* [(*Intervall führende-Feld-mit einfacher Genauigkeit*)] &#124; zweite [(*Intervall führende-Feld-mit einfacher Genauigkeit*  [, (*Intervall--Sekunden-sekundenbruchteilgenauigkeit*)]  
  
 *DateTime-Feld* :: = *nicht-Sekunde-Datetime-Feld* &#124; zweite  
  
 *nicht-Sekunde-Datetime-Feld* :: = Jahr &#124; Monat &#124; Tag &#124; Stunde &#124; MINUTE  
  
 *Intervall--Sekunden-sekundenbruchteilgenauigkeit* :: = *einer Ganzzahl ohne Vorzeichen*  
  
 *Intervall-führende-Feld-Genauigkeit* :: = *einer Ganzzahl ohne Vorzeichen*  
  
 *Anführungszeichen* :: = '  
  
 *nicht signierte Ganzzahl* :: = *Ziffer...*
