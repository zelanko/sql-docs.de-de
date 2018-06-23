---
title: Hinzufügen neuer Modelle zur Targeted Mailing-Struktur (Lernprogramm zu Datamining-Lernprogramm) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
caps.latest.revision: 45
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c5e31e06a489b1807335f63dd1675fc9e77c45b4
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312378"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>Hinzufügen neuer Modelle zur Targeted Mailing-Struktur (Lernprogramm zu Data Mining-Grundlagen)
  In dieser Aufgabe definieren Sie zwei zusätzliche Modelle mithilfe der **Miningmodelle** des Data Mining-Designers. Zum Erstellen der Modelle verwenden Sie die Algorithmen Microsoft Clustering und Microsoft Naive Bayes. Diese beiden Algorithmen werden aufgrund ihrer Fähigkeit ausgewählt, einen diskreten Wert (z. B. Fahrradkauf) vorhersagen zu können. Weitere Informationen zu diesen Algorithmen finden Sie unter [Microsoft Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) und [Microsoft Naive Bayes-Algorithmus](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)  
  
### <a name="to-create-a-clustering-mining-model"></a>So legen Sie ein Clustering-Miningmodell an  
  
1.  Wechseln Sie zu der **Miningmodelle** Registerkarte Data Mining-Designers in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
     Beachten Sie, dass der Designer zwei Spalten, eine für die Miningstruktur und eine für zeigt die `TM_Decision_Tree` Miningmodell, das Sie in der vorherigen Lektion erstellt haben.  
  
2.  Mit der rechten Maustaste die **Struktur** Spalte, und wählen **Neues Miningmodell**.  
  
3.  In der **Neues Miningmodell** Dialogfeld **Modellname**, Typ `TM_Clustering`.  
  
4.  In **Algorithmusname**Option **Microsoft Clustering**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 Das neue Modell erscheint jetzt im die **Miningmodelle** des Data Mining-Designers. Dieses Modell, integriert der [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus gruppiert Kunden mit ähnlichen Eigenschaften in Clustern und sagt den fahrradkauf für jeden Cluster. Obwohl Sie ändern können, die Verwendung von Spalten sowie die Eigenschaften für das neue Modell keine Änderungen an der `TM_Clustering` Modell für dieses Lernprogramm erforderlich sind.  
  
### <a name="to-create-a-naive-bayes-mining-model"></a>So erstellen Sie ein Naive Bayes-Miningmodell  
  
1.  In der **Miningmodelle** des Data Mining-Designers, rechts Datumsoptionen **Struktur** Spalte, und wählen Sie **Neues Miningmodell**.  
  
2.  In der **Neues Miningmodell** Dialogfeld unter **Modellname**, Typ `TM_NaiveBayes`.  
  
3.  In **Algorithmusname**Option **Microsoft Naive Bayes**, klicken Sie dann auf **OK**.  
  
     Einer Meldung darauf hingewiesen, die die [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Algorithmus unterstützt nicht die **Alter** und **Yearly Income** Spalten, die kontinuierlich sind.  
  
4.  Klicken Sie auf **Ja** bestätigt die Nachricht und den Vorgang fortsetzen.  
  
 Ein neues Modell angezeigt wird, der **Miningmodelle** des Data Mining-Designers. Obwohl Sie ändern können, die Verwendung von Spalten sowie die Eigenschaften für alle Modelle auf dieser Registerkarte keine Änderungen an der `TM_NaiveBayes` Modell für dieses Lernprogramm erforderlich sind.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Verarbeiten von Modellen in der Targeted Mailing-Struktur &#40;Lernprogramm zu Datamining-Lernprogramm&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Miningmodellen zu einer Struktur &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)   
 [Datamining-Designer](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Verschieben von Data Mining-Objekten](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  