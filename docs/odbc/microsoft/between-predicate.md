---
title: ZWISCHEN Prädikat | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- BETWEEN predicate [ODBC]
- SQL grammar [ODBC], between predicate
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f3ff800938574bec81e9cbb86839e014085a2a8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283855"
---
# <a name="between-predicate"></a>BETWEEN-Prädikat
Die Syntax ist:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 gibt true nur dann zurück, wenn *Ausdruck1* größer oder gleich *ausdruck2* ist und *expression1* kleiner oder gleich *ausdruck3*ist.  
  
 Die Semantik dieser Syntax unterscheidet sich für die Desktopdatenbanktreiber und die Microsoft Jet-Engine. In Microsoft Jet SQL kann *Expression2* größer als *Ausdruck3* sein, sodass die Anweisung nur DANN TRUE zurückgibt, wenn *Expression1* größer oder gleich *expression3*ist und *expression1* kleiner oder gleich *expression2*ist.
