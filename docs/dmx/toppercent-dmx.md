---
title: Topprozent (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3f2f97ef9c7a1cdfa2bb1ba1b86dbe4cf60c8404
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669927"
---
# <a name="toppercent-dmx"></a>TopPercent (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die **topprozent** -Funktion gibt die obersten Zeilen einer Tabelle zurück, deren kumulativer Gesamtwert mindestens einem angegebenen Prozentsatz entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
TopPercent(<table expression>, <rank expression>, <percent>)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Ein Ausdruck, der eine Tabelle zurückgibt, wie z. b. ein \< Tabellen Spalten Verweis> oder eine Funktion, die eine Tabelle zurückgibt.  
  
## <a name="return-type"></a>Rückgabetyp  
 \<Tabellen Ausdrucks>  
  
## <a name="remarks"></a>Bemerkungen  
 Die **topprozent** -Funktion gibt die obersten Zeilen in absteigender Rangfolge zurück, basierend auf dem ausgewerteten Wert des \< Rang Ausdrucks> Argument für jede Zeile, sodass die Summe des \< Rang Ausdrucks> Werte mindestens dem angegebenen Prozentsatz entspricht, der durch das \< %>-Argument angegeben wird. **Topprozent** gibt die kleinste mögliche Anzahl von Elementen zurück, während gleichzeitig der angegebene Prozentwert erreicht wird.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Vorhersage Abfrage für das Association-Modell erstellt, das Sie mit dem Lernprogramm zu [Data Mining-Grundlagen](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)erstellen.  
  
 Um die Funktionsweise von topprozent zu verstehen, kann es hilfreich sein, zuerst eine Vorhersage Abfrage auszuführen, die nur die geclusterte Tabelle zurückgibt.  
  
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
  
 Die topprozent-Funktion nimmt die Ergebnisse dieser Abfrage und gibt die Zeilen mit den größten Werten zurück, die sich auf den angegebenen Prozentsatz summieren.  
  
```  
SELECT   
TopPercent  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    50)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Das erste Argument für die topprozent-Funktion ist der Name einer Tabellenspalte. In diesem Beispiel wird die-Tabelle zurückgegeben, indem die Vorhersagefunktion aufgerufen und das INCLUDE_STATISTICS-Argument verwendet wird.  
  
 Das zweite Argument der topprozent-Funktion ist die Spalte in der Tabelle, die Sie verwenden, um die Ergebnisse zu sortieren. In diesem Beispiel gibt die INCLUDE_STATISTICS-Option die Spalten $SUPPORT, $PROBABILTY und $ADJUSTED PROBABILITY zurück. In diesem Beispiel wird $SUPPORT verwendet, da diese Werte keine Bruchteile besitzen und daher leichter zu überprüfen sind.  
  
 Das dritte Argument für die topprozent-Funktion gibt den Prozentsatz als Double-Wert an. Geben Sie 50 ein, um die Zeilen für die obersten Produkte zu erhalten, die 50 Prozent der Gesamtunterstützung ergeben.  
  
 Beispielergebnisse:  
  
|Modell|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,29...|0,25...|  
|Water Bottle|2866|0,19...|0,17...|  
|Patchkit|2113|0,14...|0,13...|  
|Mountain Tire Tube|1992|0,133...|0,12...|  
  
 **Hinweis** Dieses Beispiel wird nur zur Veranschaulichung der Verwendung von topprozent bereitgestellt. Je nach Größe des Datasets kann die Ausführung dieser Abfrage lange dauern.  
  
> [!WARNING]  
>  Die MDX-Funktionen für TOPPERCENT und BOTTOMPERCENT können unerwartete Ergebnisse generieren, wenn die Werte zur Berechnung des Prozentsatzes negative Zahlen enthalten. Dieses Verhalten wirkt sich nicht auf die DMX-Funktionen aus. Weitere Informationen finden Sie unter [bottomprozent &#40;MDX-&#41;](../mdx/bottompercent-mdx.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
