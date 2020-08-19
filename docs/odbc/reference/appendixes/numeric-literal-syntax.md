---
description: Syntax von numerischen Literalen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be87238f1663bcf9b12d40cb90521bb404a25af3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425012"
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
  
 *Plus-sign* :: = *+*  
  
 *Minuszeichen* :: =-  
  
 *Ziffer* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *Period* :: =.
