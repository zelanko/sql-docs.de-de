---
title: LineSeparator-Eigenschaft (ADO) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0343954f549f2cba4b535b8ab4ebafec5a842015
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918285"
---
# <a name="lineseparator-property-ado"></a>LineSeparator-Eigenschaft (ADO)
Gibt das binäre Zeichen als das Zeilentrennzeichen in Text zu verwendende [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekte.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) hodnota ukazuje, das Zeilentrennzeichen in verwendet die **Stream**. Der Standardwert ist **AdCRLF**.  
  
## <a name="remarks"></a>Hinweise  
 **LineSeparator** wird verwendet, um Zeilen zu interpretieren, wenn Sie den Inhalt einer Textdatei lesen **Stream**. Zeilen übersprungen werden können, mit der [SkipLine](../../../ado/reference/ado-api/skipline-method.md) Methode.  
  
 **LineSeparator** wird verwendet, nur mit Text **Stream** Objekte ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) ist **AdTypeText**). Diese Eigenschaft wird ignoriert, wenn **Typ** ist **AdTypeBinary**.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
