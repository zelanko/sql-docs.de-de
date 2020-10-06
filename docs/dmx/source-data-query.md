---
description: '&lt;Quelldaten Abfrage&gt;'
title: '&lt;Quelldaten Abfrage &gt; | Microsoft-Dokumentation'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9dbceb416cea3e64200708639a771989f900be3e
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726117"
---
# <a name="ltsource-data-querygt"></a>&lt;Quelldaten Abfrage&gt;
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Wenn Sie ein Data Mining Modell trainieren und Vorhersagen aus einem Mining Modell erstellen möchten, müssen Sie auf Daten zugreifen, die sich außerhalb der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenbank befinden. Verwenden Sie die- \<source data query> Klausel in Data Mining-Erweiterungen (DMX), um diese externen Daten zu definieren. Wenn Sie [in &#40;DMX-&#41;einfügen ](../dmx/insert-into-dmx.md), [Wählen Sie aus &#60;Modell&#62; Vorhersage Verknüpfung &#40;DMX-&#41;aus ](../dmx/select-from-model-prediction-join-dmx.md), und [Wählen Sie aus natürlichen Vorhersage Join](../dmx/select-from-model-prediction-join-dmx.md) -Anweisungen, die **\<source data query>** alle verwenden  
  
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
 [&#40;Analysis Services Data Mining-&#41;](/analysis-services/data-mining/nested-tables-analysis-services-data-mining)  
  
