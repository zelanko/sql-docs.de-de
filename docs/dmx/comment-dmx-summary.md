---
title: --(Kommentar) (DMX)-Zusammenfassung | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4f0f01b0dc3550c6b09e6c2342232e6b7c7fac8f
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969911"
---
# <a name="---comment-dmx-summary"></a>--(Kommentar) (DMX)-Zusammenfassung
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Kennzeichnet eine Textzeichenfolge, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht ausführen soll. Sie können Kommentare in einer DMX-Anweisung (Data Mining-Erweiterungen) schachteln, am Ende einer Codezeile anfügen oder in eine eigene Zeile einfügen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Parameter  
 *Comment_Text*  
 Die Zeichenfolge, die den Text des Kommentars enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie diesen Operator für einzeilige oder geschachtelte Kommentare. Kommentare, die mithilfe von -- eingefügt werden, werden durch das Neue-Zeile-Zeichen begrenzt.  
  
 Es gibt keine Maximallänge für Kommentare.  
  
 Weitere Informationen zur Verwendung verschiedener Arten von Kommentaren in DMX finden Sie unter [comments &#40;DMX&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schrägstrich-Stern &#40;Kommentar&#41; &#40;DMX-&#41;](../dmx/slash-star-comment-dmx.md)   
 [Doppelter Schrägstrich &#40;Kommentar&#41; &#40;DMX-&#41;](../dmx/double-slash-comment-dmx.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
