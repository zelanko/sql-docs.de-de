---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0cd6d06a50047f431700af9418a504faa4bd6957
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919696"
---
# <a name="commandtype-property-ado"></a>CommandType-Eigenschaft (ADO)
Gibt den Typ eines [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen oder mehrere [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) -Werte fest oder gibt ihn zurück.  
  
> [!NOTE]
>  Verwenden Sie die **commandtypeaufum** -Werte **adcmdfile** oder **adCmdTableDirect** nicht mit **CommandType**. Diese Werte können nur als Optionen mit den [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -und [Requery](../../../ado/reference/ado-api/requery-method.md) -Methoden eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **CommandType** -Eigenschaft, um die Auswertung der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft zu optimieren.  
  
 Wenn der **CommandType** -Eigenschafts Wert auf den Standardwert **adCmdUnknown**festgelegt ist, kann die Leistung beeinträchtigt werden, da ADO Aufrufe an den Anbieter ausführen muss, um zu bestimmen, ob die **CommandText** -Eigenschaft eine SQL-Anweisung, eine gespeicherte Prozedur oder ein Tabellenname ist. Wenn Sie wissen, welche Art von Befehl Sie verwenden, weist das Festlegen der **CommandType** -Eigenschaft ADO an, direkt zum relevanten Code zu wechseln. Wenn die **CommandType** -Eigenschaft nicht mit dem Typ des Befehls in der **CommandText** -Eigenschaft identisch ist, tritt ein Fehler auf, wenn Sie die [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -Methode aufruft.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
