---
title: Verarbeiten von Modellen in der Targeted Mailing-Struktur (Lernprogramm zu Datamining-Lernprogramm) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d8233bb-117e-4563-9302-8a5a8ad1fae2
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cbc9a6edac8206a521bf26f10ecb12969f1a4c74
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313198"
---
# <a name="processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>Verarbeiten von Modellen in der Targeted Mailing-Struktur (Lernprogramm zu Data Mining-Grundlagen)
  Bevor Sie die erstellten Miningmodelle durchsuchen und verwenden können, müssen Sie das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Projekt bereitstellen und die Miningstruktur und die Miningmodelle verarbeiten.  
  
-   *Bereitstellen von* sendet das Projekt an einen Server und alle Objekte in diesem Projekt auf dem Server erstellt.  
  
-   *Verarbeiten von* füllt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Objekte mit Daten aus relationalen Datenquellen.  
  
 Modelle können erst dann verwendet werden, wenn sie bereitgestellt und verarbeitet wurden. Wenn Sie Änderungen am Modell vornehmen, z. B. neue Daten hinzufügen, müssen Sie die Modelle darüber hinaus erneut bereitstellen und verarbeiten.  
  
## <a name="ensuring-consistency-with-holdoutseed"></a>Sicherstellen von Konsistenz mit HoldoutSeed  
 Wenn Sie ein Projekt bereitstellen und die Struktur sowie die Modelle verarbeiten, werden die einzelnen Zeilen in der Datenstruktur auf Grundlage eines numerischen Ausgangswerts entweder dem Trainings- oder Testsatz zugewiesen. Der numerische Ausgangswert wird in der Regel auf der Basis von Attributen der Datenstruktur berechnet. Bei einer Änderung der Modellaspekte würde sich der Ausgangswert jedoch ändern und zu leicht abweichenden Ergebnissen führen. Aus diesem Grund, um sicherzustellen, dass Ihre Ergebnisse den hier beschriebenen entsprechen, wir nach dem Zufallsprinzip weist eine feste *zurückhaltungsausgangswert* von `12`. Mit dem Ausgangswert zurückgehaltener Daten wird der Stichprobenalgorithmus initialisiert, und es wird sichergestellt, dass die Daten für alle Miningstrukturen und deren Modelle weitestgehend auf die gleiche Weise partitioniert werden.  
  
 Dieser Wert hat keinen Einfluss auf die Anzahl der Fälle im Trainingssatz, sondern stellt lediglich sicher, dass bei jeder Modellerstellung dieselbe Partitionierungsmethode verwendet wird.  
  
 Weitere Informationen über zurückhaltungsausgangswerte finden Sie unter [Trainings- und Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).  
  
#### <a name="to-set-the-holdout-seed"></a>So legen Sie den Ausgangswert zurückgehaltener Daten fest  
  
1.  Klicken Sie auf die **Miningstruktur** Registerkarte oder die **Miningmodelle** Registerkarte Data Mining-Designers in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
     **Targeted Mailing-Miningstruktur** zeigt in der **Eigenschaften** Bereich.  
  
2.  Sicherstellen, dass die **Eigenschaften** Bereich geöffnet ist, durch Drücken von **F4**.  
  
3.  Sicherstellen, dass **"CacheMode"** festgelegt ist, um **KeepTrainingCases**.  
  
4.  Geben Sie `12` für **HoldoutSeed**.  
  
## <a name="deploying-and-processing-the-models"></a>Bereitstellen und Verarbeiten der Modelle  
 Im Data Mining-Designer können Sie je nach Umfang der am Modell oder den zugrunde liegenden Daten vorgenommenen Änderungen entscheiden, welche Objekte verarbeitet werden sollen:  
  
 Bei dieser Aufgabe verarbeiten Sie die Struktur und alle Modelle gleichzeitig, weil die Daten und Modelle neu sind.  
  
#### <a name="to-deploy-the-project-and-process-all-the-mining-models"></a>So stellen Sie das Projekt bereit und verarbeiten alle Miningmodelle  
  
1.  In der **Miningmodell** klicken Sie im Menü **Miningstruktur verarbeiten und alle Modelle**.  
  
     Falls Sie Änderungen an der Miningstruktur vorgenommen haben, werden Sie aufgefordert, das Projekt zu erstellen und bereitzustellen, bevor Sie die Modelle verarbeiten. Klicken Sie auf **Ja**.  
  
2.  Klicken Sie auf **ausführen** in der **Miningstruktur verarbeiten - Targeted Mailing** (Dialogfeld).  
  
     Das Dialogfeld **Verarbeitungsstatus** wird geöffnet und zeigt detaillierte Informationen zur Verarbeitung des Modells an. Verarbeitung des Modells dauert einige Zeit, abhängig von Ihrem Computer.  
  
3.  Klicken Sie nach Abschluss der Modellverarbeitung im Dialogfeld **Verarbeitungsstatus** auf **Schließen** .  
  
4.  Klicken Sie auf **schließen** in der **Miningstruktur verarbeiten - \<Struktur >** (Dialogfeld).  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Hinzufügen neuer Modelle zur Targeted Mailing-Struktur &#40;Lernprogramm zu Datamining-Lernprogramm&#41;](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Untersuchen der Targeted Mailing-Modelle &#40;Lernprogramm zu Datamining-Lernprogramm&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Datamining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  