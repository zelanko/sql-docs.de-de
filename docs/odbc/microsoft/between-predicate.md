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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f3ff800938574bec81e9cbb86839e014085a2a8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283855"
---
# <a name="between-predicate"></a>BETWEEN-Prädikat
Die Syntax ist:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 gibt nur dann true zurück, wenn *expression1* größer als oder gleich *expression2* ist und *expression1* kleiner oder gleich *expression3*ist.  
  
 Die Semantik dieser Syntax unterscheidet sich für die Desktop-Datenbanktreiber und das Microsoft Jet-Modul. In Microsoft Jet SQL kann *expression2* größer als *expression3* sein, damit die Anweisung nur dann true zurückgibt, wenn *expression1* größer oder gleich *expression3*und *expression1* kleiner oder gleich *expression2*ist.
