---
title: SELECT FROM &lt;Modell&gt; (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5611ce3da4f12bca5cb271cabe8af3e149dcbf35
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928324"
---
# <a name="select-from-ltmodelgt-dmx"></a>SELECT FROM &lt;Modell&gt; (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Führt einen leeren Vorhersagejoin aus und gibt den wahrscheinlichsten Wert oder die wahrscheinlichsten Werte für die angegebenen Spalten zurück. Für das Erstellen der Vorhersage wird ausschließlich der Inhalt aus dem Miningmodell verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT <expression list> [TOP <n>] FROM <model>   
[WHERE <condition list>]   
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *Liste mit Ausdrücken*  
 Eine durch Trennzeichen getrennte Liste mit Ausdrücken oder mit PREDICT- bzw. PREDICT ONLY-Spalten.  
  
 *n*  
 Optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Liste der Bedingungen*  
 Optional. Bedingungen, die die Werte einschränken, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die Spalten in der *Ausdrucksliste* müssen als predict oder only Predict definiert oder im Zusammenhang mit einer vorhersagbaren Spalte.  
  
## <a name="naive-bayes-example"></a>Beispiel für Naive Bayes-Algorithmus  
 Im folgenden Beispiel wird ein leerer Vorhersagejoin für die Bike Buyer-Spalte ausgeführt und der für das TM Naive Bayes-Miningmodell wahrscheinlichste Status zurückgegeben.  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>Beispiel für den Time Series-Algorithmus  
 Im folgenden Beispiel wird eine Vorhersage für die Amount-Spalte des Forecasting-Modells ausgeführt, und die nächsten vier Schritte werden zurückgegeben. In der Model Region-Spalte sind die Fahrradmodelle und die Regionen zu jeweils einem Bezeichner kombiniert. Die Abfrage verwendet die [PredictTimeSeries &#40;DMX&#41; ](../dmx/predicttimeseries-dmx.md) Funktion, um die Vorhersage auszuführen.  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT &#40;DMX&#41;](../dmx/select-dmx.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
