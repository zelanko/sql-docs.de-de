---
title: SkipLine-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8439f7d8fabc5675e43fca5bba006b22574b992
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931044"
---
# <a name="skipline-method"></a>SkipLine-Methode
Überspringt beim Lesen eines [Textstreams](../../../ado/reference/ado-api/stream-object-ado.md)eine gesamte Zeile.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Alle Zeichen bis einschließlich des Trenn Zeichens für die nächste Zeile werden übersprungen. Standardmäßig ist der [lineseparser](../../../ado/reference/ado-api/lineseparator-property-ado.md) **adCRLF**. Wenn Sie versuchen, das Überschreiten von [EOS](../../../ado/reference/ado-api/eos-property.md)zu überspringen, bleibt die aktuelle Position bei **EOS**erhalten.  
  
 Die **SkipLine** -Methode wird mit Textstreams verwendet ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) ist **adtypetext**).  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
