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
manager: jroth
ms.openlocfilehash: ef6830a02fc7e82d88645e2380d0fc5239793bfc
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66695808"
---
# <a name="commandstream-property-ado"></a>CommandStream-Eigenschaft (ADO)
Gibt den Datenstrom verwendet als Eingabe für eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt den Datenstrom verwendet als Eingabe für eine **Befehl** Objekt. Das Format für diesen Datenstrom ist anbieterspezifisch; finden Sie unter der Dokumentation des Anbieters weitere Informationen. Diese Eigenschaft ähnelt der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft, die an eine Zeichenfolge für die Eingabe eine **Befehl**.  
  
## <a name="remarks"></a>Hinweise  
 **CommandStream** und **CommandText** gegenseitig aus. Wenn der Benutzer legt fest der **' CommandStream '** -Eigenschaft, die **CommandText** Eigenschaft wird auf eine leere Zeichenfolge festgelegt werden (""). Wenn der Benutzer die **CommandText** -Eigenschaft, die **' CommandStream '** Eigenschaft auf festgelegt **"Nothing"** .  
  
 Das Verhalten des der **Command.Parameters.Refresh** und **Command.Prepare** Methoden werden vom Anbieter definiert. Die Werte der Parameter in einem Datenstrom können nicht aktualisiert werden.  
  
 Der Eingabedatenstrom ist nicht verfügbar für andere ADO-Objekte, die die Quelle des Zurückgeben einer **Befehl**. Z. B. wenn die [Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md) von einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) nastaven NA hodnotu eine **Befehl** -Objekt, das einen Datenstrom als Eingabe, hat **Recordset.Source** weiterhin zurück, die **CommandText** -Eigenschaft, die eine leere Zeichenfolge enthält (""), anstatt den Inhalt des Streams von der **' CommandStream '** Eigenschaft.  
  
 Bei Verwendung einer befehlsdatenstrom (nach den Angaben von **' CommandStream '** ), der einzige gültige [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) Werte für die [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) Eigenschaft  **AdCmdText** und **AdCmdUnknown**. Jeder andere Wert verursacht einen Fehler.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Dialect-Eigenschaft](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)
