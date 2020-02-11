---
title: Number-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce027747c843e02998f4845db7075e70cf8733b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917994"
---
# <a name="number-property-ado"></a>Number-Eigenschaft (ADO)
Gibt die Zahl an, durch die ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt eindeutig identifiziert wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Long** -Wert zurück, der einer der [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) -Konstanten entsprechen kann.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die Eigenschaft **Number** , um zu bestimmen, welcher Fehler aufgetreten ist. Der Wert der-Eigenschaft ist eine eindeutige Zahl, die der Fehlerbedingung entspricht.  
  
 Die [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) -Auflistung gibt ein HRESULT im Hexadezimal Format (z. b. 0x80004005) oder Long Value (z. b. 2147467259) zurück. Diese HRESULTs können von zugrunde liegenden Komponenten, z. b. OLE DB oder sogar von OLE selbst, ausgelöst werden. Weitere Informationen zu diesen Zahlen finden Sie unter [Errors (OLE DB)](https://msdn.microsoft.com/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) in der [OLE DB Programmer es Reference](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)*.*  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties Example (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description-Eigenschaft](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext, HelpFile-Eigenschaften](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Source-Eigenschaft (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
