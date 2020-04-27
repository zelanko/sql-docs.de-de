---
title: Interval-Literalsyntax | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81290570"
---
# <a name="interval-literal-syntax"></a>Syntax von Intervallliteralen
Die folgende Syntax wird für intervallliterale in ODBC verwendet.  
  
 *Interval-Literale:: = Interval* [+*&#124;*-] *Intervall-Zeichen folgen Intervall-Qualifizierer*  
  
 *Interval-String* :: = *Zitat* { *year-month-Literale* &#124; *Tag-Time-Literale* }- *Anführungs* Zeichen  
  
 *year-month-Literale* :: = *Jahre-Wert* &#124; [*Jahre-Wert* -] *Monate-Wert*  
  
 *Day-time-Literale* :: = *Day-time-interval* &#124; *Zeitintervall*  
  
 *Day-time-interval* :: = *Days-Value* [*Hours-Value* [:*Minutes-Value*[:*seconds-Value*]]]  
  
 *Zeitintervall* :: = *Stunden-Wert* [:*Minutes-Wert* [:*seconds-Wert* ]]  
  
 &#124; *Minuten-Wert* [:*seconds-Wert* ]  
  
 &#124; *Sekunden-Wert*  
  
 *years-Value* :: = *DateTime-Value*  
  
 *Monate-Wert* :: = *DateTime-Value*  
  
 *Days-Value* :: = *DateTime-Value*  
  
 *Hours-Value* :: = *DateTime-Value*  
  
 *Minutes-Value* :: = *DateTime-Value*  
  
 *seconds-Value* :: = *seconds-ganzzahliger Wert* [. [ *Sekundenbruchteile*] ]  
  
 *seconds-integer-value* :: = *unsigned-Integer*  
  
 *seconds-Bruchteil* :: = *unsigned-Integer*  
  
 *DateTime-Value* :: = *unsigned-Integer*  
  
 *Interval-Qualifizierer* :: = *Start-Field* -to *-End-Field* &#124; *Single-DateTime-Field*  
  
 *Start-Field* :: = *Non-Second-DateTime-Field* [(*Intervall-führende-Feld Genauigkeit* )]  
  
 *End-Field* :: = *Non-Second-DateTime-Field* &#124; Sekunde [(*Intervall-Bruch Sekunden-Genauigkeit*)]  
  
 *Single-DateTime-Field* :: = *Non-Second-DateTime-Field* [(*Interval-Leading-Field-Precision*)] &#124; Second [(*Interval-Leading-Field-Precision* [, (*Intervall-Sekundenbruchteile-Genauigkeit*)]  
  
 *DateTime-Field* :: = *nicht-Second-DateTime-Field* &#124; Sekunde  
  
 *nicht-Second-DateTime-Field* :: = Jahr &#124; Monat &#124; Tag &#124; Stunde &#124; Minute  
  
 *Interval-Sekundenbruchteile-Genauigkeit* :: = *unsignierte Ganzzahl*  
  
 *Interval-Leading-Field-Precision* :: = *unsigned-Integer*  
  
 *Anführungs* Zeichen:: = '  
  
 *unsigned-Integer* :: = *Digit...*
