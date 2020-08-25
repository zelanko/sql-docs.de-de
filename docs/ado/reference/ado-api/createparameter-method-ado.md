---
description: CreateParameter-Methode (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c3ed02109806232f8301b33e8b0387ea78b6ef4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775609"
---
# <a name="createparameter-method-ado"></a>CreateParameter-Methode (ADO)
Erstellt ein neues [Parameter](./parameter-object.md) Objekt mit den angegebenen Eigenschaften.  
  
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
 Optional. Ein [datatyetenum](./datatypeenum.md) -Wert, der den Datentyp des **Parameter** Objekts angibt.  
  
 *Richtung*  
 Optional. Ein [ParameterDirectionEnum](./parameterdirectionenum.md) -Wert, der den Typ des **Parameter** Objekts angibt.  
  
 *Größe*  
 Optional. Ein **Long** -Wert, der die maximale Länge für den Parameterwert in Zeichen oder Bytes angibt.  
  
 *Wert*  
 Optional. Eine **Variante** , die den Wert für das **Parameter** Objekt angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die Methode " **kreateparameter** ", um ein neues **Parameter** Objekt mit einem angegebenen Namen, Typ, Richtung, Größe und Wert zu erstellen. Alle Werte, die Sie an die Argumente übergeben, werden in die entsprechenden **Parameter** Eigenschaften geschrieben.  
  
 Diese Methode fügt das **Parameter** Objekt nicht automatisch an die **Parameter** Auflistung eines [Befehls](./command-object-ado.md) Objekts an. Auf diese Weise können Sie zusätzliche Eigenschaften festlegen, deren Werte von ADO überprüft werden, wenn Sie das **Parameter** Objekt an die Auflistung anfügen.  
  
 Wenn Sie einen Datentyp variabler Länge im *Typargument* angeben, müssen Sie entweder ein *size* -Argument übergeben oder die [size](./size-property-ado-parameter.md) -Eigenschaft des **Parameter** Objekts festlegen, bevor es an die **Parameter** Auflistung angehängt wird. Andernfalls tritt ein Fehler auf.  
  
 Wenn Sie einen numerischen Datentyp (**adNumeric** oder **addecimal**) im *Typargument* angeben, müssen Sie auch die Eigenschaften " [NumericScale](./numericscale-property-ado.md) " und " [Precision](./precision-property-ado.md) " festlegen.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Append und die Methode "Anfüge Parameter" (VB)](./append-and-createparameter-methods-example-vb.md)   
 [Beispiel für Append und die Methode "append Parameter" (VC + +)](./append-and-createparameter-methods-example-vc.md)   
 [Append-Methode (ADO)](./append-method-ado.md)   
 [Parameter-Objekt](./parameter-object.md)   
 [Parameters-Collection (ADO)](./parameters-collection-ado.md)