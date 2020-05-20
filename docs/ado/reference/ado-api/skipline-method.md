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
author: rothja
ms.author: jroth
ms.openlocfilehash: f983646fd87be27fe9861f3a37b0e852a05ba06b
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759876"
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
