---
description: ORDER BY-Ausdrucksliste
title: Order by-Ausdrucks Liste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [ODBC]
- SQL grammar [ODBC], order by clause
ms.assetid: 5ef88186-a99f-4e2c-a3f3-98a42d4f03a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fd084a1012d445c89cacba168f21267238bc250f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340616"
---
# <a name="order-by-expression-list"></a>ORDER BY-Ausdrucksliste
Ausdrücke können in der ORDER BY-Klausel verwendet werden. In den folgenden Klauseln wird die Tabelle z. b. nach drei Schlüssel Ausdrücken geordnet: a + b, c + d und e.  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Für Set-Funktionen oder einen Ausdruck, der eine Set-Funktion enthält, ist keine Reihenfolge zulässig.
