---
title: Ausschließen doppelter Zeilen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bb8dabb400121ffc98a5322132eb6fe4a2ea8d8c
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68254579"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Ausschließen doppelter Zeilen (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Wenn in einem Resultset nur eindeutige Werte angezeigt werden sollen, können Sie das Ausschließen von Duplikaten aus dem Resultset angeben.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>So schließen Sie doppelte Zeilen aus dem Resultset aus  
  
1.  Klicken Sie mit der rechten Maustaste auf den Hintergrund des Diagrammbereichs, und wählen Sie im Kontextmenü **Eigenschaften** aus.  
  
2.  Klicken Sie im Eigenschaftenfenster auf **DISTINCT-Werte** , und legen Sie als Wert **Ja**fest.  
  
    Der Abfrage- und Sicht-Designer fügt das Schlüsselwort DISTINCT vor der Liste der Anzeigespalten in der SQL-Anweisung ein.  
  
    > [!NOTE]  
    > Wenn Sie das Schlüsselwort DISTINCT verwenden, können Sie möglicherweise die Ergebnisse im Ergebnisbereich nicht ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
[Angeben von Suchkriterien &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Sortieren und Gruppieren von Abfrageergebnissen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  
