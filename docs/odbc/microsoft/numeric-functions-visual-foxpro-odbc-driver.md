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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73379b769da61fe14ba18815446337d0172c2805
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654402"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>Numerische Funktionen (Visual FoxPro-ODBC-Treiber)
Die folgende Tabelle beschreibt die numerische ODBC-Funktionen von der Visual FoxPro-ODBC-Treiber unterstützt werden; Wenn die Visual FoxPro-Grammatik für die gleiche Funktion aus der ODBC-Syntax unterscheidet, wird der Visual FoxPro-Äquivalent aufgeführt.  
  
|ODBC-Grammatik|Visual FoxPro-Grammatik|  
|------------------|---------------------------|  
|ABS *(Numeric_exp)*||  
|ACOS *(Float_exp)*||  
|ASIN *(Float_exp)*||  
|ATAN *(Float_exp)*||  
|Atan2 *(float_exp1, float_exp2)*|ATN2 (*float_exp1, float_exp2*)|  
|CEILING- *(Numeric_exp)*||  
|COS *(Float_exp)*||  
|COT *(Float_exp)*||  
|Grad *(Numeric_exp)*|RTOD *(Numeric_exp)*|  
|"Exp" *(Float_exp)*||  
|FLOOR *(Numeric_exp)*||  
|LOG *(Float_exp)*||  
|Log10 *(Float_exp)*||  
|MOD *(integer_exp1, integer_exp2)*||  
|PI *)*||  
|BOGENMAß *(Numeric_exp)*|DTOR *(Numeric_exp)*|  
|RAND *([Integer_exp])*||  
|ROUND *(Numeric_exp, Integer_exp)*||  
|Anmeldung *(Numeric_exp)*||  
|SIN *(Float_exp)*||  
|"SQRT" *(Float_exp)*||  
|TAN *(Float_exp)*||  
  
 Die folgenden Funktionen werden nicht unterstützt:  
  
 POWER *(Numeric_exp, Integer_exp)*  
  
 ABSCHNEIDEN *(Numeric_exp, Integer_exp)*
