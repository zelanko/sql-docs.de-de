---
title: Verarbeiten von Modellen in der Ziel-Mailing Struktur (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d8233bb-117e-4563-9302-8a5a8ad1fae2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 605088d405cbd2dcfba92a2da5fa4e07c38d8f0b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63188226"
---
# <a name="processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>Verarbeiten von Modellen in der Targeted Mailing-Struktur (Lernprogramm zu Data Mining-Grundlagen)
  Bevor Sie die erstellten Miningmodelle durchsuchen und verwenden können, müssen Sie das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Projekt bereitstellen und die Miningstruktur und die Miningmodelle verarbeiten.  
  
-   Bei der Bereitstellung wird das Projekt an einen *Server gesendet,* und es werden alle Objekte in diesem Projekt auf dem Server erstellt.  
  
-   *Processing* Bei der Verarbeitung [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] werden-Objekte mit Daten aus relationalen Datenquellen aufgefüllt.  
  
 Modelle können erst dann verwendet werden, wenn sie bereitgestellt und verarbeitet wurden. Wenn Sie Änderungen am Modell vornehmen, z. B. neue Daten hinzufügen, müssen Sie die Modelle darüber hinaus erneut bereitstellen und verarbeiten.  
  
## <a name="ensuring-consistency-with-holdoutseed"></a>Sicherstellen von Konsistenz mit HoldoutSeed  
 Wenn Sie ein Projekt bereitstellen und die Struktur sowie die Modelle verarbeiten, werden die einzelnen Zeilen in der Datenstruktur auf Grundlage eines numerischen Ausgangswerts entweder dem Trainings- oder Testsatz zugewiesen. Der numerische Ausgangswert wird in der Regel auf der Basis von Attributen der Datenstruktur berechnet. Bei einer Änderung der Modellaspekte würde sich der Ausgangswert jedoch ändern und zu leicht abweichenden Ergebnissen führen. Um sicherzustellen, dass Ihre Ergebnisse den hier beschriebenen entsprechen, weisen wir daher willkürlich *einen festgehaltenen* Ausgangswert von `12`zurück. Mit dem Ausgangswert zurückgehaltener Daten wird der Stichprobenalgorithmus initialisiert, und es wird sichergestellt, dass die Daten für alle Miningstrukturen und deren Modelle weitestgehend auf die gleiche Weise partitioniert werden.  
  
 Dieser Wert hat keinen Einfluss auf die Anzahl der Fälle im Trainingssatz, sondern stellt lediglich sicher, dass bei jeder Modellerstellung dieselbe Partitionierungsmethode verwendet wird.  
  
 Weitere Informationen zum Ausgangswert für zurück gehaltene Daten finden Sie unter [Trainings-und Test Datasets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).  
  
#### <a name="to-set-the-holdout-seed"></a>So legen Sie den Ausgangswert zurückgehaltener Daten fest  
  
1.  Klicken Sie im Data Mining-Designer von auf die Registerkarte **Mining Struktur** oder auf [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]die Registerkarte **Mining Modelle** .  
  
     Die **Ziel-Mailing-Mining Struktur** wird im **Eigenschaften** Bereich angezeigt.  
  
2.  Stellen Sie sicher, dass der Bereich **Eigenschaften** durch Drücken von **F4**geöffnet ist.  
  
3.  Stellen Sie sicher, dass **CacheMode** auf **KeepTrainingCases**festgelegt ist.  
  
4.  Geben `12` Sie für **HoldoutSeed**ein.  
  
## <a name="deploying-and-processing-the-models"></a>Bereitstellen und Verarbeiten der Modelle  
 Im Data Mining-Designer können Sie entscheiden, welche Objekte verarbeitet werden sollen, abhängig vom Umfang der Änderungen, die Sie am Modell oder den zugrunde liegenden Daten vorgenommen haben:  
  
 Bei dieser Aufgabe verarbeiten Sie die Struktur und alle Modelle gleichzeitig, weil die Daten und Modelle neu sind.  
  
#### <a name="to-deploy-the-project-and-process-all-the-mining-models"></a>So stellen Sie das Projekt bereit und verarbeiten alle Miningmodelle  
  
1.  Wählen Sie im Menü **Mining Modell** die Option **Mining Struktur und alle Modelle verarbeiten**aus.  
  
     Falls Sie Änderungen an der Miningstruktur vorgenommen haben, werden Sie aufgefordert, das Projekt zu erstellen und bereitzustellen, bevor Sie die Modelle verarbeiten. Klicken Sie auf **Ja**.  
  
2.  Klicken Sie im Dialogfeld **Verarbeitungs Mining Struktur-Ziel** senden auf **Ausführen** .  
  
     Das Dialogfeld **Verarbeitungsstatus** wird geöffnet und zeigt detaillierte Informationen zur Verarbeitung des Modells an. Die Modell Verarbeitung kann je nach Computer einige Zeit in Anspruch nehmen.  
  
3.  Klicken Sie nach Abschluss der Modellverarbeitung im Dialogfeld **Verarbeitungsstatus** auf **Schließen** .  
  
4.  Klicken Sie im Dialogfeld **Mining Struktur verarbeiten \<-Struktur>** auf **Schließen** .  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Hinzufügen neuer Modelle zur Ziel-Mailing-Struktur &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Untersuchen der Ziel-Mailing-Modelle &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
