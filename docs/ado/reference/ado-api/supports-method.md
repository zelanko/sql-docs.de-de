---
description: Supports-Methode
title: Unterstützt die Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Supports
- Recordset15::Supports
helpviewer_keywords:
- Supports method [ADO]
ms.assetid: 298fc41c-0b55-42fc-b373-c5133b4da6a5
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a91268668dae9ba430ba696ffb0186749047af9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988321"
---
# <a name="supports-method"></a>Supports-Methode
Bestimmt, ob ein angegebenes [Recordsetobjekt](./recordset-object-ado.md) einen bestimmten Funktionstyp unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **booleschen** Wert zurück, der angibt, ob alle durch das *Cursor Options* -Argument identifizierten Features vom Anbieter unterstützt werden.  
  
#### <a name="parameters"></a>Parameter  
 *Cursor Optionen*  
 Ein **Long** -Ausdruck, der aus einem oder mehreren [Cursor optionenum](./cursoroptionenum.md) -Werten besteht.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **unterstützte** Methode, um zu bestimmen, welche Arten von Funktionen ein **Recordset** -Objekt unterstützt. Wenn das **Recordset** -Objekt die Funktionen unterstützt, deren zugehörige Konstanten in *Cursor Options*enthalten sind, gibt die **unterstützte** Methode **true**zurück. Andernfalls wird **false**zurückgegeben.  
  
> [!NOTE]
>  Obwohl die **unterstützte** Methode möglicherweise für eine bestimmte Funktionalität **true** zurückgibt, gewährleistet Sie nicht, dass der Anbieter die Funktion unter allen Umständen verfügbar machen kann. Die **unterstützte** Methode gibt einfach zurück, ob der Anbieter die angegebene Funktionalität unterstützen kann, vorausgesetzt, dass bestimmte Bedingungen erfüllt sind. Beispielsweise kann die **unterstützte** Methode angeben, dass ein **Recordset** -Objekt Updates unterstützt, obwohl der Cursor auf einem Join mehrerer Tabellen basiert, einige Spalten, von denen Sie nicht aktualisierbar sind.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützt Methoden Beispiel (VB)](./supports-method-example-vb.md)   
 [Unterstützt Methoden Beispiel (VC + +)](./supports-method-example-vc.md)   
 [CursorType-Eigenschaft (ADO)](./cursortype-property-ado.md)