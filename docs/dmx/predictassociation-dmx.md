---
title: PredictAssociation (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7a23407b546bcde2dd1fde81654da4fe861e0719
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37989542"
---
# <a name="predictassociation-dmx"></a>PredictAssociation (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sagt eine assoziative Mitgliedschaft voraus.  
  
Beispielsweise können Sie die PredictAssociation-Funktion, um die Empfehlungen den aktuellen Status der Einkaufswagen eines Kunden abzurufen. 
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictAssociation(<table column reference>, option1, option2, n ...)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Algorithmen, die vorhersagbare geschachtelte Tabellen, einschließlich von Zuordnungs- und einige Klassifizierungsalgorithmen enthalten. Klassifikationsalgorithmen, die Unterstützung für geschachtelte Tabellen enthalten die [!INCLUDE[msCoName](../includes/msconame-md.md)] Entscheidungsstrukturen [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes und [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network-Algorithmen.  
  
## <a name="return-type"></a>Rückgabetyp  
 \<Tabellenausdruck >  
  
## <a name="remarks"></a>Hinweise  
 Die Optionen für die **PredictAssociation** -Funktion enthalten, EXCLUDE_NULL, INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (Standardwert), INPUT_ONLY, INCLUDE_STATISTICS und INCLUDE_NODE_ID.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY und INCLUDE_STATISTICS gelten nur für Verweise auf Tabellenspalten, und EXCLUDE_NULL und INCLUDE_NULL gelten nur für Verweise auf skalare Spalten.  
  
 INCLUDE_STATISTICS gibt nur zurück, **$Probability** und **$AdjustedProbability**.  
  
 Wenn der numerische Parameter *n* angegeben wird, die **PredictAssociation** Funktion gibt die obersten n am wahrscheinlichsten Werte, die basierend auf der Wahrscheinlichkeit zurück:  
  
```  
PredictAssociation(colref, [$AdjustedProbability], n)  
```  
  
 Wenn Sie einschließen **$AdjustedProbability**, die Anweisung gibt *n* Werte auf Grundlage der **$AdjustedProbability**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die **PredictAssociation** Funktion zurück, die vier Produkte in der Adventure Works-Datenbank, die am wahrscheinlichsten zusammen verkauft werden werden.  
  
```  
SELECT  
  PredictAssociation([Association].[v Assoc Seq Line Items],4)  
From  
  [Association]  
```  
Das folgende Beispiel veranschaulicht die Verwendung eine geschachtelte Tabelle als Eingabe für die Vorhersagefunktion kann mithilfe der SHAPE-Klausel. SHAPE-Abfrage erstellt ein Rowset mit "CustomerID" als eine Spalte und eine geschachtelte Tabelle als eine zweite Spalte, die die Liste der Produkte enthält, die ein Kunde bereits geladen wurde. 

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

  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
