---
title: HelpContext- und HelpFile-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetHelpContext
- Error::GetHelpFile
- Error::get_HelpFile
- Error::get_HelpContext
- Error::HelpContext
- Error::HelpFile
helpviewer_keywords:
- HelpContext property [ADO]
- HelpFile property [ADO]
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ba441a52958e423308e648f15dd36e14d6d1d895
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918480"
---
# <a name="helpcontext-helpfile-properties"></a>HelpContext- und HelpFile-Eigenschaft
Gibt an, die Hilfedatei und das zugeordnete Thema ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt.  
  
## <a name="return-values"></a>Rückgabewerte  
  
-   **Hilfekontext-ID** gibt eine Kontext-ID als ein **lange** Wert für ein Thema in einer Hilfedatei.  
  
-   **HelpFile** gibt eine **Zeichenfolge** Wert, der eine vollständig aufgelösten Pfad zu einer Hilfedatei ergibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn in eine Hilfedatei angegeben ist die **HelpFile** -Eigenschaft, die **HelpContext** Eigenschaft wird verwendet, um das Hilfethema zeigt automatisch identifiziert. Wenn keine entsprechenden Hilfethema verfügbar, die **HelpContext** Eigenschaft gibt NULL zurück und die **HelpFile** Eigenschaft gibt eine Zeichenfolge der Länge 0 (null) zurück ("").  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description-Eigenschaft](../../../ado/reference/ado-api/description-property.md)   
 [Number-Eigenschaft (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source-Eigenschaft (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
