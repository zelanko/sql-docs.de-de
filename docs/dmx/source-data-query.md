---
title: '&lt;Quelldaten Abfrage&gt; | Microsoft-Dokumentation'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e523d33da502a971b950e33ec0bd935149ed26f7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68892344"
---
# <a name="ltsource-data-querygt"></a>&lt;Quelldaten Abfrage&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Wenn Sie ein Data Mining Modell trainieren und Vorhersagen aus einem Mining Modell erstellen möchten, müssen Sie auf Daten zugreifen, die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sich außerhalb der Datenbank befinden. Sie verwenden die \<Quelldaten Abfrage>-Klausel in Data Mining-Erweiterungen (DMX), um diese externen Daten zu definieren. Die [INSERT INTO &#40;DMX-&#41;](../dmx/insert-into-dmx.md), [Wählen Sie aus &#60;Modell&#62; Vorhersage Verknüpfung &#40;DMX-&#41;aus ](../dmx/select-from-model-prediction-join-dmx.md), und [Wählen Sie from Natural Vorhersage Join](../dmx/select-from-model-prediction-join-dmx.md) -Anweisungen aus, die alle ** \<Quelldaten Abfrage>** verwenden.  
  
## <a name="query-types"></a>Abfragetypen  
 Die drei häufigsten Arten zum Angeben von Quelldaten sind:  
  
 [OPENQUERY-&#40;DMX-&#41;](../dmx/source-data-query-openquery.md)  
 Diese Anweisung fragt Daten ab, die für eine Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] externe Daten sind. Dazu wird eine vorhandene Datenquelle verwendet.  
  
 Obwohl **OPENQUERY** in der Funktion zu **OPENROWSET**ähnlich ist, bietet **OPENQUERY** die folgenden Vorteile:  
  
-   Eine DMX-Abfrage ist mit **OPENQUERY**viel einfacher zu schreiben. Statt jedes Mal, wenn Sie eine Abfrage schreiben, eine neue Verbindungszeichenfolge zu erstellen, können Sie die vorhandene Verbindungszeichenfolge in der Datenquelle nutzen. Das Datenquellenobjekt kann außerdem den Datenzugriff für einzelne Benutzer steuern.  
  
-   Der Administrator kann besser steuern, wie auf die Daten auf dem Server zugegriffen wird. Beispielsweise kann der Administrator festlegen, welche Anbieter in den Server geladen werden und auf welche externen Daten zugegriffen werden kann.  
  
 [OPENROWSET &#40;DMX-&#41;](../dmx/source-data-query-openrowset.md)  
 Diese Anweisung fragt Daten ab, die für eine Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] externe Daten sind. Dazu wird eine vorhandene Datenquelle verwendet.  
  
 [Form &#40;DMX-&#41;](../dmx/source-data-query-shape.md)  
 Diese Anweisung fragt mehrere Datenquellen ab, um eine geschachtelte Tabelle zu erstellen. Mithilfe von **Form**können Sie Daten aus mehreren Quellen in einer einzigen hierarchischen Tabelle kombinieren. Auf diese Weise können Sie die Möglichkeit von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nutzen, Tabellen zu schachteln, indem eine Tabelle in eine andere Tabelle eingebettet wird.  
  
 Zur Angabe der Quelldaten haben Sie folgende Möglichkeiten:  
  
-   Eine gültige DMX-Anweisung  
  
-   Eine gültige MDX-Anweisung (Multidimensional Expressions)  
  
-   Eine Tabelle, die eine gespeicherte Prozedur zurückgibt  
  
-   Ein XMLA-Rowset (XML for Analysis)  
  
-   Ein Rowsetparameter  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [&#40;Analysis Services Data Mining-&#41;](https://docs.microsoft.com/analysis-services/data-mining/nested-tables-analysis-services-data-mining)  
  
  
