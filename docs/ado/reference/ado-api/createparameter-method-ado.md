---
title: Kreateparameter-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: af796c36bd2960730536ec07ac49614876311e84
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933297"
---
# <a name="createparameter-method-ado"></a>CreateParameter-Methode (ADO)
Erstellt ein neues [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt mit den angegebenen Eigenschaften.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein **Parameter** Objekt zurück.  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Optional. Ein **Zeichen** folgen Wert, der den Namen des **Parameter** Objekts enthält.  
  
 *Typ*  
 Optional. Ein [datatyetenum](../../../ado/reference/ado-api/datatypeenum.md) -Wert, der den Datentyp des **Parameter** Objekts angibt.  
  
 *Orientierung*  
 Optional. Ein [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) -Wert, der den Typ des **Parameter** Objekts angibt.  
  
 *Größe*  
 Optional. Ein **Long** -Wert, der die maximale Länge für den Parameterwert in Zeichen oder Bytes angibt.  
  
 *Wert*  
 Optional. Eine **Variante** , die den Wert für das **Parameter** Objekt angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die Methode " **kreateparameter** ", um ein neues **Parameter** Objekt mit einem angegebenen Namen, Typ, Richtung, Größe und Wert zu erstellen. Alle Werte, die Sie an die Argumente übergeben, werden in die entsprechenden **Parameter** Eigenschaften geschrieben.  
  
 Diese Methode fügt das **Parameter** Objekt nicht automatisch an die **Parameter** Auflistung eines [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekts an. Auf diese Weise können Sie zusätzliche Eigenschaften festlegen, deren Werte von ADO überprüft werden, wenn Sie das **Parameter** Objekt an die Auflistung anfügen.  
  
 Wenn Sie einen Datentyp variabler Länge im *Typargument* angeben, müssen Sie entweder ein *size* -Argument übergeben oder die [size](../../../ado/reference/ado-api/size-property-ado-parameter.md) -Eigenschaft des **Parameter** Objekts festlegen, bevor es an die **Parameter** Auflistung angehängt wird. Andernfalls tritt ein Fehler auf.  
  
 Wenn Sie einen numerischen Datentyp (**adNumeric** oder **addecimal**) im *Typargument* angeben, müssen Sie auch die Eigenschaften " [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) " und " [Precision](../../../ado/reference/ado-api/precision-property-ado.md) " festlegen.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Append und die Methode "Anfüge Parameter" (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Beispiel für Append und die Methode "append Parameter" (VC + +)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Append-Methode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)   
 [Parameters-Collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
