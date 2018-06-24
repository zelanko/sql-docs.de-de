---
title: Ändern der Diskretisierung von Spalten in einem Miningmodell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cc0352074e37bf284bd4ea033bae759638e040a6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058197"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>Ändern der Diskretisierung von Spalten in Miningmodellen
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diskretisiert automatisch Werte, d. h., in bestimmten Szenarien werden Daten in numerischen Spalten klassifiziert. Wenn die Daten zum Beispiel fortlaufende numerische Daten enthalten und Sie ein Entscheidungsstrukturmodell erstellen, wird jede Spalte mit fortlaufenden Daten abhängig von der Verteilung der Daten automatisch klassifiziert. Wenn Sie steuern möchten, wie die Daten diskretisiert werden, müssen Sie die Eigenschaften der Spalte "Miningstruktur" ändern, die steuern, wie die Daten im Modell verwendet werden.  
  
 Allgemeine Informationen zum Festlegen der Eigenschaften eines Miningmodells finden Sie unter [Miningmodellspalten](mining-model-columns.md).  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>So zeigen Sie die Eigenschaften einer Miningmodellspalte an  
  
1.  Klicken Sie im Data Mining-Designer auf der Registerkarte **Miningmodelle** mit der rechten Maustaste entweder auf den Spaltenheader, der den Namen des Miningmodells enthält, oder auf die Zeile des Rasters mit dem Namen des Miningalgorithmus. Wählen Sie anschließend **Eigenschaften**aus.  
  
     Das Fenster **Eigenschaften** zeigt die Eigenschaften an, die dem Miningmodell insgesamt zugeordnet sind.  
  
2.  Klicken Sie in der Spalte **Struktur** an der linken Seite des Bildschirms auf die Spalte, die die fortlaufenden numerischen Daten enthält, die Sie diskretisieren möchten.  
  
     Das Fenster **Eigenschaften** zeigt die Eigenschaften an, die dieser Spalte zugeordnet sind.  
  
### <a name="to-change-the-discretization-method"></a>So ändern Sie die Diskretisierungsmethode  
  
1.  In der **Data Mining-Eigenschaften** Fenster, klicken Sie auf das Textfeld neben **Content**, und wählen Sie `Discretized` aus der Dropdownliste aus.  
  
     Das Fenster <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> und <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> sind nun aktiviert.  
  
2.  In der **Eigenschaften** Fenster, klicken Sie auf das Textfeld neben <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> und wählen Sie eine der folgenden Werte: `Automatic`, `EqualAreas`, oder `Cluster`.  
  
    > [!NOTE]  
    >  Wenn die Spaltenverwendung, um festgelegt ist `Ignore`, **Eigenschaften** Fenster für die Spalte ist leer.  
  
     Der neue Wert wird wirksam, wenn Sie ein anderes Element im Designer auswählen.  
  
3.  Klicken Sie im Data Mining-Designer auf der Registerkarte **Eigenschaften** neben <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> , und geben Sie einen numerischen Wert ein.  
  
    > [!NOTE]  
    >  Wenn Sie diese Eigenschaften ändern, muss die Struktur zusammen mit allen Modellen, in denen Sie die neue Einstellung verwenden möchten, neu verarbeitet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodelltasks und -anweisungen](mining-model-tasks-and-how-tos.md)  
  
  