---
title: Angeben eines Testdatasets für die Struktur (Lernprogramm zu Datamining-Lernprogramm) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75cd508f-b126-418b-848d-3c4c3e6c303f
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2023672b21e8ffde191b400329031895d200e1ea
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312628"
---
# <a name="specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial"></a>Angeben eines Testdatasets für die Struktur (Lernprogramm zu Data Mining-Grundlagen)
  Auf den letzten Seiten des Data Mining-Assistenten teilen Sie Ihre Daten in einen Testsatz und einen Trainingssatz auf. Anschließend benennen Sie die Struktur und aktivieren Drillthrough für das Modell.  
  
## <a name="specifying-a-testing-set"></a>Angeben eines Testsatzes  
 Indem die Daten beim Erstellen einer Miningstruktur in einen Trainings- und einen Testsatz aufgeteilt werden, wird die Beurteilung der Genauigkeit von Miningmodellen, die Sie zu einem späteren Zeitpunkt erstellen, erheblich vereinfacht. Weitere Informationen zu testsätzen finden Sie unter [Trainings- und Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).  
  
#### <a name="to-specify-the-testing-set"></a>So geben Sie den Testsatz an  
  
1.  Auf der **Testsatz erstellen** Seite für **Prozentsatz der Testdaten**, behalten Sie den Standardwert des `30`.  
  
2.  Für **maximale Anzahl von Fällen in Testdatensatz**, Typ `1000`.  
  
3.  Klicken Sie auf **Weiter**.  
  
## <a name="specifying-drillthrough"></a>Angeben von Drillthrough  
 Drillthrough kann für Modelle und für Strukturen aktiviert werden. Durch das Kontrollkästchen in diesem Dialogfeld wird der Drillthrough für das benannte Modell aktiviert. Nach der Verarbeitung des Modells können Sie detaillierte Informationen aus den Trainingsdaten abrufen, die zur Modellerstellung verwendet wurden.  
  
 Wenn auch in der zugrunde liegenden Miningstruktur die Verwendung von Drillthrough konfiguriert wurde, können Sie detaillierte Informationen sowohl aus den Modellfällen als auch aus der Miningstruktur abrufen, einschließlich Spalten, die nicht im Miningmodell enthalten sind. Weitere Informationen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-name-the-model-and-structure-and-specify-drillthrough"></a>So benennen Sie das Modell und die Struktur und geben Drillthrough an  
  
1.  Auf der **Abschließen des Assistenten** Seite **Miningstrukturname**, Typ `Targeted Mailing`.  
  
2.  In **Miningmodellname**, Typ `TM_Decision_Tree`.  
  
3.  Wählen Sie die **Drillthrough zulassen** Kontrollkästchen.  
  
4.  Überprüfen Sie die **Vorschau** Bereich. Beachten Sie, dass nur die Spalten, die als ausgewählt **Schlüssel**, **Eingabe** oder **vorhersagbar** werden angezeigt. Die anderen ausgewählten Spalten, z. B. AddressLine1, werden nicht zum Erstellen des Modells verwendet. Sie sind jedoch in der zugrunde liegenden Struktur verfügbar und können nach Verarbeitung und Bereitstellung des Modells abgefragt werden.  
  
5.  Klicken Sie auf **Fertig stellen**.  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Angeben von den Daten- und Inhaltstyp &#40;Lernprogramm zu Datamining-Lernprogramm&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Hinzufügen und Verarbeiten von Modellen](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren von Drillthrough für ein Miningmodell](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)   
 [Drillthroughabfragen &#40;Datamining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Geben Sie die Trainingsdaten &#40;Datamining-Assistenten&#41;](../../2014/analysis-services/specify-the-training-data-data-mining-wizard.md)  
  
  