---
title: CommandStream-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::CommandStream
helpviewer_keywords:
- CommandStream property [ADO]
ms.assetid: f78f61b6-87e0-48dc-961e-83d0e20da58e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 23ec65380bfea16d38f02cab0a070ab69f85d525
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67919749"
---
# <a name="commandstream-property-ado"></a>CommandStream-Eigenschaft (ADO)
Gibt den Datenstrom an, der als Eingabe für ein [Command](../../../ado/reference/ado-api/command-object-ado.md) -Objekt verwendet wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt den als Eingabe für ein **Befehls** Objekt verwendeten Stream fest oder gibt diesen zurück. Das Format für diesen Stream ist Anbieter spezifisch. Weitere Informationen finden Sie in der Dokumentation Ihres Anbieters. Diese Eigenschaft ähnelt der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft, die zum Angeben einer Zeichenfolge für die Eingabe eines **Befehls**verwendet wurde.  
  
## <a name="remarks"></a>Bemerkungen  
 **CommandStream** und **CommandText** schließen sich gegenseitig aus. Wenn der Benutzer die **CommandStream** -Eigenschaft festlegt, wird die **CommandText** -Eigenschaft auf die leere Zeichenfolge ("") festgelegt. Wenn der Benutzer die **CommandText** -Eigenschaft festlegt, wird die **CommandStream** -Eigenschaft auf " **Nothing**" festgelegt.  
  
 Das Verhalten der **Command. Parameters. Refresh** -Methode und der **Command. Prepare** -Methode werden vom Anbieter definiert. Die Werte von Parametern in einem Stream können nicht aktualisiert werden.  
  
 Der Eingabestream ist für andere ADO-Objekte, die die Quelle eines **Befehls**zurückgeben, nicht verfügbar. Wenn z. b. die [Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md) eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md) auf ein **Befehls** Objekt festgelegt ist, das über einen Stream als Eingabe verfügt, gibt **Recordset. Source** weiterhin die **CommandText** -Eigenschaft zurück, die eine leere Zeichenfolge ("") enthält, anstelle des streaminhalts der **CommandStream** -Eigenschaft.  
  
 Wenn Sie einen Befehlsdaten Strom (wie von **CommandStream**angegeben) verwenden, sind die einzigen gültigen [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) -Werte für die [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) -Eigenschaft **adCmdText** und **adCmdUnknown**. Jeder andere Wert verursacht einen Fehler.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Dialekt Eigenschaft](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)
