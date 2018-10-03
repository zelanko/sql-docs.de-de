---
title: Size-Eigenschaft (ADO Parameter) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Size
helpviewer_keywords:
- Size property [ADO Parameter]
ms.assetid: e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 682a7aa30596af8a3727eec0daaba4e9fd412ac4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601618"
---
# <a name="size-property-ado-parameter"></a>Size-Eigenschaft (ADO-Parameter)
Gibt die maximale Größe in Bytes oder Zeichen, der eine [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** hodnota ukazuje, die maximale Größe in Bytes oder Zeichen eines Werts in einer **Parameter** Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Größe** Eigenschaft zum Ermitteln der maximalen Größe für die geschriebenen Werte oder beim Lesen von der [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft eine **Parameter** Objekt.  
  
 Wenn Sie angeben, dass einen Datentyp mit variabler Länge, die für eine **Parameter** Objekt (z. B. eine **Zeichenfolge** eingeben, z. B. **AdVarChar**), müssen Sie festlegen, des Objekts  **Größe** -Eigenschaft vor dem Anfügen, damit die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung; andernfalls ein Fehler auftritt.  
  
 Wenn Sie bereits angefügt wurden die **Parameter** -Objekt an der **Parameter** Auflistung von eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt und seinen Typ in einen Datentyp mit variabler Länge ändern, müssen Sie Legen Sie die **Parameter** des Objekts **Größe** Eigenschaft vor dem Ausführen der **Befehl** Objekt; andernfalls ein Fehler auftritt.  
  
 Bei Verwendung der [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) Methode zum Abrufen von Informationen zu den Parametern aus dem Anbieter, und es gibt eine oder mehrere Daten variabler Länge-Typ zurück, **Parameter** Objekten, die ADO möglicherweise arbeitsspeicherzuweisung für die Parameter basierend Klicken Sie auf die maximal mögliche Größe, die während der Ausführung einen Fehler verursachen könnte. Sie sollten explizit festlegen, um Fehler zu vermeiden, die **Größe** -Eigenschaft für diese Parameter vor dem Ausführen des Befehls.  
  
 Die **Größe** Eigenschaft schreibgeschützt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Size-Eigenschaft (ADO Stream)](../../../ado/reference/ado-api/size-property-ado-stream.md)
