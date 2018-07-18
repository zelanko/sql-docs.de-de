---
title: Allgemeine Vorhersagefunktionen (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c8de92033c58f2583fc7ba93e6c326d4a406c90a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37985432"
---
# <a name="general-prediction-functions-dmx"></a>Allgemeine Vorhersagefunktionen (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Können Sie die **wählen** Anweisung im Data Mining Extensions (DMX) auf verschiedene Arten von Abfragen zu erstellen. Eine Abfrage kann verwendet werden, um Informationen zum Miningmodell selbst zurückzugeben, neue Vorhersagen zu treffen oder das Modell durch Trainieren mit neuen Daten zu ändern. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet eine Vielzahl von spezialisierten Funktionen, die die Art der Informationen zu steuern, die in einer Abfrage zurückgegeben wird. Durch Hinzufügen dieser Funktionen zu einer DMX-Abfrage können Sie zusätzliche statistische Daten oder Datenspalten abrufen. Jeder Abfragetyp und jeder Modelltyp unterstützt jedoch nur bestimmte Funktionen.  
  
## <a name="common-functions"></a>Allgemeine Funktionen  
 Mit Funktionen können Sie die Ergebnisse erweitern, die von einem Miningmodell zurückgegeben werden. Sie können die folgenden Funktionen für alle **wählen** -Anweisung, die einen Tabellenausdruck zurückgibt:  
  
|||  
|-|-|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|[RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)|  
|[BottomPercent &#40;DMX&#41;](../dmx/bottompercent-dmx.md)|[TopCount &#40;DMX&#41;](../dmx/topcount-dmx.md)|  
|[Vorhersagen &#40;DMX&#41;](../dmx/predict-dmx.md)|[TopPercent &#40;DMX&#41;](../dmx/toppercent-dmx.md)|  
|[RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)|[TopSum &#40;DMX&#41;](../dmx/topsum-dmx.md)|  
|[RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)||  
  
 Außerdem werden die folgenden Funktionen für fast alle Modelltypen unterstützt:  
  
-   [Vorhanden &#40;DMX&#41;](../dmx/exists-dmx.md)  
  
-   [IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)  
  
-   [IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)  
  
-   [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md)  
  
-   [Vorhersagen &#40;DMX&#41;](../dmx/predict-dmx.md)  
  
-   [RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)  
  
-   [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)  
  
-   [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
-   [StructureColumn &#40;DMX&#41;](../dmx/structurecolumn-dmx.md)  
  
 Einzelne Algorithmen unterstützen möglicherweise weitere Funktionen. Eine Liste der Funktionen, die von jedem Modelltyp unterstützt werden, finden Sie unter [Data Mining-Abfragen](../analysis-services/data-mining/data-mining-queries.md).  
  
## <a name="functions-specific-to-select-syntax"></a>Spezielle Funktionen für die SELECT-Syntax  
 Die folgende Tabelle enthält die Funktionen, mit denen Sie für jeden Typ von **wählen** Anweisung.  
  
 Allgemeine Informationen zu Funktionen in DMX finden Sie unter [Data Mining-Erweiterungen &#40;DMX&#41; Funktionsverweis](../dmx/data-mining-extensions-dmx-function-reference.md).  
  
|Abfragetyp|Unterstützte Funktionen|Hinweise|  
|----------------|-------------------------|-------------|  
|[SELECT DISTINCT FROM \<Modell >](../dmx/select-distinct-from-model-dmx.md)|[RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)<br /><br /> [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)<br /><br /> [RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)|Mit diesen Funktionen können maximale Werte, minimale Werte und Durchschnittswerte für jede Spalte angegeben werden, die einen numerischen Datentyp enthält. Dies ist unabhängig davon, ob die Spalte kontinuierliche oder diskrete Werte enthält.|  
|[SELECT FROM \<Modell >. INHALT](../dmx/select-from-model-content-dmx.md)<br /><br /> oder<br /><br /> [SELECT FROM \<Modell >. DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)|[IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)|Mit dieser Funktion werden untergeordnete Knoten für den angegebenen Knoten im Modell abgerufen. Die Funktion kann beispielsweise zum Durchlaufen der Knoten im Miningmodellinhalt verwendet werden. Die Anordnung der Knoten im Miningmodellinhalt hängt vom Modeltyp ab. Informationen über die Struktur für jeden Mining-Modelltyp finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).<br /><br /> Wenn Sie den Miningmodellinhalt als Dimension gespeichert haben, können Sie auch andere Multidimensional Expressions-Funktionen (MDX) verwenden, die für die Abfrage in einer Attributhierarchie verfügbar sind.|  
|[SELECT FROM \<Modell >. FÄLLEN](../dmx/select-from-model-cases-dmx.md)|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)<br /><br /> [ClientSettingsGeneralFlag-Klasse](../relational-databases/wmi-provider-configuration-classes/clientsettingsgeneralflag-class/clientsettingsgeneralflag-class.md)<br /><br /> [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md)<br /><br /> [IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)|Die Lag-Funktion ist nur für zeitreihenmodelle unterstützt.<br /><br /> Die IsTestCase-Funktion wird in Modellen unterstützt, die auf einer Struktur basieren, die mit der Option Zurückgehaltene Daten, erstellen Sie ein testdataset erstellt wurde. Wenn das Modell nicht auf einer Struktur mit einem Zurückhaltungstestdataset basiert, werden alle Fälle als Trainingsfälle interpretiert.|  
|[SELECT FROM \<Modell >. SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md)|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)|In diesem Fall gibt die IsInNode-Funktion einen Fall, der auf einen Satz von Beispielfälle gehört.|  
|SELECT FROM \<Modell >. PMML|Nicht verfügbar. Verwenden Sie stattdessen XML-Abfragefunktionen.|PMML-Darstellungen werden nur für die folgenden Modelltypen unterstützt:<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering|  
|[SELECT FROM \<Model > PREDICTION JOIN-Anweisung](../dmx/select-from-model-prediction-join-dmx.md)|Vorhersagefunktionen, die speziell für den Algorithmus verwendet werden, mit dem Sie das Modell erstellen.|Eine Liste der Vorhersagefunktionen für jeden Modelltyp, finden Sie unter [Data Mining-Abfragen](../analysis-services/data-mining/data-mining-queries.md).|  
|[SELECT FROM \<Modell >](../dmx/select-from-model-dmx.md)|Vorhersagefunktionen, die speziell für den Algorithmus verwendet werden, mit dem Sie das Modell erstellen.|Eine Liste der Vorhersagefunktionen für jeden Modelltyp, finden Sie unter [Data Mining-Abfragen](../analysis-services/data-mining/data-mining-queries.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Verweis](../dmx/data-mining-extensions-dmx-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Syntaxkonventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Syntaxelemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Struktur und Verwendung von DMX-Vorhersageabfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
