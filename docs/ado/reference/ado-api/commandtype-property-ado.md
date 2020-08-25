---
description: CommandType-Eigenschaft (ADO)
title: CommandType-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
author: rothja
ms.author: jroth
ms.openlocfilehash: 0216a04051ee45cf92d5451396c8012dbd47fe7b
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776089"
---
# <a name="commandtype-property-ado"></a>CommandType-Eigenschaft (ADO)
Gibt den Typ eines [Befehls](./command-object-ado.md) Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen oder mehrere [CommandTypeEnum](./commandtypeenum.md) -Werte fest oder gibt ihn zurück.  
  
> [!NOTE]
>  Verwenden Sie die **commandtypeaufum** -Werte **adcmdfile** oder **adCmdTableDirect** nicht mit **CommandType**. Diese Werte können nur als Optionen mit den [Open](./open-method-ado-recordset.md) -und [Requery](./requery-method.md) -Methoden eines [Recordsets](./recordset-object-ado.md)verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **CommandType** -Eigenschaft, um die Auswertung der [CommandText](./commandtext-property-ado.md) -Eigenschaft zu optimieren.  
  
 Wenn der **CommandType** -Eigenschafts Wert auf den Standardwert **adCmdUnknown**festgelegt ist, kann die Leistung beeinträchtigt werden, da ADO Aufrufe an den Anbieter ausführen muss, um zu bestimmen, ob die **CommandText** -Eigenschaft eine SQL-Anweisung, eine gespeicherte Prozedur oder ein Tabellenname ist. Wenn Sie wissen, welche Art von Befehl Sie verwenden, weist das Festlegen der **CommandType** -Eigenschaft ADO an, direkt zum relevanten Code zu wechseln. Wenn die **CommandType** -Eigenschaft nicht mit dem Typ des Befehls in der **CommandText** -Eigenschaft identisch ist, tritt ein Fehler auf, wenn Sie die [Execute](./execute-method-ado-command.md) -Methode aufruft.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VB)](./activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VC + +)](./activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (JScript)](./activeconnection-commandtext-timeout-type-size-example-jscript.md)