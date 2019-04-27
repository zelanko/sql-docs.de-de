---
title: Ändern der Diskretisierung von Spalten in einem Miningmodell | Microsoft-Dokumentation
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8a85b645562ce39f19c15191b6b1d3ba4a7fb332
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62670436"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>Ändern der Diskretisierung von Spalten in Miningmodellen
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diskretisiert automatisch Werte – das heißt, es Klassen, Daten in einer numerischen Spalte in bestimmten Szenarien. Wenn die Daten zum Beispiel fortlaufende numerische Daten enthalten und Sie ein Entscheidungsstrukturmodell erstellen, wird jede Spalte mit fortlaufenden Daten abhängig von der Verteilung der Daten automatisch klassifiziert. Wenn Sie steuern möchten, wie die Daten diskretisiert werden, müssen Sie die Eigenschaften der Spalte "Miningstruktur" ändern, die steuern, wie die Daten im Modell verwendet werden.  
  
 Allgemeine Informationen zum Festlegen der Eigenschaften eines Miningmodells finden Sie unter [Miningmodellspalten](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>So zeigen Sie die Eigenschaften einer Miningmodellspalte an  
  
1.  Klicken Sie im Data Mining-Designer auf der Registerkarte **Miningmodelle** mit der rechten Maustaste entweder auf den Spaltenheader, der den Namen des Miningmodells enthält, oder auf die Zeile des Rasters mit dem Namen des Miningalgorithmus. Wählen Sie anschließend **Eigenschaften**aus.  
  
     Das Fenster **Eigenschaften** zeigt die Eigenschaften an, die dem Miningmodell insgesamt zugeordnet sind.  
  
2.  Klicken Sie in der Spalte **Struktur** an der linken Seite des Bildschirms auf die Spalte, die die fortlaufenden numerischen Daten enthält, die Sie diskretisieren möchten.  
  
     Das Fenster **Eigenschaften** zeigt die Eigenschaften an, die dieser Spalte zugeordnet sind.  
  
### <a name="to-change-the-discretization-method"></a>So ändern Sie die Diskretisierungsmethode  
  
1.  Klicken Sie im Fenster **Data Mining-Eigenschaften** neben **Inhalt**auf das Textfeld, und wählen Sie **Discretized** aus der Dropdownliste aus.  
  
     Das Fenster <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> und <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> sind nun aktiviert.  
  
2.  In der **Eigenschaften** Fenster, auf das Textfeld neben <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> und wählen Sie eine der folgenden Werte: **Automatische**, **EqualAreas**, oder **Cluster**.  
  
    > [!NOTE]  
    >  Wenn die Spaltenverwendung auf **Ignore**festgelegt wird, ist das Fenster **Eigenschaften** für die Spalte leer.  
  
     Der neue Wert wird wirksam, wenn Sie ein anderes Element im Designer auswählen.  
  
3.  Klicken Sie im Data Mining-Designer auf der Registerkarte **Eigenschaften** neben <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> , und geben Sie einen numerischen Wert ein.  
  
    > [!NOTE]  
    >  Wenn Sie diese Eigenschaften ändern, muss die Struktur zusammen mit allen Modellen, in denen Sie die neue Einstellung verwenden möchten, neu verarbeitet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodelltasks und -anweisungen](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
