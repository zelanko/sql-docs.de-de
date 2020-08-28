---
description: Size-Eigenschaft (ADO-Parameter)
title: Size-Eigenschaft (ADO-Parameter) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 914f751c4bfd48755470ce3da9e994dae4a33477
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989121"
---
# <a name="size-property-ado-parameter"></a>Size-Eigenschaft (ADO-Parameter)
Gibt die maximale Größe eines [Parameter](./parameter-object.md) Objekts in Bytes oder Zeichen an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der die maximale Größe in Bytes oder Zeichen eines Werts in einem **Parameter** Objekt angibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **size** -Eigenschaft, um die maximale Größe für Werte zu ermitteln, die in die [value](./value-property-ado.md) -Eigenschaft eines **Parameter** Objekts geschrieben oder daraus gelesen werden.  
  
 Wenn Sie einen Datentyp variabler Länge für ein **Parameter** Objekt angeben (z. b. einen beliebigen **Zeichen** Folgentyp wie **adVarChar**), müssen Sie die **size** -Eigenschaft des Objekts festlegen, bevor es an die [Parameter](./parameters-collection-ado.md) Auflistung angehängt wird. Andernfalls tritt ein Fehler auf.  
  
 Wenn Sie das **Parameter** Objekt bereits an die **Parameter** Auflistung eines [Befehls](./command-object-ado.md) Objekts angefügt haben und den Typ in einen Datentyp mit variabler Länge ändern, müssen Sie die **size** -Eigenschaft des **Parameter** Objekts festlegen, bevor Sie das **Befehls** Objekt ausführen. Andernfalls tritt ein Fehler auf.  
  
 Wenn Sie die [Refresh](./refresh-method-ado.md) -Methode verwenden, um Parameterinformationen vom Anbieter abzurufen, und ein oder mehrere Datentyp **Parameter** Objekte variabler Länge zurückgibt, kann ADO Arbeitsspeicher für die Parameter zuweisen, basierend auf Ihrer maximalen potenziellen Größe, die während der Ausführung einen Fehler verursachen könnte. Um einen Fehler zu vermeiden, sollten Sie die **size** -Eigenschaft für diese Parameter explizit festlegen, bevor Sie den Befehl ausführen.  
  
 Die **size** -Eigenschaft ist Lese-/Schreibzugriff.  
  
## <a name="applies-to"></a>Gilt für  
 [Parameter-Objekt](./parameter-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VB)](./activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VC + +)](./activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (JScript)](./activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Size-Eigenschaft (ADO-Stream)](./size-property-ado-stream.md)