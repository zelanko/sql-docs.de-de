---
description: Allgemeine Vorhersagefunktionen (DMX)
title: Allgemeine Vorhersagefunktionen (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 22fe85d0e51de59d0b25b6a3eb89d29edf655ee4
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726181"
---
# <a name="general-prediction-functions-dmx"></a>Allgemeine Vorhersagefunktionen (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Sie können die **Select** -Anweisung in Data Mining-Erweiterungen (DMX) verwenden, um unterschiedliche Abfrage Typen zu erstellen. Eine Abfrage kann verwendet werden, um Informationen zum Miningmodell selbst zurückzugeben, neue Vorhersagen zu treffen oder das Modell durch Trainieren mit neuen Daten zu ändern. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt eine Reihe von spezialisierten Funktionen bereit, die den Typ der Informationen steuern, die in einer Abfrage zurückgegeben werden. Durch Hinzufügen dieser Funktionen zu einer DMX-Abfrage können Sie zusätzliche statistische Daten oder Datenspalten abrufen. Jeder Abfragetyp und jeder Modelltyp unterstützt jedoch nur bestimmte Funktionen.  
  
## <a name="common-functions"></a>Allgemeine Funktionen  
 Mit Funktionen können Sie die Ergebnisse erweitern, die von einem Miningmodell zurückgegeben werden. Die folgenden Funktionen können für jede **Select** -Anweisung verwendet werden, die einen Tabellen Ausdruck zurückgibt:  

:::row:::
    :::column:::
        [BottomCount &#40;DMX-&#41;](../dmx/bottomcount-dmx.md)  
        [&#40;DMX-&#41;im unteren Prozentsatz ](../dmx/bottompercent-dmx.md)  
        [Predict &#40;DMX&#41;](../dmx/predict-dmx.md)  
        [Rangemax &#40;DMX-&#41;](../dmx/rangemax-dmx.md)  
        [RangeMid &#40;DMX-&#41;](../dmx/rangemid-dmx.md)  
    :::column-end:::
    :::column:::
        [RangeMin &#40;DMX-&#41;](../dmx/rangemin-dmx.md)  
        [TopCount &#40;DMX-&#41;](../dmx/topcount-dmx.md)  
        [Topprozent &#40;DMX-&#41;](../dmx/toppercent-dmx.md)  
        [TopSum &#40;DMX-&#41;](../dmx/topsum-dmx.md)  
    :::column-end:::
:::row-end:::

 Außerdem werden die folgenden Funktionen für fast alle Modelltypen unterstützt:  
  
-   [Vorhanden &#40;DMX-&#41;](../dmx/exists-dmx.md)  
  
-   [IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)  
  
-   [IsTestCase &#40;DMX-&#41;](../dmx/istestcase-dmx.md)  
  
-   [IsTrainingCase &#40;DMX-&#41;](../dmx/istrainingcase-dmx.md)  
  
-   [Predict &#40;DMX&#41;](../dmx/predict-dmx.md)  
  
-   [Rangemax &#40;DMX-&#41;](../dmx/rangemax-dmx.md)  
  
-   [RangeMid &#40;DMX-&#41;](../dmx/rangemid-dmx.md)  
  
-   [RangeMin &#40;DMX-&#41;](../dmx/rangemin-dmx.md)  
  
-   [Structurecolren &#40;DMX-&#41;](../dmx/structurecolumn-dmx.md)  
  
 Einzelne Algorithmen unterstützen möglicherweise weitere Funktionen. Eine Liste der Funktionen, die von den einzelnen Modelltypen unterstützt werden, finden Sie unter [Data Mining-Abfragen](/analysis-services/data-mining/data-mining-queries).  
  
## <a name="functions-specific-to-select-syntax"></a>Spezielle Funktionen für die SELECT-Syntax  
 In der folgenden Tabelle sind die Funktionen aufgelistet, die Sie für jeden Typ von **Select** -Anweisung verwenden können.  
  
 Allgemeine Informationen zu Funktionen in DMX finden Sie unter [Data Mining Extensions &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md).  
  
|Abfragetyp|Unterstützte Funktionen|Bemerkungen|  
|----------------|-------------------------|-------------|  
|[SELECT DISTINCT FROM \<model>](../dmx/select-distinct-from-model-dmx.md)|[RangeMin &#40;DMX-&#41;](../dmx/rangemin-dmx.md)<br /><br /> [RangeMid &#40;DMX-&#41;](../dmx/rangemid-dmx.md)<br /><br /> [Rangemax &#40;DMX-&#41;](../dmx/rangemax-dmx.md)|Mit diesen Funktionen können maximale Werte, minimale Werte und Durchschnittswerte für jede Spalte angegeben werden, die einen numerischen Datentyp enthält. Dies ist unabhängig davon, ob die Spalte kontinuierliche oder diskrete Werte enthält.|  
|[SELECT FROM \<model>.CONTENT](../dmx/select-from-model-content-dmx.md)<br /><br /> oder<br /><br /> [SELECT FROM \<model>.DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)|[IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)|Mit dieser Funktion werden untergeordnete Knoten für den angegebenen Knoten im Modell abgerufen. Die Funktion kann beispielsweise zum Durchlaufen der Knoten im Miningmodellinhalt verwendet werden. Die Anordnung der Knoten im Miningmodellinhalt hängt vom Modeltyp ab. Weitere Informationen zur Struktur für jeden Mining Modelltyp finden Sie unter [Mining Model Content &#40;Analysis Services-Data Mining&#41;](/analysis-services/data-mining/mining-model-content-analysis-services-data-mining).<br /><br /> Wenn Sie den Mining Modell Inhalt als Dimension gespeichert haben, können Sie auch andere MDX-Funktionen (Multidimensional Expressions) verwenden, die zum Abfragen einer Attribut Hierarchie verfügbar sind.|  
|[SELECT FROM \<model>.CASES](../dmx/select-from-model-cases-dmx.md)|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)<br /><br /> [ClientSettingsGeneralFlag-Klasse](../relational-databases/wmi-provider-configuration-classes/clientsettingsgeneralflag-class/clientsettingsgeneralflag-class.md)<br /><br /> [IsTrainingCase &#40;DMX-&#41;](../dmx/istrainingcase-dmx.md)<br /><br /> [IsTestCase &#40;DMX-&#41;](../dmx/istestcase-dmx.md)|Die lag-Funktion wird nur für Zeitreihen Modelle unterstützt.<br /><br /> Die IsTestCase-Funktion wird in Modellen unterstützt, die auf einer Struktur basieren, die mithilfe der Option "zurück gehaltene Daten" erstellt wurde, um ein Test Dataset zu erstellen. Wenn das Modell nicht auf einer Struktur mit einem Zurückhaltungstestdataset basiert, werden alle Fälle als Trainingsfälle interpretiert.|  
|[SELECT FROM \<model>.SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md)|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)|In diesem Kontext gibt die IsInNode-Funktion einen Fall zurück, der zu einem Satz idealisierter Beispiel Fälle gehört.|  
|Wählen Sie aus \<model> . PMML|Nicht zutreffend Verwenden Sie stattdessen XML-Abfragefunktionen.|PMML-Darstellungen werden nur für die folgenden Modelltypen unterstützt:<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering|  
|[SELECT FROM \<model> PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)|Vorhersagefunktionen, die speziell für den Algorithmus verwendet werden, mit dem Sie das Modell erstellen.|Eine Liste der Vorhersagefunktionen für die einzelnen Modelltypen finden Sie unter [Data Mining-Abfragen](/analysis-services/data-mining/data-mining-queries).|  
|[Select from \<model>](../dmx/select-from-model-dmx.md)|Vorhersagefunktionen, die speziell für den Algorithmus verwendet werden, mit dem Sie das Modell erstellen.|Eine Liste der Vorhersagefunktionen für die einzelnen Modelltypen finden Sie unter [Data Mining-Abfragen](/analysis-services/data-mining/data-mining-queries).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Struktur und Verwendung von DMX-Vorhersage Abfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
