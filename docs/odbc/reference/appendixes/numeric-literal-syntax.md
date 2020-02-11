---
title: Numerische Literale Syntax | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990718"
---
# <a name="numeric-literal-syntax"></a>Syntax von numerischen Literalen
Die folgende Syntax wird für numerische Literale in ODBC verwendet:  
  
 *numeric-Literale* :: = *Signed-numeric-Literal &#124; nicht signiertes numeric-Literale*  
  
 *Signed-numeric-Literale* :: = [*Sign*] *unsigned-numeric-Literale*  
  
 *unsigned-numeric-Literale* :: = *Exact-numeric-Literal&#124; ungefähre numerische Literale*  
  
 *Exact-numeric-Literale* :: = *unsigned-Integer* [*Period*[*unsigned-Integer*]] *&#124;period unsigned-Integer*  
  
 *Sign* :: = *plus-Sign &#124; minus-Sign*  
  
 *ungefähre-numeric-Literale* :: = *Mantisse E Exponent*  
  
 *Mantisse* :: = *Exact-numeric-Literale*  
  
 *Exponent* :: = *-Ganzzahl* mit Vorzeichen  
  
 *signed-integer* :: = [*Sign*] *nicht signierte Ganzzahl*  
  
 *unsigned-Integer* :: = *Digit...*  
  
 *Plus-sign* :: =*+*  
  
 *Minuszeichen* :: =-  
  
 *Ziffer* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 #a5 7 #a6 8 &#124; 9 &#124; 0  
  
 *Period* :: =.
