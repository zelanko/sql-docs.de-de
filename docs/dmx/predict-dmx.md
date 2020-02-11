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
ms.openlocfilehash: eb939c45d298117fa81b05d6188aa3a4c5cd7c4b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68008159"
---
# <a name="predict-dmx"></a>Predict (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die **Vorhersage** Funktion gibt einen vorhergesagten Wert oder eine Gruppe von Werten für eine angegebene Spalte zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Predict(<scalar column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
Predict(<table column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Einen Verweis auf eine skalare Spalte oder einen Verweis auf eine Tabellenspalte.  
  
## <a name="return-type"></a>Rückgabetyp  
 \<Verweis> für skalare Spalten  
  
 oder  
  
 \<Tabellen Spalten Verweis>  
  
 Der Rückgabetyp hängt vom Typ der Spalte ab, auf die diese Funktion angewendet wird.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY und INCLUDE_STATISTICS gelten nur für Verweise auf Tabellenspalten, und EXCLUDE_NULL und INCLUDE_NULL gelten nur für Verweise auf skalare Spalten.  
  
## <a name="remarks"></a>Bemerkungen  
 Zu den Optionen gehören EXCLUDE_NULL (Standardwert), INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (Standardwert), INPUT_ONLY und INCLUDE_STATISTICS.  
  
> [!NOTE]  
>  Bei Zeitreihen Modellen unterstützt die Vorhersagefunktion keine INCLUDE_STATISTICS.  
  
 Der INCLUDE_NODE_ID-Parameter gibt die $NODEID-Spalte im Ergebnis zurück. NODE_ID ist der Inhaltsknoten, für den die Vorhersage in einem bestimmten Fall ausgeführt wird. Dieser Parameter ist optional, wenn Vorhersagen für Tabellen Spalten verwendet werden.  
  
 Der *n* -Parameter gilt für Tabellen Spalten. Er legt fest, wie viele Zeilen entsprechend dem Typ der Vorhersage zurückgegeben werden sollen. Wenn die zugrunde liegende Spalte sequence ist, wird die Funktion " **prätsequence** " aufgerufen. Wenn die zugrunde liegende Spalte Zeitreihen ist, wird die Funktion " **prättimeseries** " aufgerufen. Bei assoziativen Typen von Vorhersagen wird die Funktion " **prätassociation** " aufgerufen.  
  
 Die **Vorhersage** Funktion unterstützt Polymorphie.  
  
 Häufig werden die folgenden alternativen Kurzformen verwendet:  
  
-   [Geschlecht] ist eine Alternative zur **Vorhersage**([Geschlecht], EXCLUDE_NULL).  
  
-   [Produkte Käufe] ist eine Alternative für **Vorhersagen**([Produkte Käufe], EXCLUDE_NULL, exklusiv).  
  
    > [!NOTE]  
    >  Der Rückgabetyp dieser Funktion wird als Spaltenverweis angesehen. Dies bedeutet, dass die **Vorhersage** Funktion als Argument in anderen Funktionen verwendet werden kann, die einen Spalten Verweis als Argument annehmen (außer der **Vorhersage** Funktion selbst).  
  
 Wenn Sie INCLUDE_STATISTICS an eine Vorhersage für eine Tabellenwert Spalte übergeben, werden die Spalten **$Probability** und **$Support** der resultierenden Tabelle hinzugefügt. Diese Spalten beschreiben die Wahrscheinlichkeit des Vorhandenseins für den Datensatz der zugeordneten geschachtelten Tabelle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Vorhersagefunktion verwendet, um die vier Produkte in der Adventure Works-Datenbank zurückzugeben, die höchstwahrscheinlich zusammen verkauft werden. Da die Funktion mit einem Mining Modell für Zuordnungs Regeln vorhergesagt wird, wird automatisch die Funktion " **prätassociation** " verwendet, wie zuvor beschrieben.  
  
```  
SELECT  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,4)  
FROM     [Association]  
```  
  
 Beispielergebnisse:  
  
 Diese Abfrage gibt eine einzelne Zeile mit Daten in einer Spalte (`Expression`) zurück, diese Spalte enthält jedoch die folgende geschachtelte Tabelle.  
  
|Modell|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016331743|0.252695851192499|  
|Water Bottle|2866|0.192620471805901|0.175205052318795|  
|Patchkit|2113|0.142012232004839|0.132389356196586|  
|Mountain Tire Tube|1992|0.133879965051415|0.125304947722259|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
