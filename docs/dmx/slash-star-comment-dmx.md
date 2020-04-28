---
title: Schrägstrich-Stern (Kommentar) (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5d0b929ba60915f116d9ff6843b4f20b3105a7ae
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67942844"
---
# <a name="slash-star-comment-dmx"></a>Schrägstrich-Stern (Kommentar) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Kennzeichnet eine Textzeichenfolge, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht ausführen soll. Der Text zwischen den Kommentarzeichen/* und \*/wird vom Server nicht ausgewertet. Sie können Kommentare in einer DMX-Anweisung (Data Mining-Erweiterungen) schachteln, am Ende einer Codezeile anfügen oder in eine eigene Zeile einfügen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
/* Comment_Text */  
```  
  
#### <a name="parameters"></a>Parameter  
 *Comment_Text*  
 Die Zeichenfolge, die den Text des Kommentars enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Kommentare, die sich über mehrere Zeilen erstrecken, müssen in /* und \*/ eingeschlossen sein.  
  
 Es gibt keine Maximallänge für Kommentare.  
  
 Weitere Informationen zur Verwendung verschiedener Arten von Kommentaren in DMX finden Sie unter [comments &#40;DMX&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Doppelter Schrägstrich &#40;Kommentar&#41; &#40;DMX-&#41;](../dmx/double-slash-comment-dmx.md)   
 [--&#40;Kommentar&#41; &#40;DMX-&#41; Zusammenfassung](../dmx/comment-dmx-summary.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
