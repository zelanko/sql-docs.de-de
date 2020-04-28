---
title: Prätassociation (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea0a9915e062d7b6f15b63e18976e88cc339202d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "76939497"
---
# <a name="predictassociation-dmx"></a>PredictAssociation (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sagt eine assoziative Mitgliedschaft voraus.  
  
Beispielsweise können Sie die Funktion "prätassociation" verwenden, um den Satz der Empfehlungen zu erhalten, wenn der aktuelle Zustand des Warenkorbs für einen Kunden angezeigt wird. 
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictAssociation(<table column reference>, option1, option2, n ...)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Algorithmen, die vorhersagbare Tabellen enthalten, einschließlich der Zuordnung und einiger Klassifizierungs Algorithmen. Zu den Klassifizierungs Algorithmen, die die Unterstützung [!INCLUDE[msCoName](../includes/msconame-md.md)] von Netzwerk Tabellen [!INCLUDE[msCoName](../includes/msconame-md.md)] unterstützen, gehören die [!INCLUDE[msCoName](../includes/msconame-md.md)] Algorithmen Decision Trees, Naive Bayes und Neural Network.  
  
## <a name="return-type"></a>Rückgabetyp  
 \<Tabellen Ausdrucks>  
  
## <a name="remarks"></a>Bemerkungen  
 Zu den Optionen für die **prätassociation** -Funktion zählen EXCLUDE_NULL, INCLUDE_NULL, inklusiv, exklusiv (Standard), INPUT_ONLY, INCLUDE_STATISTICS und INCLUDE_NODE_ID.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY und INCLUDE_STATISTICS gelten nur für Verweise auf Tabellenspalten, und EXCLUDE_NULL und INCLUDE_NULL gelten nur für Verweise auf skalare Spalten.  
  
 INCLUDE_STATISTICS gibt nur **$Probability** und **$AdjustedProbability**zurück.  
  
 Wenn der numerische Parameter *n* angegeben ist, gibt die **prätassociation** -Funktion die obersten n wahrscheinlichsten Werte basierend auf der Wahrscheinlichkeit zurück:  
  
```  
PredictAssociation(colref, [$AdjustedProbability], n)  
```  
  
 Wenn Sie **$AdjustedProbability**einschließen, gibt die-Anweisung die obersten *n* -Werte basierend auf der **$AdjustedProbability**zurück.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die vier Produkte in der Adventure Works-Datenbank, die höchstwahrscheinlich zusammen verkauft werden, mithilfe der Funktion " **prätassociation** " zurückgegeben.  
  
```  
SELECT  
  PredictAssociation([Association].[v Assoc Seq Line Items],4)  
From  
  [Association]  
```  
Im folgenden Beispiel wird veranschaulicht, wie Sie eine Tabellen Tabelle mithilfe der Shape-Klausel als Eingabe für die Vorhersagefunktion verwenden können. Die Shape-Abfrage erstellt ein Rowset mit CustomerID als eine Spalte und eine in einer Tabelle gespeicherte Tabelle als zweite Spalte, die die Liste der Produkte enthält, die ein Kunde bereits eingegeben hat. 

~~~~
SELECT T.[CustomerId], PredictAssociation(MyNestedTable, 5) // returns top 5 associated items
FROM My Model
PREDICTION JOIN
SHAPE {
    OPENQUERY([Adventure Works DW],'SELECT CustomerID, OrderNumber
    FROM vAssocSeqOrders ORDER BY OrderNumber')
} APPEND (
    {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, model FROM 
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}
  RELATE OrderNumber to OrderNumber) AS T
~~~~  

  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
