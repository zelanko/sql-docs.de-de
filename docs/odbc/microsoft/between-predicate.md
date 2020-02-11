---
title: Zwischen Prädikat | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1a0ac99729966acdcb03c2aab0175c34bba0c08a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138117"
---
# <a name="between-predicate"></a>BETWEEN-Prädikat
Die Syntax ist:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 gibt nur dann true zurück, wenn *expression1* größer als oder gleich *expression2* ist und *expression1* kleiner oder gleich *expression3*ist.  
  
 Die Semantik dieser Syntax unterscheidet sich für die Desktop-Datenbanktreiber und das Microsoft Jet-Modul. In Microsoft Jet SQL kann *expression2* größer als *expression3* sein, damit die Anweisung nur dann true zurückgibt, wenn *expression1* größer oder gleich *expression3*und *expression1* kleiner oder gleich *expression2*ist.
