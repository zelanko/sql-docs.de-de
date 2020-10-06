---
description: BottomSum (DMX)
title: BottomSum (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 551fde90989093ab601cfa6100b6c6e208fac9e6
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727745"
---
# <a name="bottomsum-dmx"></a>BottomSum (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Gibt in aufsteigender Rangreihenfolge die untersten Zeilen einer Tabelle zurück, deren kumulativer Gesamtwert mindestens so groß wie ein angegebener Wert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BottomSum(<table expression>, <rank expression>, <sum>)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Ein Ausdruck, der eine Tabelle zurückgibt, wie z \<table column reference> . b., oder eine Funktion, die eine Tabelle zurückgibt.  
  
## <a name="return-type"></a>Rückgabetyp  
 \<table expression>  
  
## <a name="remarks"></a>Bemerkungen  
 Die **BottomSum** -Funktion gibt die untersten Zeilen in steigender Rangfolge zurück. Der Rang basiert auf dem ausgewerteten Wert des- \<rank expression> Arguments für jede Zeile, sodass die Summe der \<rank expression> Werte mindestens dem angegebenen Gesamtwert entspricht, der durch das-Argument angegeben wird \<sum> . **BottomSum** gibt die kleinste mögliche Anzahl von Elementen zurück, während gleichzeitig der angegebene Summenwert erreicht wird.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Vorhersage Abfrage für das Association-Modell erstellt, das Sie mit dem Lernprogramm zu [Data Mining-Grundlagen](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130))erstellen.  
  
 Um zu verstehen, wie BottomSum funktioniert, kann es hilfreich sein, zuerst eine Vorhersage Abfrage auszuführen, die nur die in der Tabelle abgesterte Tabelle zurückgibt.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  In diesem Beispiel enthält der als Eingabe bereitgestellte Wert ein einzelnes Anführungszeichen und muss daher mit Escapezeichen versehen werden, indem ihm ein weiteres einzelnes Anführungszeichen vorangestellt wird. Wenn Sie über die Syntax zum Einfügen von Escapezeichen nicht sicher sind, können Sie den Generator für Vorhersageabfragen verwenden, um die Abfrage zu erstellen. Wenn Sie den Wert aus der Dropdownliste auswählen, wird das erforderliche Escapezeichen automatisch eingefügt. Weitere Informationen finden Sie unter [Erstellen einer SINGLETON-Abfrage im Data Mining-Designer](/analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer).  
  
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
  
 Die BottomSum-Funktion nimmt die Ergebnisse dieser Abfrage und gibt die Zeilen mit den niedrigsten Werten zurück, die die angegebene Anzahl summieren.  
  
```  
SELECT   
BottomSum  
    (  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $PROBABILITY,  
    .1)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Das erste Argument der BottomSum-Funktion ist der Name einer Tabellenspalte. In diesem Beispiel wird die-Tabelle zurückgegeben, indem die Vorhersagefunktion aufgerufen und das INCLUDE_STATISTICS-Argument verwendet wird.  
  
 Das zweite Argument der BottomSum-Funktion ist die Spalte in der Tabelle, die Sie zum Sortieren der Ergebnisse verwenden. In diesem Beispiel gibt die INCLUDE_STATISTICS-Option die Spalten $SUPPORT, $PROBABILTY und $ADJUSTED PROBABILITY zurück. In diesem Beispiel wird $PROBABILITY zum Zurückgeben von Zeilen verwendet, die mindestens eine Wahrscheinlichkeit von 50 % ergeben.  
  
 Das dritte Argument der BottomSum-Funktion gibt die Ziel Summe als Double-Wert an. Geben Sie .1 ein, um die Zeilen für die Produkte mit der niedrigsten Anzahl zu erhalten, die 10 Prozent Wahrscheinlichkeit ergeben.  
  
 Beispielergebnisse:  
  
|Modell|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0,08...|0,07...|  
|Mountain Bottle Cage|1367|0,09...|0,08...|  
  
 **Hinweis** Dieses Beispiel wird nur zur Veranschaulichung der Verwendung von "BottomSum" bereitgestellt. Je nach Größe des Datasets kann die Ausführung dieser Abfrage lange dauern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)   
 [&#40;DMX-&#41;im unteren Prozentsatz ](../dmx/bottompercent-dmx.md)  
  
