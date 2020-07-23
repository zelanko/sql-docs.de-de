---
title: SELECT FROM &lt; Model &gt; (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 43a7157c5ec7889b2f8cb7018423d909f3db3cb7
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970557"
---
# <a name="select-from-ltmodelgt-dmx"></a>Aus &lt; Modell auswählen &gt; (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Führt einen leeren Vorhersagejoin aus und gibt den wahrscheinlichsten Wert oder die wahrscheinlichsten Werte für die angegebenen Spalten zurück. Für das Erstellen der Vorhersage wird ausschließlich der Inhalt aus dem Miningmodell verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT <expression list> [TOP <n>] FROM <model>   
[WHERE <condition list>]   
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *Ausdrucks Liste*  
 Eine durch Trennzeichen getrennte Liste mit Ausdrücken oder mit PREDICT- bzw. PREDICT ONLY-Spalten.  
  
 *n*  
 Dies ist optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Bedingungs Liste*  
 Dies ist optional. Bedingungen, die die Werte einschränken, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Dies ist optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Spalten in der *Ausdrucks Liste* müssen als Vorhersagen oder Vorhersagen definiert oder mit einer vorhersagbaren Spalte verknüpft werden.  
  
## <a name="naive-bayes-example"></a>Beispiel für Naive Bayes-Algorithmus  
 Im folgenden Beispiel wird ein leerer Vorhersagejoin für die Bike Buyer-Spalte ausgeführt und der für das TM Naive Bayes-Miningmodell wahrscheinlichste Status zurückgegeben.  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>Beispiel für den Time Series-Algorithmus  
 Im folgenden Beispiel wird eine Vorhersage für die Amount-Spalte des Forecasting-Modells ausgeführt, und die nächsten vier Schritte werden zurückgegeben. In der Model Region-Spalte sind die Fahrradmodelle und die Regionen zu jeweils einem Bezeichner kombiniert. Die Abfrage verwendet die Funktion " [prättimeseries &#40;DMX&#41;](../dmx/predicttimeseries-dmx.md) ", um die Vorhersage auszuführen.  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wählen Sie &#40;DMX-&#41;](../dmx/select-dmx.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
