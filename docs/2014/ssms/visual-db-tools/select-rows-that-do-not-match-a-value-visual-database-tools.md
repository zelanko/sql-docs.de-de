---
title: Auswählen von Zeilen, die mit einem Wert nicht übereinstimmen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
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
ms.openlocfilehash: f84f4fcc8a6dde7dcf9f556a72c2599356e231f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067536"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Auswählen von Zeilen, die mit einem Wert nicht übereinstimmen (Visual Database Tools)
  Zum Suchen von Zeilen, die mit einem Wert nicht übereinstimmen, wird der Operator NOT verwendet.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>So suchen Sie nach Zeilen, die mit einem Wert nicht übereinstimmen  
  
1.  Wenn Sie dies noch nicht getan haben, fügen Sie die Spalten oder Ausdrücke, die Sie in der Such Bedingung verwenden möchten, dem [Kriterienbereich](visual-database-tools.md)hinzu.  
  
2.  Wechseln Sie zu der Zeile, die die Datenspalte oder den Ausdruck für die Suche enthält. Geben Sie anschließend in der Datenblattspalte **Filter** den Operator NOT gefolgt von einem Suchwert ein.  
  
 Um beispielsweise alle Zeilen in der Tabelle `products` zu suchen, in denen der Wert in der Spalte für den Produktcode nicht mit "A" beginnt, können Sie folgende Suchbedingung eingeben:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Regeln für das Eingeben von Such Werten &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Angeben von Suchkriterien &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
