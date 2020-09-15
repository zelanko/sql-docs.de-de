---
description: Erstellen von UNION-Abfragen (Visual Database Tools)
title: Erstellen von UNION-Abfragen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 12731ff7960a8376c8f0a79d933d62fde43e76dd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88314986"
---
# <a name="create-union-queries-visual-database-tools"></a>Erstellen von UNION-Abfragen (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Mit dem Schlüsselwort UNION können Sie die Ergebnisse von zwei SELECT-Anweisungen in eine Ergebnistabelle aufnehmen. Alle Zeilen, die von den beiden SELECT-Anweisungen zurückgegeben werden, werden zum Ergebnis des UNION-Ausdrucks kombiniert. Beispiele finden Sie unter [SELECT-Beispiele (Transact-SQL)](https://msdn.microsoft.com/9b9caa3d-e7d0-42e1-b60b-a5572142186c).  
  
> [!NOTE]  
> Im Diagrammbereich kann nur eine SELECT-Klausel angezeigt werden. Wenn Sie eine UNION-Abfrage verwenden, wird der Bereich Tabellenvorgänge Abfrage-Designer daher nicht angezeigt.  
  
### <a name="to-create-a-merged-select-query"></a>So erstellen Sie eine zusammengeführte SELECT-Abfrage  
  
1.  Öffnen Sie eine Abfrage, oder erstellen Sie eine neue.  
  
2.  Geben Sie im Bereich SQL einen gültigen UNION-Ausdruck ein.  
  
    Das folgende Beispiel stellt einen gültigen UNION-Ausdruck dar.  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  Klicken Sie im Menü **Abfrage-Designer** auf **SQL ausführen** , um die Abfrage auszuführen.  
  
    Die UNION-Abfrage wird jetzt vom Abfrage-Designer formatiert.  
  
## <a name="see-also"></a>Weitere Informationen  
[Unterstützte Abfragetypen](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Artikel zum Entwerfen von Abfragen und Sichten](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Ausführen grundlegender Vorgänge mit Abfragen](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[UNION (Transact-SQL)](https://msdn.microsoft.com/607c296f-8a6a-49bc-975a-b8d0c0914df7)
