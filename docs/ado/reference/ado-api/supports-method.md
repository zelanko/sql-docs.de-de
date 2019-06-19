---
title: Supports-Methode | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1d1df1d780cf9e1e631f6b146e45cc0a34da9438
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710689"
---
# <a name="supports-method"></a>Supports-Methode
Bestimmt, ob ein angegebener [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt unterstützt, eine bestimmte Art von Funktionalität.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **booleschen** Wert, der angibt, ob alle Funktionen von identifiziert die *CursorOptions* Argument vom Anbieter unterstützt werden.  
  
#### <a name="parameters"></a>Parameter  
 *CursorOptions*  
 Ein **lange** Ausdruck, der eine oder mehrere besteht [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) Werte.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **unterstützt** Methode, um zu bestimmen, welche Funktionalität einer **Recordset** -Objekt unterstützt. Wenn die **Recordset** Objekt unterstützt die Funktionen, deren entsprechenden Konstanten in sind *CursorOptions*, **unterstützt** Methodenrückgabe **"true"** . Andernfalls wird **"false"** .  
  
> [!NOTE]
>  Obwohl die **unterstützt** Methodenrückgabewert möglicherweise **"true"** für eine bestimmte Funktionalität, dies garantiert nicht, dass der Anbieter das Feature unter allen Umständen zur Verfügung stellen kann. Die **unterstützt** -Methode einfach zurückgegeben, ob der Anbieter unterstützt den angegebenen Funktionen können unter bestimmten Bedingungen erfüllt sind. Z. B. die **unterstützt** Methode hinweisen, die eine **Recordset** Objekt Updates unterstützt, auch wenn der Cursor auf einen Join mit mehreren Tabellen basiert einige Spalten der sind nicht aktualisierbar.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Supports – Methodenbeispiel (VB)](../../../ado/reference/ado-api/supports-method-example-vb.md)   
 [Supports – Methodenbeispiel (VC++)](../../../ado/reference/ado-api/supports-method-example-vc.md)   
 [CursorType-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
