---
title: PredictSequence (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c6828b77af36b5dbbc50fbca0210961a7f2ed20c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041919"
---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sagt zukünftige Sequenzwerte für eine angegebene Gruppe von Sequenzdaten voraus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein \<Tabellenausdruck >.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die *n* -Parameter angegeben wird, gibt die folgenden Werte:  
  
-   Wenn *n* ist größer als 0 (null), die am wahrscheinlichsten Sequence-Werte in den nächsten *n* Schritte.  
  
-   Wenn beide *für die ersten n* und *n-Ende-* angegeben sind, die Sequenzwerte von *für die ersten n* zu *n-Ende-* .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird basierend auf dem Sequence Clustering-Miningmodell eine Sequenz der fünf Produkte in der [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]-Datenbank zurückgegeben, bei denen die Wahrscheinlichkeit am größten ist, dass sie von einem Kunden gekauft werden.  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
