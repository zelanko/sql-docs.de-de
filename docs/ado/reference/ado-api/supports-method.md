---
description: Supports-Methode
title: Unterstützt die Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 8b0c05118b0f4b8f952b933bc2474bd1f0879865
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441752"
---
# <a name="supports-method"></a>Supports-Methode
Bestimmt, ob ein angegebenes [Recordsetobjekt](../../../ado/reference/ado-api/recordset-object-ado.md) einen bestimmten Funktionstyp unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **booleschen** Wert zurück, der angibt, ob alle durch das *Cursor Options* -Argument identifizierten Features vom Anbieter unterstützt werden.  
  
#### <a name="parameters"></a>Parameter  
 *Cursor Optionen*  
 Ein **Long** -Ausdruck, der aus einem oder mehreren [Cursor optionenum](../../../ado/reference/ado-api/cursoroptionenum.md) -Werten besteht.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **unterstützte** Methode, um zu bestimmen, welche Arten von Funktionen ein **Recordset** -Objekt unterstützt. Wenn das **Recordset** -Objekt die Funktionen unterstützt, deren zugehörige Konstanten in *Cursor Options*enthalten sind, gibt die **unterstützte** Methode **true**zurück. Andernfalls wird **false**zurückgegeben.  
  
> [!NOTE]
>  Obwohl die **unterstützte** Methode möglicherweise für eine bestimmte Funktionalität **true** zurückgibt, gewährleistet Sie nicht, dass der Anbieter die Funktion unter allen Umständen verfügbar machen kann. Die **unterstützte** Methode gibt einfach zurück, ob der Anbieter die angegebene Funktionalität unterstützen kann, vorausgesetzt, dass bestimmte Bedingungen erfüllt sind. Beispielsweise kann die **unterstützte** Methode angeben, dass ein **Recordset** -Objekt Updates unterstützt, obwohl der Cursor auf einem Join mehrerer Tabellen basiert, einige Spalten, von denen Sie nicht aktualisierbar sind.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützt Methoden Beispiel (VB)](../../../ado/reference/ado-api/supports-method-example-vb.md)   
 [Unterstützt Methoden Beispiel (VC + +)](../../../ado/reference/ado-api/supports-method-example-vc.md)   
 [CursorType-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
