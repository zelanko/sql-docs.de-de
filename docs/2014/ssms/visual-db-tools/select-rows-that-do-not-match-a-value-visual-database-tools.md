---
title: Auswählen von Zeilen, die mit einem Wert nicht übereinstimmen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 92e0ac92531caeab2aa64187141c4978bc08bcba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181860"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Auswählen von Zeilen, die mit einem Wert nicht übereinstimmen (Visual Database Tools)
  Zum Suchen von Zeilen, die mit einem Wert nicht übereinstimmen, wird der Operator NOT verwendet.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>So suchen Sie nach Zeilen, die mit einem Wert nicht übereinstimmen  
  
1.  Fügen Sie im [Kriterienbereich](visual-database-tools.md)die Spalten oder Ausdrücke hinzu, die in der Suchbedingung verwendet werden sollen, falls dies nicht bereits geschehen ist.  
  
2.  Wechseln Sie zu der Zeile, die die Datenspalte oder den Ausdruck für die Suche enthält. Geben Sie anschließend in der Datenblattspalte **Filter** den Operator NOT gefolgt von einem Suchwert ein.  
  
 Um beispielsweise alle Zeilen in der Tabelle `products` zu suchen, in denen der Wert in der Spalte für den Produktcode nicht mit "A" beginnt, können Sie folgende Suchbedingung eingeben:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Regeln für das Eingeben von Suchwerten &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Angeben von Suchkriterien &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
