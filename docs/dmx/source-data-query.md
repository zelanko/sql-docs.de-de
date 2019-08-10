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
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892344"
---
# <a name="ltsource-data-querygt"></a>&lt;Quelldaten Abfrage&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Wenn Sie ein Data Mining Modell trainieren und Vorhersagen aus einem Mining Modell erstellen möchten, müssen Sie auf Daten zugreifen, die [!INCLUDE[msCoName](../includes/msconame-md.md)] sich außerhalb der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenbank befinden. Sie verwenden die \<Quelldaten Abfrage >-Klausel in Data Mining-Erweiterungen (DMX), um diese externen Daten zu definieren. Die [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md), [Select from &#60;Model&#62; Vorhersage Join &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)und [Select from Natural Vorhersage Join](../dmx/select-from-model-prediction-join-dmx.md) -Anweisungen verwenden **\<Quelldaten Abfrage >** .  
  
## <a name="query-types"></a>Abfragetypen  
 Die drei häufigsten Arten zum Angeben von Quelldaten sind:  
  
 [OPENQUERY &#40;DMX&#41;](../dmx/source-data-query-openquery.md)  
 Diese Anweisung fragt Daten ab, die für eine Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] externe Daten sind. Dazu wird eine vorhandene Datenquelle verwendet.  
  
 Obwohl **OPENQUERY** in der Funktion zu **OPENROWSET**ähnlich ist, bietet **OPENQUERY** die folgenden Vorteile:  
  
-   Eine DMX-Abfrage ist mit **OPENQUERY**viel einfacher zu schreiben. Statt jedes Mal, wenn Sie eine Abfrage schreiben, eine neue Verbindungszeichenfolge zu erstellen, können Sie die vorhandene Verbindungszeichenfolge in der Datenquelle nutzen. Das Datenquellenobjekt kann außerdem den Datenzugriff für einzelne Benutzer steuern.  
  
-   Der Administrator kann besser steuern, wie auf die Daten auf dem Server zugegriffen wird. Beispielsweise kann der Administrator festlegen, welche Anbieter in den Server geladen werden und auf welche externen Daten zugegriffen werden kann.  
  
 [OPENROWSET &#40;DMX&#41;](../dmx/source-data-query-openrowset.md)  
 Diese Anweisung fragt Daten ab, die für eine Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] externe Daten sind. Dazu wird eine vorhandene Datenquelle verwendet.  
  
 [FORM &#40;DMX&#41;](../dmx/source-data-query-shape.md)  
 Diese Anweisung fragt mehrere Datenquellen ab, um eine geschachtelte Tabelle zu erstellen. Mithilfe von **Form**können Sie Daten aus mehreren Quellen in einer einzigen hierarchischen Tabelle kombinieren. Auf diese Weise können Sie die Möglichkeit von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nutzen, Tabellen zu schachteln, indem eine Tabelle in eine andere Tabelle eingebettet wird.  
  
 Zur Angabe der Quelldaten haben Sie folgende Möglichkeiten:  
  
-   Eine gültige DMX-Anweisung  
  
-   Eine gültige MDX-Anweisung (Multidimensional Expressions)  
  
-   Eine Tabelle, die eine gespeicherte Prozedur zurückgibt  
  
-   Ein XMLA-Rowset (XML for Analysis)  
  
-   Ein Rowsetparameter  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining- &#40;Erweiterungen DMX&#41; -Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [DMX&#41; - &#40;Anweisungs Referenz für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-statements.md)   
 [Analysis Services Data Mining &#40;-Tabellen&#41;](https://docs.microsoft.com/analysis-services/data-mining/nested-tables-analysis-services-data-mining)  
  
  
