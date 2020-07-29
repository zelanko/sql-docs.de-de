---
title: Auswählen von Zeilen, die mit einem Wert nicht übereinstimmen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 56038b9497f60c2a3275c9216d5c2252d65d81f3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86010607"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Auswählen von Zeilen, die mit einem Wert nicht übereinstimmen (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Zum Suchen von Zeilen, die mit einem Wert nicht übereinstimmen, wird der Operator NOT verwendet.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>So suchen Sie nach Zeilen, die mit einem Wert nicht übereinstimmen  
  
1.  Fügen Sie im [Kriterienbereich](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)die Spalten oder Ausdrücke hinzu, die in der Suchbedingung verwendet werden sollen, falls dies nicht bereits geschehen ist.  
  
2.  Wechseln Sie zu der Zeile, die die Datenspalte oder den Ausdruck für die Suche enthält. Geben Sie anschließend in der Datenblattspalte **Filter** den Operator NOT gefolgt von einem Suchwert ein.  
  
Um beispielsweise alle Zeilen in der Tabelle `products` zu suchen, in denen der Wert in der Spalte für den Produktcode nicht mit "A" beginnt, können Sie folgende Suchbedingung eingeben:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Regeln für die Eingabe von Suchwerten](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Angeben von Suchkriterien](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
