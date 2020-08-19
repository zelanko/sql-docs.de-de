---
description: LineSeparator-Eigenschaft (ADO)
title: Lineseparser-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
author: rothja
ms.author: jroth
ms.openlocfilehash: e3571f6a01fc60377380c0dcc40c870dfc71276a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443372"
---
# <a name="lineseparator-property-ado"></a>LineSeparator-Eigenschaft (ADO)
Gibt das binäre Zeichen an, das als Zeilen Trennzeichen in [textstreamobjekten](../../../ado/reference/ado-api/stream-object-ado.md) verwendet werden soll.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [lineseparameatorsenum](../../../ado/reference/ado-api/lineseparatorsenum.md) -Wert fest, der das im **Stream**verwendete Zeilen Trennzeichen angibt, oder gibt diesen zurück. Der Standardwert ist **adCRLF**.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit **lineseparser** werden Zeilen beim Lesen des Inhalts eines **Textstreams**interpretiert. Zeilen können mit der [SkipLine](../../../ado/reference/ado-api/skipline-method.md) -Methode übersprungen werden.  
  
 **Lineseparser** wird nur mit **textstreamobjekten** ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) : **adtypetext**) verwendet. Diese Eigenschaft wird ignoriert, wenn der **Typ** **adTypeBinary**ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
