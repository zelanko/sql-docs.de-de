---
title: Erstellen und Verwalten von Measures in tabellarischen Modellen von Analysis Services | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1c3794d9ed2927cf86b9aada08588f71b3a55b8a
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072607"
---
# <a name="create-and-manage-measures"></a>Erstellen und Verwalten von measures 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Ein Measure ist eine Formel, die zur Verwendung in einem Bericht oder einer PivotTable (oder einem PivotChart) von Excel erstellt wird. Measures können auf Standardaggregationsfunktionen basieren, z. B. COUNT oder SUM, oder Sie können mit DAX eigene Formeln definieren. Die Aufgaben in diesem Thema wird beschrieben, wie zum Erstellen und Verwalten von Measures mithilfe des measurerasters für eine Tabelle.  
  
## <a name="tasks"></a>Richtlinienübersicht  
 Verwenden Sie zum Erstellen und Verwalten von Measures, measurerasters für eine Tabelle. Sie können das Measureraster für eine Tabelle nur in der Datensicht des Modell-Designers anzeigen. In der Diagrammsicht können Sie keine Measures erstellen und kein Measureraster anzeigen. Vorhandene Measures können in der Diagrammsicht jedoch angezeigt werden. Um das Measureraster für eine Tabelle anzuzeigen, klicken Sie auf das Menü **Tabelle** und dann auf **Measureraster anzeigen**.  
  
###  <a name="bkmk_create_stand"></a> So erstellen Sie ein Measure mithilfe einer Standardaggregationsformel  
  
-   Klicken Sie auf die Spalte, für die Sie das Measure erstellen möchten, klicken Sie dann auf das Menü **Spalte** , zeigen Sie auf **AutoSumme**, und klicken Sie dann auf einen Aggregationstyp.  
  
     Das Measure wird automatisch mit einem Standardnamen erstellt, gefolgt von der Formel in der ersten Zelle im Measureraster direkt unterhalb der Spalte.  
  
###  <a name="bkmk_create_custom"></a> So erstellen Sie ein Measure mithilfe einer benutzerdefinierten Formel  
  
-   Klicken Sie im Measureraster unter der Spalte, für die Sie das Measure erstellen möchten, auf eine Zelle, und geben Sie dann in der Bearbeitungsleiste einen Namen gefolgt von einem Doppelpunkt (:), einem Gleichheitszeichen (=) und der Formel ein. Drücken Sie die EINGABETASTE, um die Formel zu übernehmen.  
  
###  <a name="bkmk_edit"></a> So bearbeiten Sie Measureeigenschaften  
  
-   Klicken Sie im Measureraster auf ein Measure, und geben Sie dann im Fenster **Eigenschaften** einen anderen Eigenschaftswert ein, oder wählen Sie ihn aus.  
  
###  <a name="bkmk_rename"></a> So benennen Sie ein Measure um  
  
-   Klicken Sie im Measureraster auf ein Measure, und geben Sie dann im Fenster **Eigenschaften** in **Measurename**einen neuen Namen ein, und drücken Sie die EINGABETASTE.  
  
     Sie können ein Measure auch in der Bearbeitungsleiste umbenennen. Der Measurename ist der Formel gefolgt von einem Doppelpunkt vorangestellt.  
  
###  <a name="bkmk_delete"></a> So löschen Sie ein Measure  
  
-   Klicken Sie im Measureraster mit der rechten Maustaste auf ein Measure, und klicken Sie auf **Löschen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Measures](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [KPIs](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [Berechnete Spalten](../../analysis-services/tabular-models/ssas-calculated-columns.md)  
  
  
