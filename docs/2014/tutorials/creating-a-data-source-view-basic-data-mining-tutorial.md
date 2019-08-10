---
title: Erstellen einer Datenquellen Sicht (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ac7730e8437eaed304ed69c40e45fc93ee9b5531
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68888650"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a>Erstellen einer Datenquellensicht (Lernprogramm zu Data Mining-Grundlagen)
  Eine Datenquellensicht wird für eine Datenquelle erstellt und definiert eine Teilmenge der Daten, die Sie in Miningstrukturen verwenden können. Sie können die Datenquellensicht auch verwenden, um Spalten hinzuzufügen, berechnete Spalten und Aggregate zu erstellen und benannte Sichten hinzuzufügen. Mithilfe von Datenquellensichten können Sie die Daten auswählen, die sich auf Ihr jeweiliges Projekt beziehen, Beziehungen zwischen Tabellen festlegen und die Datenstruktur ohne Änderung der ursprünglichen Datenquelle bearbeiten. Weitere Informationen finden Sie unter [Datenquellsichten in mehrdimensionalen Modellen](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models).  
  
### <a name="to-create-a-data-source-view"></a>So erstellen Sie eine Datenquellensicht  
  
1.  Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf **Datenquellen Sichten**, und wählen Sie **neue Datenquellen Sicht**aus.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**.  
  
3.  Wählen Sie auf der Seite **Datenquelle auswählen** unter **relationale Datenquellen**die Datenquelle Adventure Works DW 2012 aus, die Sie in der letzten Aufgabe erstellt haben. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie eine Datenquelle erstellen möchten, klicken Sie mit der rechten Maustaste auf **Datenquellen** , und klicken Sie dann auf **neue Datenquelle** , um den Datenquellen-Assistenten zu starten.  
  
4.  Wählen Sie auf der Seite **Tabellen und Sichten auswählen** die folgenden Objekte aus, und klicken Sie dann auf den Pfeil nach rechts, um Sie in die neue Datenquellen Sicht einzuschließen:  
  
    -   **ProspectiveBuyer (dbo)** -Tabelle potenzieller Fahrrad Käufer  
  
    -   **vTargetMail (dbo)** -Ansicht der Verlaufs Daten zu den bisherigen Fahrrad Käufern  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der Seite **Assistenten abschließen** wird die Datenquellen Sicht standardmäßig Adventure Works DW 2012 benannt. Ändern Sie den Namen `Targeted Mailing`in, und klicken Sie dann auf **Fertig**stellen.  
  
     Die neue Datenquellen Sicht wird in der Ziel Registerkarte " **Mailing. DSV [Entwurf]** " geöffnet.  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Erstellen eines Lernprogramms &#40;zu Data Mining-Grundlagen&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Aufbauen eines Lernprogramms zur &#40;gezielten Mailing-Struktur grundlegender Data Mining&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren einer Datenquellensicht &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services)  
  
  
