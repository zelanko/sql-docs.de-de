---
title: Erstellen eine Datenquellensicht (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b64202ccd2b5f420eceeb0287407656dde1cefe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241840"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a>Erstellen einer Datenquellensicht (Lernprogramm zu Data Mining-Grundlagen)
  Eine Datenquellensicht wird für eine Datenquelle erstellt und definiert eine Teilmenge der Daten, die Sie in Miningstrukturen verwenden können. Sie können die Datenquellensicht auch verwenden, um Spalten hinzuzufügen, berechnete Spalten und Aggregate zu erstellen und benannte Sichten hinzuzufügen. Mithilfe von Datenquellensichten können Sie die Daten auswählen, die sich auf Ihr jeweiliges Projekt beziehen, Beziehungen zwischen Tabellen festlegen und die Datenstruktur ohne Änderung der ursprünglichen Datenquelle bearbeiten. Weitere Informationen finden Sie unter [Datenquellsichten in mehrdimensionalen Modellen](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
### <a name="to-create-a-data-source-view"></a>So erstellen Sie eine Datenquellensicht  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Datenquellensichten**, und wählen Sie **neue Datenquellensicht**.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**.  
  
3.  Auf der **Vybrat Zdroj DAT** Seite **relationale Datenquellen**, wählen Sie die Adventure Works DW 2012-Datenquelle, die Sie in der vorhergehenden Aufgabe erstellt. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie eine Datenquelle erstellen möchten, mit der rechten Maustaste **Datenquellen** , und klicken Sie dann auf **neue Datenquelle** des Datenquellen-Assistenten zu starten.  
  
4.  Auf der **Tabellen und Sichten auswählen** Seite, wählen Sie die folgenden Objekte aus, und klicken Sie dann auf den Pfeil nach rechts, um diese in die neue Datenquellensicht aufzunehmen:  
  
    -   **ProspectiveBuyer (Dbo)** -Tabelle potenzieller fahrradkäufer  
  
    -   **vTargetMail (Dbo)** -Ansicht von Verlaufsdaten zu letzten fahrradkäufer  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **Abschließen des Assistenten** Seite, die die Datenquellensicht heißt standardmäßig Adventure Works DW 2012. Ändern Sie den Namen in `Targeted Mailing`, und klicken Sie dann auf **Fertig stellen**.  
  
     Die neue Datenquellensicht wird geöffnet, der **Targeted Mailing.dsv [Entwurf]** Registerkarte.  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Erstellen einer Datenquelle &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Erstellen einer Targeted Mailing-Struktur &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren einer Datenquellensicht &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services.md)  
  
  
