---
title: Hinzufügen neuer Modelle zur Ziel-Mailing-Struktur (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 285ee82110ffdef521d75fb43343f4889663e981
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62822635"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>Hinzufügen neuer Modelle zur Targeted Mailing-Struktur (Lernprogramm zu Data Mining-Grundlagen)
  In dieser Aufgabe definieren Sie zwei zusätzliche Modelle, indem Sie die Registerkarte **Mining Modelle** des Data Mining-Designers verwenden. Zum Erstellen der Modelle verwenden Sie die Algorithmen Microsoft Clustering und Microsoft Naive Bayes. Diese beiden Algorithmen werden aufgrund ihrer Fähigkeit ausgewählt, einen diskreten Wert (z. B. Fahrradkauf) vorhersagen zu können. Weitere Informationen zu diesen Algorithmen finden Sie unter [Microsoft Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) und [Microsoft Naive Bayes-Algorithmus](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md) .  
  
### <a name="to-create-a-clustering-mining-model"></a>So legen Sie ein Clustering-Miningmodell an  
  
1.  Wechseln Sie in zur Registerkarte **Mining Modelle** im Data Mining [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]-Designer.  
  
     Beachten Sie, dass im Designer zwei Spalten angezeigt werden: eine für die Mining Struktur und `TM_Decision_Tree` eine für das Mining Modell, die Sie in der vorherigen Lektion erstellt haben.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Spalte **Struktur** , und wählen Sie **Neues Mining Modell**.  
  
3.  Geben `TM_Clustering`Sie im Dialogfeld **Neues Mining Modell** unter **Modellname den Namen**ein.  
  
4.  Wählen Sie unter **Algorithmusname den Namen** **Microsoft Clustering**aus.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 Das neue Modell wird jetzt auf der Registerkarte **Mining Modelle** im Data Mining-Designer angezeigt. Dieses Modell, das mit dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus erstellt wurde, gruppiert Kunden mit ähnlichen Merkmalen in Clustern und prognostiziert den Fahrradkauf für jeden Cluster. Obwohl Sie die Spalten Verwendung und die Eigenschaften für das neue Modell ändern können, sind für dieses `TM_Clustering` Tutorial keine Änderungen am Modell erforderlich.  
  
### <a name="to-create-a-naive-bayes-mining-model"></a>So erstellen Sie ein Naive Bayes-Miningmodell  
  
1.  Klicken Sie im Data Mining-Designer auf der Registerkarte **Mining Modelle** mit der rechten Maustaste auf die Spalte **Struktur** , und wählen Sie **Neues Mining Modell**aus.  
  
2.  Geben `TM_NaiveBayes`Sie im Dialogfeld **Neues Mining Modell** unter **Modellname den Namen**ein.  
  
3.  Wählen Sie unter **Algorithmusname**die Option **Microsoft Naive Bayes**aus, und klicken Sie auf **OK**.  
  
     Es wird eine Meldung angezeigt, [!INCLUDE[msCoName](../includes/msconame-md.md)] die besagt, dass der Naive Bayes-Algorithmus die Spalten **Alter** und **jährlicher Einkommen** , die kontinuierlich sind, nicht unterstützt.  
  
4.  Klicken Sie auf **Ja** , um die Meldung zu bestätigen und fortzufahren.  
  
 Auf der Registerkarte **Mining Modelle** des Data Mining-Designers wird ein neues Modell angezeigt. Obwohl Sie die Spalten Verwendung und-Eigenschaften für alle Modelle auf dieser Registerkarte ändern können, sind für dieses `TM_NaiveBayes` Tutorial keine Änderungen am Modell erforderlich.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Verarbeiten von Modellen in der vorgesehenen Mailing-Struktur &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Mining Modellen zu einer Struktur &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)   
 [Data Mining-Designer](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Verschieben von Data Mining-Objekten](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  
