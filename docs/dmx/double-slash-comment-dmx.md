---
title: Doppelte Schrägstriche (Kommentar) (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ca3b7040e5d51c324ddd50d489243b0f67f64feb
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841203"
---
# <a name="double-slash-comment-dmx"></a>Schrägstrich / / (Kommentar) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Kennzeichnet eine Textzeichenfolge, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht ausführen soll. Sie können Kommentare in einer DMX-Anweisung (Data Mining-Erweiterungen) schachteln, am Ende einer Codezeile anfügen oder in eine eigene Zeile einfügen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>Parameter  
 *Comment_Text*  
 Die Zeichenfolge, die den Text des Kommentars enthält.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie // nur für einzeilige Kommentare. Kommentare, die mithilfe von // eingefügt werden, werden durch das Neue-Zeile-Zeichen begrenzt.  
  
 Es gibt keine Maximallänge für Kommentare.  
  
 Weitere Informationen zur Verwendung von unterschiedlichen Arten von Kommentaren in DMX finden Sie unter [Kommentare &#40;DMX&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Schrägstrich Stern &#40;Kommentar&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)   
 [-- &#40;Kommentar&#41; &#40;DMX&#41; Zusammenfassung](../dmx/comment-dmx-summary.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
