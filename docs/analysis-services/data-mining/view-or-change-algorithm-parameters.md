---
title: Anzeigen oder Ändern von Algorithmusparametern | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 58b512d726d45a8ceabb76a4ce2b1e6c8c62815b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209558"
---
# <a name="view-or-change-algorithm-parameters"></a>Anzeigen oder Ändern von Algorithmusparametern
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Sie können die Parameter ändern, die mit den Algorithmen zum Erstellen von Data Mining-Modellen bereitgestellt wurden, um die Ergebnisse des Modells anzupassen.  
  
 Durch die in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitgestellten Algorithmusparameter wird viel mehr als nur die Eigenschaften des Modells geändert. Sie können auch verwendet werden, um die Methode, mit der Daten verarbeitet, gruppiert und angezeigt werden, grundlegend zu ändern. Sie können mithilfe von Algorithmusparametern beispielsweise Folgende Aufgaben ausführen:  
  
-   Ändern der Analysemethode, z. B. die Clustermethode.  
  
-   Steuern des Funktionsauswahlverhaltens.  
  
-   Angeben der Größe von Itemsets oder der Wahrscheinlichkeit von Regeln.  
  
-   Steuern der Elementverzweigung und der Tiefe von Entscheidungsstrukturen.  
  
-   Angeben eines Ausgangswert oder der Größe des internen zur Modellerstellung verwendeten Zurückhaltungsdatasets.  
  
 Für jeden Algorithmus bereitgestellten Parameter variieren stark; eine Liste der Parameter, die Sie für jeden Algorithmus festlegen können, finden Sie in den technische Referenzthemen in diesem Abschnitt: [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
### <a name="change-an-algorithm-parameter"></a>Ändern eines Algorithmusparameters  
  
1.  Klicken Sie in der Registerkarte **Miningmodelle** des Data Mining-Designers in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]mit der rechten Maustaste auf den Algorithmustyp des Miningmodells, dessen Algorithmus Sie optimieren wollen, und klicken Sie anschließend auf **Algorithmusparameter festlegen**.  
  
     Das Dialogfeld **Algorithmusparameter** wird geöffnet.  
  
2.  Legen Sie in der **Wert** -Spalte einen neuen Wert für den Algorithmus fest, den Sie ändern wollen.  
  
     Wenn Sie in die **Wert** -Spalte keinen Wert eingeben, verwendet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] den Standardparameterwert. Die **Bereich** -Spalte beschreibt die möglichen Eingabewerte.  
  
3.  Klicken Sie auf **OK**.  
  
     Der Algorithmusparameter wird auf den neuen Wert festgelegt. Die Parameteränderung wird erst dann im Miningmodell widergespiegelt, wenn Sie das Modell erneut verarbeitet haben.  
  
### <a name="view-the-parameters-used-in-an-existing-model"></a>Anzeigen der in einem vorhandenen Modell verwendeten Parameter  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ein DMX-Abfragefenster in.  
  
2.  Geben Sie eine ähnliche Abfrage wie die Folgende ein:  
  
    ```  
    select MINING_PARAMETERS   
    from $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = '<model name>'  
  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodelltasks und -anweisungen](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
