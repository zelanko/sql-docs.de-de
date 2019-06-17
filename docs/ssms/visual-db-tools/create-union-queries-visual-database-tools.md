---
title: Erstellen von UNION-Abfragen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
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
manager: craigg
ms.openlocfilehash: 087abb83075b37b3002f649164485ae64cf137c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65095216"
---
# <a name="create-union-queries-visual-database-tools"></a>Erstellen von UNION-Abfragen (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
[Unterstützte Abfragetypen (Visual Database Tools)](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Ausführen grundlegender Vorgänge mit Abfragen (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[UNION (Transact-SQL)](https://msdn.microsoft.com/607c296f-8a6a-49bc-975a-b8d0c0914df7)  
  
