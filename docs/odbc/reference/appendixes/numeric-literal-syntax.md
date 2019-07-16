---
title: Numerischen Literalen Syntax | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9daa81e2e0c2e927ee7407d4a00d5d48c333bd54
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67990718"
---
# <a name="numeric-literal-syntax"></a>Syntax von numerischen Literalen
Die folgende Syntax wird für numerische Literale in ODBC verwendet:  
  
 *numerischen Literalen* :: = *signiert-numerische-Literal &#124; unsigned-numerische-Literal*  
  
 *signiert-numerische-Literal* :: = [*anmelden*] *unsigned-numerische-Literal*  
  
 *unsigned-numerische-Literal* :: = *exakte numerische-literalen &#124; ungefähren numerischen-Literalen*  
  
 *exakte numerische-literalen* :: = *unsigned Integer* [*Zeitraum*[*unsigned Integer*]]  *&#124;Zeitraum des unsigned Integer*  
  
 *sign* ::= *plus-sign &#124; minus-sign*  
  
 *Ungefähre numerische-literalen* :: = *Mantisse E Exponent*  
  
 *Mantisse* :: = *exakte numerische-literalen*  
  
 *Exponent* :: = *Ganzzahl mit Vorzeichen*  
  
 *signierte Ganzzahl* :: = [*anmelden*] *einer Ganzzahl ohne Vorzeichen*  
  
 *nicht signierte Ganzzahl* :: = *Ziffer...*  
  
 *Pluszeichen (+)* :: = *+*  
  
 *Minuszeichen (-)* :: = -  
  
 *digit* ::= 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *Zeitraum* :: =.
