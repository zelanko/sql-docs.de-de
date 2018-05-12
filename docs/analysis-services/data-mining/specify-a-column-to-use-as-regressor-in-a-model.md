---
title: Geben Sie eine zu verwendenden Spalte in einem Modell als Regressor | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0cfbe8f17c14518b2acf41bdb9ecf64b1679ffb2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a>Bestimmen einer in einem Modell als Regressor zu verwendenden Spalte
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Ein lineares Regressionsmodell stellt den Wert des vorhersagbaren Attributs als Ergebnis einer Formel dar, die die Eingaben so kombiniert, dass die Daten so nah wie möglich an einer geschätzten Regressionsgeraden liegen. Der Algorithmus akzeptiert nur numerische Werte als Eingaben und erkennt automatisch die am besten passenden Eingaben.  
  
 Sie können jedoch angeben, dass eine Spalte als Regressor einbezogen werden soll, indem Sie dem Modell den FORCE_REGRESSOR-Parameter hinzufügen und die zu verwendenden Regressoren angeben. Sie sollten dies in Fällen tun, in denen das Attribut eine Bedeutung hat, auch wenn die Wirkung zu klein ist, um vom Modell erkannt zu werden. Oder wenn Sie sicherstellen möchten, dass das Attribut in die Formel einbezogen wird.  
  
 In der folgenden Prozedur wird beschrieben, wie ein einfaches lineares Regressionsmodell erstellt wird, und zwar mit den gleichen Beispieldaten, die im [Lernprogramm zu neuronalen Netzwerken](http://msdn.microsoft.com/library/42c3701a-1fd2-44ff-b7de-377345bbbd6b)verwendet werden. Das Modell ist nicht unbedingt robust, zeigt jedoch, wie Sie ein lineares Regressionsmodell mit dem Data Mining-Designer anpassen können.  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a>Erstellen eines einfachen linearen Regressionsmodells  
  
1.  Erweitern Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im **Projektmappen-Explorer**den Knoten **Miningstrukturen**.  
  
2.  Doppelklicken Sie auf die Datei Call Center.dmm, um sie im Designer zu öffnen.  
  
3.  Wählen Sie im Menü **Miningmodell** die Option **Neues Miningmodell**.  
  
4.  Wählen Sie als Algorithmus die Option **Microsoft Linear Regression**. Geben Sie als Namen **Callcenterregression**ein.  
  
5.  Ändern Sie die Spaltenverwendung auf der Registerkarte **Miningmodelle** wie folgt. Soweit dies nicht bereits der Fall ist, sollten alle Spalten, die nicht in der folgenden Liste enthalten sind, auf **Ignorieren**festgelegt werden.  
  
     FactCallCenterID**Key**  
  
     ServiceGrade**PredictOnly**  
  
     Total Operators**Input**  
  
     AverageTimePerIssue**Input**  
  
6.  Wählen Sie im Menü **Miningmodell** die Option zum Festlegen der **Modellparameter** aus.  
  
7.  Geben Sie für den FORCE_REGRESSOR-Parameter in der Spalte **Wert** die Spaltennamen in Klammern und durch Kommas getrennt wie folgt ein:  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  Der Algorithmus erkennt automatisch, welche Spalten die besten Regressoren sind. Sie müssen Regressoren nur erzwingen, wenn Sie sicherstellen möchten, dass eine Spalte in der endgültigen Formel enthalten ist.  
  
8.  Wählen Sie im Menü **Miningmodell** die Option **Modell verarbeiten**.  
  
     Im Viewer wird das Modell als einzelner Knoten dargestellt, der die Regressionsformel enthält. Sie können die Formel in der **Mininglegende**anzeigen oder die Koeffizienten für die Formel mithilfe von Abfragen extrahieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Linear Regression-Algorithmus](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)   
 [Datamining-Abfragen](../../analysis-services/data-mining/data-mining-queries.md)   
 [Technische Referenz zu Microsoft Linear Regression-Algorithmus](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)   
 [Miningmodellinhalt, lineare Regressionsmodelle & #40; Analysis Services – Datamining & #41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
