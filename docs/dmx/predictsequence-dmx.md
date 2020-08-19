---
description: PredictSequence (DMX)
title: Prätsequence (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 31f99205f3e23db23c5c2a38750f75212763e8de
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426102"
---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Sagt zukünftige Sequenzwerte für eine angegebene Gruppe von Sequenzdaten voraus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein \<table expression>.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der *n* -Parameter angegeben wird, werden die folgenden Werte zurückgegeben:  
  
-   Wenn *n* größer als 0 (null) ist, handelt es sich um die wahrscheinlichsten Sequenzwerte in den nächsten *n* Schritten.  
  
-   Wenn sowohl *n-Start* als auch *n-End* angegeben sind, werden die Sequenzwerte von *n-Start* zu *n-End*angegeben.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird basierend auf dem Sequence Clustering-Miningmodell eine Sequenz der fünf Produkte in der [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]-Datenbank zurückgegeben, bei denen die Wahrscheinlichkeit am größten ist, dass sie von einem Kunden gekauft werden.  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
