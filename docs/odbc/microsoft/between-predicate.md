---
title: Prädikat BETWEEN | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: a4411345d790e64ae9fb21144a7d82ffe4cd45e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690948"
---
# <a name="between-predicate"></a>BETWEEN-Prädikat
Die Syntax:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Gibt "true" nur, wenn *expression1* ist größer als oder gleich *expression2* und *expression1* ist kleiner als oder gleich *expression3*.  
  
 Die Semantik dieser Syntax ist für die Desktop-Datenbanktreiber und Microsoft Jet-Engine unterschiedlich. In der Microsoft Jet-SQL *expression2* kann größer sein als *expression3* , damit die Anweisung "true" zurückgeben werden nur dann, wenn *expression1* ist größer als oder gleich *expression3*, und *expression1* ist kleiner als oder gleich *expression2*.
