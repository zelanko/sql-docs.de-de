---
title: Size-Eigenschaft (ADO-Parameter) | Microsoft-Dokumentation
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
ms.openlocfilehash: 3796f772dedb961ec34eb0639034350989f99142
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931052"
---
# <a name="size-property-ado-parameter"></a>Size-Eigenschaft (ADO-Parameter)
Gibt die maximale Größe eines [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekts in Bytes oder Zeichen an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der die maximale Größe in Bytes oder Zeichen eines Werts in einem **Parameter** Objekt angibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **size** -Eigenschaft, um die maximale Größe für Werte zu ermitteln, die in die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft eines **Parameter** Objekts geschrieben oder daraus gelesen werden.  
  
 Wenn Sie einen Datentyp variabler Länge für ein **Parameter** Objekt angeben (z. b. einen beliebigen **Zeichen** Folgentyp wie **adVarChar**), müssen Sie die **size** -Eigenschaft des Objekts festlegen, bevor es an die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung angehängt wird. Andernfalls tritt ein Fehler auf.  
  
 Wenn Sie das **Parameter** Objekt bereits an die **Parameter** Auflistung eines [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekts angefügt haben und den Typ in einen Datentyp mit variabler Länge ändern, müssen Sie die **size** -Eigenschaft des **Parameter** Objekts festlegen, bevor Sie das **Befehls** Objekt ausführen. Andernfalls tritt ein Fehler auf.  
  
 Wenn Sie die [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode verwenden, um Parameterinformationen vom Anbieter abzurufen, und ein oder mehrere Datentyp **Parameter** Objekte variabler Länge zurückgibt, kann ADO Arbeitsspeicher für die Parameter zuweisen, basierend auf Ihrer maximalen potenziellen Größe, die während der Ausführung einen Fehler verursachen könnte. Um einen Fehler zu vermeiden, sollten Sie die **size** -Eigenschaft für diese Parameter explizit festlegen, bevor Sie den Befehl ausführen.  
  
 Die **size** -Eigenschaft ist Lese-/Schreibzugriff.  
  
## <a name="applies-to"></a>Gilt für  
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Size-Eigenschaft (ADO-Stream)](../../../ado/reference/ado-api/size-property-ado-stream.md)
