---
title: Commandtypeaufumum | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 68572a642333e4e9c2c334cd7680b96b0cacced3
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760376"
---
# <a name="commandtypeenum"></a>CommandTypeEnum
Gibt an, wie ein Befehls Argument interpretiert werden soll.  
  
 Es ist wichtig, vom Benutzer bereitgestellte *CommandString* -Werte zu validieren, um zu vermeiden, dass Anwendungs Benutzern potenziell gefährliche Befehle zur Ausführung von ADO hinzufügen können.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adcmdunspezifiziert**|-1|Gibt das Befehlstyp Argument nicht an.|  
|**adCmdText**|1|Wertet [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) als Text Definition eines Befehls oder eines gespeicherten Prozedur Aufrufes aus.|  
|**adCmdTable**|2|Wertet **CommandText** als einen Tabellennamen aus, dessen Spalten von einer intern generierten SQL-Abfrage zurückgegeben werden.|  
|**adCmdStoredProc**|4|Wertet **CommandText** als Namen einer gespeicherten Prozedur aus.|  
|**adCmdUnknown**|8|Standard. Gibt an, dass der Befehlstyp in der **CommandText** -Eigenschaft nicht bekannt ist.<br /><br /> Wenn der Typ des Befehls nicht bekannt ist, werden von ADO mehrere Versuche unternommen, den **CommandText**zu interpretieren.<br /><br /> -   **CommandText** wird als Text Definition eines Befehls oder eines gespeicherten Prozedur Aufrufes interpretiert. Dies entspricht dem Verhalten von **adCmdText**.<br />-   **CommandText** ist der Name einer gespeicherten Prozedur. Dies entspricht dem Verhalten von **adCmdStoredProc**.<br />-   **CommandText** wird als Name einer Tabelle interpretiert. Alle Spalten werden von einer intern generierten SQL-Abfrage zurückgegeben. Dies ist das gleiche Verhalten wie **adCmdTable**.|  
|**adcmdfile**|256|Wertet **CommandText** als den Dateinamen eines permanent gespeicherten [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)aus. Wird mit **Recordset verwendet.** Nur [Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) oder [Requery](../../../ado/reference/ado-api/requery-method.md) .|  
|**adCmdTableDirect**|512|Wertet **CommandText** als einen Tabellennamen aus, dessen Spalten alle zurückgegeben werden. Wird nur mit " **Recordset. Open** " oder " **Requery** " verwendet. Um die [Seek](../../../ado/reference/ado-api/seek-method.md) -Methode zu verwenden, muss das **Recordset** mit **adCmdTableDirect**geöffnet werden.<br /><br /> Dieser Wert kann nicht mit dem [executeoptionenumum](../../../ado/reference/ado-api/executeoptionenum.md) -Wert **adAsyncExecute**kombiniert werden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoerums. CommandType. nicht angegeben|  
|Adoerums. CommandType. Text|  
|Adoerums. CommandType. Table|  
|Adoerums. CommandType. StoredProc|  
|Adoerums. CommandType. Unknown|  
|Adoerums. CommandType. file|  
|Adoerums. CommandType. TableDirect|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[CommandType-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)|[Execute-Methode (ADO-Befehl)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Execute-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|[Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Requery-Methode](../../../ado/reference/ado-api/requery-method.md)||
