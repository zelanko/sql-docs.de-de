---
title: Numerische Funktionen (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3993a9a1b2412cb15229f2763c7c3b38f6b7862
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298160"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>Numerische Funktionen (Visual FoxPro-ODBC-Treiber)
In der folgenden Tabelle werden die vom Visual FoxPro-ODBC-Treiber unterstützten numerischen ODBC-Funktionen beschrieben. Wenn die Visual FoxPro-Grammatik für dieselbe Funktion von der ODBC-Syntax abweicht, wird die Entsprechung von Visual FoxPro aufgeführt.  
  
|ODBC-Grammatik|Visual FoxPro-Grammatik|  
|------------------|---------------------------|  
|ABS *(numeric_exp)*||  
|ACOS *(float_exp)*||  
|ASIN *(float_exp)*||  
|Atan *(float_exp)*||  
|Atan2 *(float_exp1 float_exp2)*|ATN2 (*float_exp1 float_exp2*)|  
|Ceiling *(numeric_exp)*||  
|COS *(float_exp)*||  
|Cot *(float_exp)*||  
|Grad *(numeric_exp)*|Rtod *(numeric_exp)*|  
|Exp *(float_exp)*||  
|Floor *(numeric_exp)*||  
|Protokoll *(float_exp)*||  
|LOG10 *(float_exp)*||  
|MOD *(integer_exp1 integer_exp2)*||  
|PI *()*||  
|Radiane *(numeric_exp)*|Dtor *(numeric_exp)*|  
|Rand *([integer_exp])*||  
|Round *(numeric_exp, integer_exp)*||  
|Sign *(numeric_exp)*||  
|Sin *(float_exp)*||  
|Sqrt *(float_exp)*||  
|Tan *(float_exp)*||  
  
 Die folgenden numerischen Funktionen werden nicht unterstützt:  
  
 Strom *(numeric_exp, integer_exp)*  
  
 Abschneiden *(numeric_exp integer_exp)*
