---
title: ORDER BY-Ausdrucksliste | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c6be518211edb07251ff9234b095f3d3dde248b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758888"
---
# <a name="order-by-expression-list"></a>ORDER BY-Ausdrucksliste
Ausdrücke können in der ORDER BY-Klausel verwendet werden. Z. B. in den folgenden Klauseln in der Tabelle sortiert wird, ist durch drei wichtige Ausdrücke: a + b, C + d und e.  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Keine Sortierung kann auf Set-Funktionen oder ein Ausdruck, der eine Set-Funktion enthält.
