---
title: Verarbeiten von Data Mining-Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- processing objects [Analysis Services]
- mining structures [Analysis Services]
- process [Analysis Services]
- mining structures [Analysis Services], creating
- mining structures [Analysis Services], how-to topics
- mining structures [Analysis Services], processing
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4a6693a46679badc068111a311bb82219e752cd
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84520756"
---
# <a name="processing-data-mining-objects"></a>Verarbeiten von Data Mining-Objekten
  Ein Data Mining-Objekt ist vor seiner Verarbeitung nur ein leerer Container. Die*Verarbeitung* eines Data Mining-Modells wird auch als *Training*bezeichnet.  
  
 **Verarbeiten von Miningstrukturen:** Eine Miningstruktur ruft Daten von einer externen Datenquelle ab, die über die Spaltenbindungen und Verwendungsmetadaten definiert ist, und liest die Daten. Diese Daten werden vollständig gelesen und anschließend analysiert, um verschiedene statistische Informationen zu extrahieren. Analysis Services speichert eine kurze Darstellung der Daten, die für die Analyse durch Data Mining-Algorithmen geeignet ist, in einem lokalen Cache. Sie können diesen Cache entweder beibehalten oder löschen, nachdem die Modelle verarbeitet wurden. Standardmäßig wird der Cache gespeichert. Weitere Informationen finden Sie unter [Process a Mining Structure](process-a-mining-structure.md).  
  
 **Verarbeiten von Miningmodellen:** Bis zu seiner Verarbeitung ist ein Miningmodell leer und enthält nur Definitionen. Um ein Miningmodell verarbeiten zu können, muss zuerst die zugrunde liegende Miningstruktur verarbeitet werden. Das Miningmodell erhält die Daten aus dem Cache der Miningstruktur, wendet die Filter an, die ggf. für das Modell erstellt wurden, und übergibt dann das Dataset über den Algorithmus, um Muster zu ermitteln. Nachdem das Modell verarbeitet wurde, speichert das Modell nur die Ergebnisse der Verarbeitung, nicht die Daten selbst. Weitere Informationen finden Sie unter [Verarbeiten eines Miningmodells](process-a-mining-model.md).  
  
 In der folgenden Abbildung ist jeweils der Datenfluss für die Verarbeitung einer Miningstruktur und für die Verarbeitung eines Miningmodells dargestellt.  
  
 ![Datenverarbeitung: Quelle-zu-Struktur-zu-Modell](../media/dmcon-modelarch.gif "Datenverarbeitung: Quelle-zu-Struktur-zu-Modell")  
  
## <a name="viewing-the-results-of-processing"></a>Anzeigen der Ergebnisse der Verarbeitung  
 Nachdem eine Miningstruktur verarbeitet wurde, enthält sie eine kurze Darstellung der Daten zur Verwendung in statistischen Analysen. Wenn der Cache nicht gelöscht wurde, können Sie wie folgt auf die Daten im Cache zugreifen:  
  
-   Sie können eine DMX-Abfrage (Data Mining Extensions, Data Mining-Erweiterungen) für das Modell erstellen und einen Drillthrough zur Struktur ausführen. Weitere Informationen finden Sie unter [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).  
  
-   Sie können ein Modell basierend auf der Struktur durchsuchen und eine Option der Benutzeroberfläche verwenden, um einen Drillthrough zu den Strukturfällen auszuführen. Weitere Informationen finden Sie unter [Data Mining-Modell-Viewer](data-mining-model-viewers.md)oder [Ausführen von Drillthroughs für Falldaten aus einem Miningmodell](drill-through-to-case-data-from-a-mining-model.md).  
  
-   Erstellen Sie eine DMX-Abfrage für die Strukturfälle. Weitere Informationen finden Sie unter [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).  
  
 Nachdem ein Miningmodell verarbeitet wurde, enthält es nur die Muster, die bei der Analyse ermittelt wurden, sowie die Zuordnungen von den Modellergebnissen zu den im Cache zwischengespeicherten Trainingsdaten. Sie können die Modellergebnisse, die auch als *Modellinhalt*bezeichnet werden, durchsuchen oder abfragen, oder Sie können die Modell- und Strukturfälle abfragen, wenn diese zwischengespeichert wurden.  
  
 Der Modellinhalt eines Miningmodells hängt von dem Algorithmus ab, der für die Erstellung verwendet wurde. Wenn ein Modell beispielsweise ein Clusteringmodell ist und ein anderes Modell ein Entscheidungsstrukturmodell, unterscheidet sich der Modellinhalt stark, obwohl die beiden Modelle dieselben Daten verwenden. Weitere Informationen finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).  
  
## <a name="processing-requirements"></a>Anforderungen für die Verarbeitung  
 Die Anforderungen für die Verarbeitung hängen davon ab, ob die Miningmodelle ausschließlich auf relationalen Daten oder auf einer mehrdimensionaler Datenquelle basieren.  
  
 Bei einer relationalen Datenquelle müssen Sie für die Verarbeitung nur Trainingsdaten erstellen und Miningalgorithmen für diese Daten ausführen. Miningmodelle, die auf OLAP-Objekten, z. B. Dimensionen und Measures, basieren, erfordern jedoch, dass die zugrunde liegenden Daten in einem verarbeiteten Status vorliegen. Hierfür kann es notwendig sein, dass die mehrdimensionalen Objekte verarbeitet werden, um das Miningmodell zu füllen.  
  
 Weitere Informationen finden Sie unter [Anforderungen und Überlegungen zur Verarbeitung &#40;Data Mining&#41;](processing-requirements-and-considerations-data-mining.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Drillthrough-Abfragen &#40;Data Mining-&#41;](drillthrough-queries-data-mining.md)   
 [Mining Strukturen &#40;Analysis Services Data Mining-&#41;](mining-structures-analysis-services-data-mining.md)   
 [Mining Modelle &#40;Analysis Services Data Mining-&#41;](mining-models-analysis-services-data-mining.md)   
 [Logische Architektur &#40;Analysis Services – Data Mining&#41;](logical-architecture-analysis-services-data-mining.md)  
  
  
