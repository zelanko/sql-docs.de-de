---
description: BottomCount (DMX)
title: BottomCount (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a2b810d2b268e12c97857475e474d3ed597978ec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431172"
---
# <a name="bottomcount-dmx"></a>BottomCount (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Gibt die angegebene Anzahl von untersten Zeilen in der durch einen Ausdruck angegebenen aufsteigenden Rangreihenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BottomCount(<table expression>, <rank expression>, <count>)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Ein Ausdruck, der eine Tabelle zurückgibt, wie z \<table column reference> . b., oder eine Funktion, die eine Tabelle zurückgibt.  
  
## <a name="return-type"></a>Rückgabetyp  
 \<table expression>  
  
## <a name="remarks"></a>Bemerkungen  
 Der Wert, der vom-Argument bereitgestellt wird \<rank expression> , bestimmt die steigende Rangfolge für die Zeilen, die im- \<table expression> Argument angegeben sind, und die Anzahl der untersten Zeilen, die im-Argument angegeben werden, \<count> wird zurückgegeben.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Vorhersage Abfrage für das Association-Modell erstellt, das Sie mit dem Lernprogramm zu [Data Mining-Grundlagen](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)erstellen.  
  
 Um zu verstehen, wie BottomCount funktioniert, kann es hilfreich sein, zuerst eine Vorhersage Abfrage auszuführen, die nur die in der Tabelle vorgegebene Tabelle zurückgibt.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  In diesem Beispiel enthält der als Eingabe bereitgestellte Wert ein einzelnes Anführungszeichen und muss daher mit Escapezeichen versehen werden, indem ihm ein weiteres einzelnes Anführungszeichen vorangestellt wird. Wenn Sie über die Syntax zum Einfügen von Escapezeichen nicht sicher sind, können Sie den Generator für Vorhersageabfragen verwenden, um die Abfrage zu erstellen. Wenn Sie den Wert aus der Dropdownliste auswählen, wird das erforderliche Escapezeichen automatisch eingefügt. Weitere Informationen finden Sie unter [Erstellen einer SINGLETON-Abfrage im Data Mining-Designer](https://docs.microsoft.com/analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer).  
  
 Beispielergebnisse:  
  
|Modell|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,291283016|0,252695851|  
|Water Bottle|2866|0,192620472|0,175205052|  
|Patchkit|2113|0,142012232|0,132389356|  
|Mountain Tire Tube|1992|0,133879965|0,125304948|  
|Mountain-200|1755|0,117951475|0,111260823|  
|Road Tire Tube|1588|0,106727603|0,101229538|  
|Cycling Cap|1473|0,098998589|0,094256014|  
|Fender Set – Mountain|1415|0,095100477|0,090718432|  
|Mountain Bottle Cage|1367|0,091874454|0,087780332|  
|Road Bottle Cage|1195|0,080314537|0,077173962|  
  
 Die BottomCount-Funktion nimmt die Ergebnisse dieser Abfrage und gibt die Zeilen mit den kleinsten Werten zurück, die den angegebenen Prozentsatz summieren.  
  
```  
SELECT   
BottomCount  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    3)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Das erste Argument der BottomCount-Funktion ist der Name einer Tabellenspalte. In diesem Beispiel wird die-Tabelle zurückgegeben, indem die Vorhersagefunktion aufgerufen und das INCLUDE_STATISTICS-Argument verwendet wird.  
  
 Das zweite Argument der BottomCount-Funktion ist die Spalte in der Tabelle, die Sie zum Sortieren der Ergebnisse verwenden. In diesem Beispiel gibt die INCLUDE_STATISTICS-Option die Spalten $SUPPORT, $PROBABILTY und $ADJUSTED PROBABILITY zurück. In diesem Beispiel wird $SUPPORT verwendet, da diese Werte keine Bruchteile besitzen und daher leichter zu überprüfen sind.  
  
 Das dritte Argument der BottomCount-Funktion gibt die Anzahl der Zeilen an. Um die drei Zeilen mit dem niedrigsten Rangfolgenwert sortiert nach $SUPPORT abzurufen, geben Sie 3 ein.  
  
 Beispielergebnisse:  
  
|Modell|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0,080314537|0,077173962|  
|Mountain Bottle Cage|1367|0,091874454|0,087780332|  
|Fender Set – Mountain|1415|0,095100477|0,090718432|  
  
 **Hinweis** Dieses Beispiel wird nur zur Veranschaulichung der Verwendung von "BottomCount" bereitgestellt. Je nach Größe des Datasets kann die Ausführung dieser Abfrage lange dauern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)   
 [&#40;DMX-&#41;im unteren Prozentsatz ](../dmx/bottompercent-dmx.md)   
 [BottomSum-&#40;DMX-&#41;](../dmx/bottomsum-dmx.md)   
 [TopCount &#40;DMX-&#41;](../dmx/topcount-dmx.md)  
  
  
