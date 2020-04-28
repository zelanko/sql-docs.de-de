---
title: Bottomprozent (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9d8b1665c6e6978af7dc673f7dd51a363da5c48d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68892871"
---
# <a name="bottompercent-dmx"></a>BottomPercent (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt in aufsteigender Rangreihenfolge die untersten Zeilen einer Tabelle zurück, deren kumulativer Gesamtwert mindestens so groß wie ein angegebener Prozentsatz ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BottomPercent(<table expression>, <rank expression>, <percent>)  
```  
  
## <a name="arguments"></a>Argumente  
 *\<Tabellen Ausdrucks>*  
 Der Name der geschachtelten Tabelle oder des Tabellenwertausdrucks.  
  
 *\<Rang Ausdrucks>*  
 Eine Spalte in der geschachtelten Tabelle oder ein Ausdruck, der eine Spalte auswertet.  
  
 *\<Prozent>*  
 Ein doppelter Wert, der den gesamten Zielprozentsatz angibt.  
  
## <a name="result-type"></a>Ergebnistyp  
 Tabelle  
  
## <a name="remarks"></a>Bemerkungen  
 Die **bottomprozent** -Funktion gibt die untersten Zeilen in steigender Rangfolge zurück. Der Rang basiert auf dem ausgewerteten Wert des \<Rang Ausdrucks> Argument für jede Zeile, sodass die Summe des \<Rang Ausdrucks> Werte mindestens dem angegebenen Prozentsatz entspricht, der durch das \<%>-Argument angegeben wird. **Bottomprozent** gibt die kleinste mögliche Anzahl von Elementen zurück, während gleichzeitig der angegebene Prozentwert erreicht wird.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Vorhersage Abfrage für das Association-Modell erstellt, das Sie im Lernprogramm zu [Data Mining-Grundlagen](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)erstellt haben.  
  
 Um zu verstehen, wie bottomprozent funktioniert, kann es hilfreich sein, zuerst eine Vorhersage Abfrage auszuführen, die nur die Tabelle mit den Tabellen zurückgibt.  
  
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
  
 Die Funktion bottomprozent nimmt die Ergebnisse dieser Abfrage und gibt die Zeilen mit den kleinsten Werten zurück, die den angegebenen Prozentsatz summieren.  
  
```  
SELECT   
BottomPercent  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    50)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Das erste Argument der bottomprozent-Funktion ist der Name einer Tabellenspalte. In diesem Beispiel wird die-Tabelle zurückgegeben, indem die Vorhersagefunktion aufgerufen und das INCLUDE_STATISTICS-Argument verwendet wird.  
  
 Das zweite Argument der bottomprozent-Funktion ist die Spalte in der Tabelle, die Sie zum Sortieren der Ergebnisse verwenden. In diesem Beispiel gibt die INCLUDE_STATISTICS-Option die Spalten $SUPPORT, $PROBABILTY und $ADJUSTED PROBABILITY zurück. In diesem Beispiel wird $SUPPORT verwendet, da diese Werte keine Bruchteile besitzen und daher leichter zu überprüfen sind.  
  
 Das dritte Argument der bottomprozent-Funktion gibt den Prozentsatz als Double-Wert an. Geben Sie 50 ein, um die Zeilen zu erhalten, die die unteren 50 Prozent der Unterstützungswerte darstellen.  
  
 Beispielergebnisse:  
  
|Modell|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0,080314537|0,077173962|  
|Mountain Bottle Cage|1367|0,091874454|0,087780332|  
|Fender Set – Mountain|1415|0,095100477|0,090718432|  
|Cycling Cap|1473|0,098998589|0,094256014|  
|Road Tire Tube|1588|0,106727603|0,101229538|  
|Mountain-200|1755|0,117951475|0,111260823|  
|Mountain Tire Tube|1992|0,133879965|0,125304948|  
  
 **Hinweis** Dieses Beispiel wird nur zur Veranschaulichung der Verwendung von "bottomprozent" bereitgestellt. Je nach Größe des Datasets kann die Ausführung dieser Abfrage lange dauern.  
  
> [!WARNING]  
>  Die MDX-Funktionen für TOPPERCENT und BOTTOMPERCENT können unerwartete Ergebnisse generieren, wenn die Werte zur Berechnung des Prozentsatzes negative Zahlen enthalten. Dieses Verhalten wirkt sich nicht auf die DMX-Funktionen aus. Weitere Informationen finden Sie unter [bottomprozent &#40;MDX-&#41;](../mdx/bottompercent-mdx.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)  
  
  
