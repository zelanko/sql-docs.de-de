---
title: Anzeigen oder Ändern von Algorithmusparametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- algorithms [data mining]
- mining models [Analysis Services], algorithms
ms.assetid: 151b899b-c27a-4a09-bcf5-5c9f0ec24168
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7f41394c2adb8cbaaee2011e52ba6155a24e2e2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66082692"
---
# <a name="view-or-change-algorithm-parameters"></a>Anzeigen oder Ändern von Algorithmusparametern
  Sie können die Parameter ändern, die mit den Algorithmen zum Erstellen von Data Mining-Modellen bereitgestellt wurden, um die Ergebnisse des Modells anzupassen.  
  
 Die in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitgestellten Algorithmusparameter ändern viel mehr als nur die Eigenschaften des Modells: Sie können verwendet werden, um die Art und Weise, in der Daten verarbeitet, gruppiert und angezeigt werden, grundlegend zu ändern. Sie können mithilfe von Algorithmusparametern beispielsweise Folgende Aufgaben ausführen:  
  
-   Ändern der Analysemethode, z. B. die Clustermethode.  
  
-   Steuern des Funktionsauswahlverhaltens.  
  
-   Angeben der Größe von Itemsets oder der Wahrscheinlichkeit von Regeln.  
  
-   Steuern der Elementverzweigung und der Tiefe von Entscheidungsstrukturen.  
  
-   Angeben eines Ausgangswert oder der Größe des internen zur Modellerstellung verwendeten Zurückhaltungsdatasets.  
  
 Die für jeden Algorithmus bereitgestellten Parameter variieren stark. Eine Liste der Parameter, die Sie für jeden Algorithmus festlegen können, finden Sie in den technische Referenzthemen in folgendem Abschnitt: [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Miningmodelltasks und Anweisungen](mining-model-tasks-and-how-tos.md)  
  
  
