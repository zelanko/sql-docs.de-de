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
manager: craigg
ms.openlocfilehash: 18b1c144e84bf0be5aaeb68b66660f7bc7865ade
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601538"
---
# <a name="numeric-literal-syntax"></a>Syntax von numerischen Literalen
Die folgende Syntax wird für numerische Literale in ODBC verwendet:  
  
 *numerischen Literalen* :: = *signiert-numerische-Literal &#124; unsigned-numerische-Literal*  
  
 *signiert-numerische-Literal* :: = [*anmelden*] *unsigned-numerische-Literal*  
  
 *unsigned-numerische-Literal* :: = *exakte numerische-literalen &#124; ungefähren numerischen-Literalen*  
  
 *exakte numerische-literalen* :: = *unsigned Integer* [*Zeitraum*[*unsigned Integer*]]  *&#124;Zeitraum des unsigned Integer*  
  
 *Anmeldung* :: = *Pluszeichen &#124; Minuszeichen (-)*  
  
 *Ungefähre numerische-literalen* :: = *Mantisse E Exponent*  
  
 *Mantisse* :: = *exakte numerische-literalen*  
  
 *Exponent* :: = *Ganzzahl mit Vorzeichen*  
  
 *signierte Ganzzahl* :: = [*anmelden*] *einer Ganzzahl ohne Vorzeichen*  
  
 *nicht signierte Ganzzahl* :: = *Ziffer...*  
  
 *Pluszeichen (+)* :: = *+*  
  
 *Minuszeichen (-)* :: = -  
  
 *Ziffer* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *Zeitraum* :: =.
