---
title: ORDER VON Ausdrucksliste | Microsoft Docs
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
ms.openlocfilehash: 272fa0be844569d322679d444807f8c332b4837b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291220"
---
# <a name="order-by-expression-list"></a>ORDER BY-Ausdrucksliste
Ausdrücke können in der ORDER BY-Klausel verwendet werden. In den folgenden Klauseln wird die Tabelle beispielsweise nach drei Schlüsselausdrücken sortiert: a+b, c+d und e.  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Für festgelegte Funktionen oder einen Ausdruck, der eine Set-Funktion enthält, ist keine Sortierung zulässig.
