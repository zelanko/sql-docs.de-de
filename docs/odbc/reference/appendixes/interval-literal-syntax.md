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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694052"
---
# <a name="interval-literal-syntax"></a>Syntax von Intervallliteralen
Die folgende Syntax wird für Intervall-Literale in ODBC verwendet.  
  
 *Intervall-Literals:: = Intervall* [+*&#124;*-] *Interval-Zeichenfolge Intervall-Qualifizierer*  
  
 *Interval-Zeichenfolge* :: = *Anführungszeichen* { *Jahr-Monat-Literal* &#124; *Day-Time-Literal* } *Anführungszeichen*  
  
 *Jahr-Monat-Literal* :: = *Jahren-Wert* &#124; [*Jahren-Wert* -] *Monate-Wert*  
  
 *Day-Time-Literal* :: = *Tag-Zeitintervall* &#124; *Zeitintervall*  
  
 *Tag-Zeitintervall* :: = *Wert Tage* [*Stundenwert* [:*Minutenwert*[:*Sekundenwert*]]]  
  
 *Zeitintervall* :: = *Stundenwert* [:*Minutenwert* [:*Sekundenwert* ]]  
  
 &#124;*Minutenwert* [:*Sekundenwert* ]  
  
 &#124;*Wert für die Sekunden*  
  
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
