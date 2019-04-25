---
title: Sortieren von Daten in einer Analysis Services-Tabellenmodell-Tabelle | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4ab79de3551f1ef4613bb3c6f14b44ca660e2dfc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472090"
---
# <a name="sort-data-in-a-table"></a>Sortieren von Daten in einer Tabelle 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Sie können Daten in einer oder mehreren Spalten nach Text (A bis Z oder Z bis A) und Zahlen (kleinsten zu größten oder größten zu kleinsten) sortieren.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a>So sortieren Sie die Daten in einer Tabelle anhand einer Textspalte  
  
1.  Wählen Sie im Modell-Designer eine Spalte mit alphanumerischen Daten oder einen Zellbereich in einer Spalte aus, oder stellen Sie sicher, dass sich die aktive Zelle in einer Tabellenspalte befindet, die alphanumerische Daten enthält. Klicken Sie dann auf den Pfeil in der Kopfzeile der Spalte, nach der Sie filtern möchten.  
  
2.  Führen Sie im Menü AutoFilter einen der folgenden Schritte aus:  
  
    -   Um in aufsteigender alphanumerischer Reihenfolge zu sortieren, klicken Sie auf **Von A bis Z sortieren**.  
  
    -   Um in absteigender alphanumerischer Reihenfolge zu sortieren, klicken Sie auf **Von Z bis A sortieren**.  
  
    > [!NOTE]  
    >  In einigen Fällen können vor Daten, die aus anderen Anwendungen importiert werden, Leerzeichen eingefügt sein. Sie müssen diese Leerzeichen entfernen, um die Daten ordnungsgemäß sortieren zu können.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a>So sortieren Sie die Daten in einer Tabelle anhand einer numerischen Spalte  
  
1.  Wählen Sie im Modell-Designer eine Spalte mit alphanumerischen Daten oder einen Zellbereich in einer Spalte aus, oder stellen Sie sicher, dass sich die aktive Zelle in einer Tabellenspalte befindet, die alphanumerische Daten enthält. Klicken Sie dann auf den Pfeil in der Kopfzeile der Spalte, nach der Sie filtern möchten.  
  
2.  Führen Sie im Menü AutoFilter einen der folgenden Schritte aus:  
  
    -   Um von niedrigen Zahlen zu hohen Zahlen zu sortieren, klicken Sie auf **Nach Größe sortieren (aufsteigend)**.  
  
    -   Um von hohen Zahlen zu niedrigen Zahlen zu sortieren, klicken Sie auf **Nach Größe sortieren (absteigend).**  
  
    > [!NOTE]  
    >  Wenn die Ergebnisse nicht die erwarteten sind, enthält die Spalte möglicherweise als Text und nicht als Zahlen gespeicherte Zahlen. Zum Beispiel werden aus einigen Abrechnungssystemen importierte negative Zahlen oder Zahlen, denen ein ' (Apostroph) vorangeht, als Text gespeichert.  
  
## <a name="see-also"></a>Siehe auch  
 [Filtern und Sortieren von Daten](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [Perspektiven](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
