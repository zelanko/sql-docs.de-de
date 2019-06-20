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
manager: jroth
ms.openlocfilehash: 5fde8adfb1b3f78e8dd0d047f8b100ddada4608c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698687"
---
# <a name="commandtype-property-ado"></a>CommandType-Eigenschaft (ADO)
Gibt den Typ des eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt eine oder mehrere [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) Werte.  
  
> [!NOTE]
>  Verwenden Sie nicht die **CommandTypeEnum** Werte **AdCmdFile** oder **AdCmdTableDirect** mit **CommandType**. Diese Werte können nur verwendet werden, als Optionen, mit der [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) und [Requery](../../../ado/reference/ado-api/requery-method.md) Methoden eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Befehlstyp (CommandType)** Eigenschaft zur Auswertung der Optimierung der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) Eigenschaft.  
  
 Wenn die **Befehlstyp (CommandType)** Eigenschaftswert wird auf den Standardwert festgelegt **AdCmdUnknown**, treten möglicherweise Leistungseinbußen hinnehmbar da ADO Aufrufe an den Anbieter zu entscheiden, ob vornehmen, muss die  **CommandText** -Eigenschaft ist eine SQL-Anweisung, einer gespeicherten Prozedur oder einen Tabellennamen an. Wenn Sie wissen, welche Art von Befehl, die Sie verwenden werden, Festlegen der **Befehlstyp (CommandType)** rowsetcache ADO, um direkt auf den gewünschten Code zu wechseln. Wenn die **Befehlstyp (CommandType)** Eigenschaft entspricht nicht den Typ des Befehls in die **CommandText** -Eigenschaft, ein Fehler auftritt, beim Aufrufen der [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) Methode.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
