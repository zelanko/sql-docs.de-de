---
title: Löschen einer Tabelle | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e9a9269457d973da6b56f9e7990c31700dafcad9
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
---
# <a name="delete-a-table"></a>Löschen einer Tabelle
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Im Modell-Designer können Sie Tabellen in der Arbeitsbereichsdatenbank des Modells löschen, die Sie nicht mehr benötigen. Das Löschen einer Tabelle wirkt sich nicht auf die ursprünglichen Quelldaten aus, sondern nur auf die importierten Daten, mit denen Sie gearbeitet haben. Das Löschen einer Tabelle kann nicht rückgängig gemacht werden.  
  
### <a name="to-delete-a-table"></a>So löschen Sie eine Tabelle  
  
-   Klicken Sie unten im Modell-Designer mit der rechten Maustaste auf die Registerkarte der Tabelle, die gelöscht werden soll, und klicken Sie dann auf **Löschen**.  
  
## <a name="considerations-when-deleting-tables"></a>Überlegungen beim Löschen von Tabellen  
  
-   Wenn Sie eine Tabelle löschen, wird die gesamte Registerkarte gelöscht, auf der sich die Tabelle befand.  
  
-   Wenn dieser Tabelle Measures zugeordnet waren, wird die Definition des Measures ebenfalls gelöscht.  
  
-   Wenn Sie mithilfe dieser Tabelle berechnete Spalten erstellt haben, werden auch die Spalten in dieser Tabelle gelöscht. Berechnete Spalten in anderen Tabellen, die Spalten aus der gelöschten Tabelle verwenden, verursachen einen Fehler.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Spalten](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
