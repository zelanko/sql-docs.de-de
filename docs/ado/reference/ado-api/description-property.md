---
title: Description-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Description
- Error::GetDescription
- Error::get_Description
helpviewer_keywords:
- Description property
ms.assetid: 4b5d6790-6c29-42aa-bf78-d9cfb8ad7965
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b9a97e1e63e3896cd451c68d6198baa991945e7a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704521"
---
# <a name="description-property"></a>Description-Eigenschaft
Beschreibt eine [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Zeichenfolge** -Wert, der eine Beschreibung des Fehlers enthält.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Beschreibung** Eigenschaft, um eine kurze Beschreibung des Fehlers zu erhalten. Zeigen Sie diese Eigenschaft an, dass den Benutzer zu einem Fehler eine Warnung, die Sie nicht oder nicht verarbeiten möchten. Die Zeichenfolge wird von der ADO oder ein Anbieter stammen.  
  
 Anbieter sind verantwortlich für die betreffenden Fehlertext an ADO übergeben. ADO fügt eine [Fehler](../../../ado/reference/ado-api/error-object.md) -Objekt an die **Fehler** Auflistung für jeden Anbieter, Fehler oder Warnung es empfängt. Auflisten der **Fehler** -Auflistung, um die Fehler zu verfolgen, die der Anbieter übergibt.  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [HelpContext-und HelpFile-Eigenschaft](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number-Eigenschaft (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source-Eigenschaft (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
