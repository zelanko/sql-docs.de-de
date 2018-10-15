---
title: Source-Eigenschaft (ADO-Fehler) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63407f75c5bee03d24b5b3f69c2ef94cb38e177e
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49168720"
---
# <a name="source-property-ado-error"></a>Source-Eigenschaft (ADO Error)
Gibt den Namen des Objekts oder der Anwendung, die ursprünglich ein Fehler generiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Zeichenfolge** Wert, der den Namen eines Objekts oder der Anwendung angibt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Quelle** Eigenschaft für eine [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt, das Bestimmen Sie den Namen des Objekts oder der Anwendung, die ursprünglich ein Fehler generiert. Dies könnte Klassennamen oder die ProgID des Objekts sein. Bei Fehlern in ADO, den Wert der Eigenschaft werden **ADODB.** _ObjectName_, wobei *ObjectName* ist der Name des Objekts, das den Fehler ausgelöst hat. ADOX und ADO MD, wird der Wert **ADOX.** _ObjectName_ und **ADOMD.** _ObjectName_bzw.  
  
 Basierend auf der Fehlerdokumentation aus der **Quelle**, [Anzahl](../../../ado/reference/ado-api/number-property-ado.md), und [Beschreibung](../../../ado/reference/ado-api/description-property.md) Eigenschaften **Fehler** Objekte aufweist, können Sie Code schreiben die wird den Fehler zu behandeln.  
  
 Die **Quelle** -Eigenschaft ist nur Lesezugriff für **Fehler** Objekte.  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description-Eigenschaft](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext-und HelpFile-Eigenschaft](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number-Eigenschaft (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source-Eigenschaft (ADO Record)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Source-Eigenschaft (ADO Recordset)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
