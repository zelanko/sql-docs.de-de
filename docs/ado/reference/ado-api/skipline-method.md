---
description: SkipLine-Methode
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
ms.openlocfilehash: c0897d90ffeccabbce57525f268214577a523d92
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777469"
---
# <a name="skipline-method"></a>SkipLine-Methode
Überspringt beim Lesen eines [Textstreams](./stream-object-ado.md)eine gesamte Zeile.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Alle Zeichen bis einschließlich des Trenn Zeichens für die nächste Zeile werden übersprungen. Standardmäßig ist der [lineseparser](./lineseparator-property-ado.md) **adCRLF**. Wenn Sie versuchen, das Überschreiten von [EOS](./eos-property.md)zu überspringen, bleibt die aktuelle Position bei **EOS**erhalten.  
  
 Die **SkipLine** -Methode wird mit Textstreams verwendet ([Type](./type-property-ado-stream.md) ist **adtypetext**).  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](./stream-object-ado.md)