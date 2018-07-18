---
title: Vorhersagen (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 733e3272bf67347f1e3459a0df5f13225488f677
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38002102"
---
# <a name="predict-dmx"></a>Predict (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die **Predict** Funktion gibt einen vorhergesagten Wert oder eine Gruppe von Werten für eine angegebene Spalte.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Predict(<scalar column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
Predict(<table column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Einen Verweis auf eine skalare Spalte oder einen Verweis auf eine Tabellenspalte.  
  
## <a name="return-type"></a>Rückgabetyp  
 \<Verweis auf skalare Spalte >  
  
 oder  
  
 \<Tabellenreferenz für die Spalte >  
  
 Der Rückgabetyp hängt vom Typ der Spalte ab, auf die diese Funktion angewendet wird.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY und INCLUDE_STATISTICS gelten nur für Verweise auf Tabellenspalten, und EXCLUDE_NULL und INCLUDE_NULL gelten nur für Verweise auf skalare Spalten.  
  
## <a name="remarks"></a>Hinweise  
 Zu den Optionen gehören EXCLUDE_NULL (Standardwert), INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (Standardwert), INPUT_ONLY und INCLUDE_STATISTICS.  
  
> [!NOTE]  
>  Für zeitreihenmodelle unterstützt die Predict-Funktion nicht INCLUDE_STATISTICS.  
  
 Der INCLUDE_NODE_ID-Parameter gibt die $NODEID-Spalte im Ergebnis zurück. NODE_ID ist der Inhaltsknoten, für den die Vorhersage in einem bestimmten Fall ausgeführt wird. Dieser Parameter ist optional, wenn Vorhersagen für Tabellenspalten verwenden.  
  
 Die *n* -Parameter gilt für Tabellenspalten. Er legt fest, wie viele Zeilen entsprechend dem Typ der Vorhersage zurückgegeben werden sollen. Wenn die zugrunde liegende Spalte Sequenz ist, ruft es die **PredictSequence** Funktion. Wenn die zugrunde liegende Spalte zeitreihenspalte ist, ruft es die **PredictTimeSeries** Funktion. Für assoziative Vorhersagen, ruft der **PredictAssociation** Funktion.  
  
 Die **Predict** -Funktion unterstützt Polymorphie.  
  
 Häufig werden die folgenden alternativen Kurzformen verwendet:  
  
-   [Gender] ist eine Alternative für **Predict**([Gender], EXCLUDE_NULL).  
  
-   [Products Purchases] ist eine Alternative für **Predict**([Products Purchases], EXCLUDE_NULL, EXCLUSIVE).  
  
    > [!NOTE]  
    >  Der Rückgabetyp dieser Funktion wird als Spaltenverweis angesehen. Dies bedeutet, dass die **Predict** Funktion kann verwendet werden, als Argument in anderen Funktionen, die einen Spaltenverweis als Argument zu akzeptieren (mit Ausnahme der **Predict** Funktion selbst).  
  
 Die Spalten hinzugefügt INCLUDE_STATISTICS an eine Vorhersage für eine tabellenwertspalte übergeben **$Probability** und **$Support** , die sich ergebende Tabelle. Diese Spalten beschreiben die Wahrscheinlichkeit des Vorhandenseins für den Datensatz der zugeordneten geschachtelten Tabelle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Predict-Funktion geben Sie die vier Produkte in der Adventure Works-Datenbank, die höchstwahrscheinlich zusammen verkauft werden. Da die Funktion für eine Zuordnungsregel Miningmodell vorhergesagt wird, verwendet er automatisch die **PredictAssociation** funktionieren wie zuvor beschrieben.  
  
```  
SELECT  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,4)  
FROM     [Association]  
```  
  
 Beispielergebnisse:  
  
 Diese Abfrage gibt eine einzelne Zeile mit Daten in einer Spalte (`Expression`) zurück, diese Spalte enthält jedoch die folgende geschachtelte Tabelle.  
  
|Model|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016331743|0.252695851192499|  
|Water Bottle|2866|0.192620471805901|0.175205052318795|  
|Patchkit|2113|0.142012232004839|0.132389356196586|  
|Mountain Tire Tube|1992|0.133879965051415|0.125304947722259|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
