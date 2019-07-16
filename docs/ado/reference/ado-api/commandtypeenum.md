---
title: CommandTypeEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CommandTypeEnum
helpviewer_keywords:
- CommandTypeEnum enumeration [ADO]
ms.assetid: 4b1feb9c-a855-40fe-a906-efe688687e9f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a2de155d9c4a61246245b2c7f9c3c73a535994a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919686"
---
# <a name="commandtypeenum"></a>CommandTypeEnum
Gibt an, wie ein Befehlsargument interpretiert werden soll.  
  
 Es ist wichtig, überprüfen Sie die benutzerdefinierte *CommandString* Werte zu vermeiden, dass Benutzer die Möglichkeit zum Einfügen von potenziell gefährliche Befehle für ADO zum Ausführen.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adCmdUnspecified**|-1|Es gibt keine das Befehlsargument für den Typ.|  
|**adCmdText**|1|Wertet [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) als Textdefinition einen Befehl oder gespeicherte Prozedur aufrufen.|  
|**adCmdTable**|2|Wertet **CommandText** als den Namen einer Tabelle, deren Spalten sind durch einen intern generierten SQL-Abfrage zurückgegeben.|  
|**adCmdStoredProc**|4|Wertet **CommandText** als Name einer gespeicherten Prozedur.|  
|**adCmdUnknown**|8|Standard. Gibt an, dass der Typ des Befehls in die **CommandText** Eigenschaft ist nicht bekannt.<br /><br /> Wenn der Typ des Befehls nicht bekannt ist, veranlasst ADO mehrere Versuche zum Interpretieren der **CommandText**.<br /><br /> -   **CommandText** wird als Text Definition eines Aufrufs für den Befehl oder gespeicherte Prozedur interpretiert. Dies ist das gleiche Verhalten wie **AdCmdText**.<br />-   **CommandText** ist der Name einer gespeicherten Prozedur. Dies ist das gleiche Verhalten wie **AdCmdStoredProc**.<br />-   **CommandText** wird als Name einer Tabelle interpretiert. Durch einen intern generierten SQL-Abfrage werden alle Spalten zurückgegeben. Dies ist das gleiche Verhalten wie **AdCmdTable**.|  
|**adCmdFile**|256|Wertet **CommandText** als den Dateinamen der dauerhaft gespeicherten [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Mit verwendet **Recordset.** [Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) oder [Requery](../../../ado/reference/ado-api/requery-method.md) nur.|  
|**adCmdTableDirect**|512|Wertet **CommandText** als den Namen einer Tabelle, deren Spalten werden zurückgegeben. Mit verwendet **Recordset.Open** oder **Requery** nur. Verwenden der [Seek](../../../ado/reference/ado-api/seek-method.md) -Methode, die **Recordset** muss geöffnet sein, mit **AdCmdTableDirect**.<br /><br /> Dieser Wert kann nicht kombiniert werden, mit der [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) Wert **AdAsyncExecute**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.CommandType.UNSPECIFIED|  
|AdoEnums.CommandType.TEXT|  
|AdoEnums.CommandType.TABLE|  
|AdoEnums.CommandType.STOREDPROC|  
|AdoEnums.CommandType.UNKNOWN|  
|AdoEnums.CommandType.FILE|  
|AdoEnums.CommandType.TABLEDIRECT|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[CommandType-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)|[Execute-Methode (ADO Command)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Execute-Methode (ADO Connection)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|[Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Requery-Methode](../../../ado/reference/ado-api/requery-method.md)||
