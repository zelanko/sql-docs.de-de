---
title: Numerische Literale Syntax | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e035e3ec53c5b5494c029d6840b9f5c836821209
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299860"
---
# <a name="numeric-literal-syntax"></a>Syntax von numerischen Literalen
Die folgende Syntax wird für numerische Literale in ODBC verwendet:  
  
 *numeric-literal* ::= *signed-numeric-literal &#124; unsigned-numeric-literal*  
  
 *signed-numeric-literal* ::= [*sign*] *unsigned-numeric-literal*  
  
 *unsigned-numeric-literal* ::= *exact-numeric-literal &#124; ungefähr-numerisch-literal*  
  
 *exact-numeric-literal* ::= *unsigned-integer* [*period*[*unsigned-integer*]] *&#124;period unsigned-integer*  
  
 *Zeichen* ::= *Pluszeichen &#124; Minuszeichen*  
  
 *ungefähr-numerisch-literal* ::= *Mantissa E exponent*  
  
 *Mantissa* ::= *exakt-numerisch-literal*  
  
 *Exponent* ::= *signierte Ganzzahl*  
  
 *signierte ganzzahlige* Zahl ::= [*Zeichen*] *Unsigned-integer*  
  
 *unsigned-integer* ::= *ziffer...*  
  
 *Pluszeichen* ::=*+*  
  
 *Minuszeichen* ::= -  
  
 *Ziffer* ::= 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *Zeitraum* ::= .
