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
manager: kfile
ms.openlocfilehash: 813641b7fa72405a0ba5a026e255f03feb94bd05
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992472"
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
  
-   Wenn beide *für die ersten n* und *n-Ende-* angegeben sind, die Sequenzwerte von *für die ersten n* zu *n-Ende-*.  
  
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
  
  
