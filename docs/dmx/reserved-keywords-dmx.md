---
title: Reservierte Schlüsselwörter (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fa17a4fb673ad6508fbfc70d5bab39e398d6c3aa
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67928458"
---
# <a name="reserved-keywords-dmx"></a>Reservierte Schlüsselwörter (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)] reserviert bestimmte Schlüsselwörter für ihre ausschließliche Verwendung. Diese Schlüsselwörter dürfen in Anweisungen für Data Mining-Erweiterungen (DMX) nur an den Positionen verwendet werden, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in der Referenz der Sprache DMX definiert. Diese beschränkten DMX-Schlüsselwörter schließen die folgenden Elemente ein:  
  
-   Alle im Thema [DMX-Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)aufgeführten Daten Definitions Anweisungen.  
  
-   Alle Data Mining Abfragefunktionen, die im Thema [DMX-Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)aufgeführt sind.  
  
-   Alle im Thema [DMX-Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)aufgeführten Operatoren.  
  
-   Schlüsselwörter, die in der Abfragesprache "Mehrdimensionale Ausdrücke (MDX)" definiert und als Teil einer DMX-Anweisung enthalten sind.  
  
-   Schlüsselwörter, die in der Spezifikation von OLE DB für Data Mining definiert und als Teil einer DMX-Anweisung enthalten sind.  
  
 Für das Benennen von Objekten in einer Datenbank empfiehlt es sich, dass Sie Benennungskonventionen verwenden, in denen auf reservierte Schlüsselwörter verzichtet wird.  
  
 Wenn eine Datenbank Objekte enthält, deren Namen mit reservierten Schlüsselwörtern übereinstimmen, müssen Sie für Verweise auf diese Objekte Begrenzungsbezeichner verwenden. Weitere Informationen finden Sie unter Bezeichner [&#40;DMX-&#41;](../dmx/identifiers-dmx.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
