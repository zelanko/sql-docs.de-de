---
title: Algorithmusparameter (Dialog Feld) (Mining Modell Ansicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.models.algorithmparameters.f1
helpviewer_keywords:
- Algorithm Parameters dialog box
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c72a3c52da21ca7af10103010500bb43fd46a10a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062610"
---
# <a name="algorithm-parameters-dialog-box-mining-models-view"></a>Algorithmusparameter (Dialogfeld, Miningmodelle-Sicht)
  Verwenden Sie das Dialogfeld **Algorithmusparameter** , um für das ausgewählte Modell spezifische Algorithmusparameter anzupassen. Wenn Sie einen Algorithmusparameter ändern, ändern Sie normalerweise auch die Ergebnisse des Miningmodells. Die Art, in der die einzelnen Parameter sich auf die Ergebnisse auswirken, ist abhängig vom verwendeten Algorithmus und den Daten. Weitere Informationen finden Sie unter [Anpassen von Miningmodellen und -strukturen](data-mining/customize-mining-models-and-structure.md).  
  
## <a name="options"></a>Optionen  
 **Parameters**  
 Listet die Parameter auf, die für das ausgewählte Miningmodell verfügbar sind.  
  
 In der folgenden Liste werden die verfügbaren Spalten beschrieben.  
  
|Column|BESCHREIBUNG|  
|------------|-----------------|  
|**Parameter**|Listet die Namen der Parameter auf.|  
|**Wert**|Geben Sie einen Wert nur dann ein, wenn Sie den Standardwert des Parameters ändern möchten.|  
|**Standard**|Listet den Standardwert des Parameters auf, den der Algorithmus verwendet, wenn Sie keinen Wert in der **Wert** -Spalte bereitstellen.|  
|**Bereich**|Listet den Bereich der möglichen Werte auf, die Sie in die **Wert** -Spalte eingeben können. Die Bereiche können einen der folgenden Werte aufweisen:<br /><br /> Eine diskrete Liste, z. b. 1, 2, 3<br /><br /> Ein inklusiver Bereich, z. b. [0, 100]<br /><br /> Ein exklusiver Bereich, z. b. (0,...)<br /><br /> Eine Kombination, z. b. [0,...)|  
  
 **Beschreibung**  
 Beschreibt den in der **Parameter** -Liste ausgewählten Parameter.  
  
 **Add (Hinzufügen)**  
 Klicken Sie auf diese Option, um der Liste zusätzliche, algorithmusspezifische Parameter hinzuzufügen. Nachdem der Parameter hinzugefügt wurde, können Sie den richtigen Namen in die Spalte **Parameter** und einen Wert in die Spalte **Wert** eingeben.  
  
 **Remove**  
 Klicken Sie auf diese Option, um einen benutzerdefinierten Parameter aus der Liste zu löschen.  
  
 Wenn Sie einen der Algorithmusstandardparameter von Analysis Services aus der Liste löschen, wird der Parameter im Modell weiterhin verwendet, jedoch mit den Standardwerten für den betreffenden Parameter. Der Parameter wird nicht dauerhaft gelöscht und wird beim nächsten Öffnen des Dialogfelds wieder angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell Ansicht &#40;Data Mining-Modell-Designer&#41;](mining-models-view-data-mining-model-designer.md)   
 [Verschieben von Data Mining-Objekten](data-mining/moving-data-mining-objects.md)  
  
  
