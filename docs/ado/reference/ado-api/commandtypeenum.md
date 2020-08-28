---
description: CommandTypeEnum
title: Commandtypeaufumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: c23647edbe916daeb3f9356e06de75d11458a59c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975061"
---
# <a name="commandtypeenum"></a>CommandTypeEnum
Gibt an, wie ein Befehls Argument interpretiert werden soll.  
  
 Es ist wichtig, vom Benutzer bereitgestellte *CommandString* -Werte zu validieren, um zu vermeiden, dass Anwendungs Benutzern potenziell gefährliche Befehle zur Ausführung von ADO hinzufügen können.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adcmdunspezifiziert**|-1|Gibt das Befehlstyp Argument nicht an.|  
|**adCmdText**|1|Wertet [CommandText](./commandtext-property-ado.md) als Text Definition eines Befehls oder eines gespeicherten Prozedur Aufrufes aus.|  
|**adCmdTable**|2|Wertet **CommandText** als einen Tabellennamen aus, dessen Spalten von einer intern generierten SQL-Abfrage zurückgegeben werden.|  
|**adCmdStoredProc**|4|Wertet **CommandText** als Namen einer gespeicherten Prozedur aus.|  
|**adCmdUnknown**|8|Standard. Gibt an, dass der Befehlstyp in der **CommandText** -Eigenschaft nicht bekannt ist.<br /><br /> Wenn der Typ des Befehls nicht bekannt ist, werden von ADO mehrere Versuche unternommen, den **CommandText**zu interpretieren.<br /><br /> -   **CommandText** wird als Text Definition eines Befehls oder eines gespeicherten Prozedur Aufrufes interpretiert. Dies entspricht dem Verhalten von **adCmdText**.<br />-   **CommandText** ist der Name einer gespeicherten Prozedur. Dies entspricht dem Verhalten von **adCmdStoredProc**.<br />-   **CommandText** wird als Name einer Tabelle interpretiert. Alle Spalten werden von einer intern generierten SQL-Abfrage zurückgegeben. Dies ist das gleiche Verhalten wie **adCmdTable**.|  
|**adcmdfile**|256|Wertet **CommandText** als den Dateinamen eines permanent gespeicherten [Recordsets](./recordset-object-ado.md)aus. Wird mit **Recordset verwendet.** Nur [Öffnen](./open-method-ado-recordset.md) oder [Requery](./requery-method.md) .|  
|**adCmdTableDirect**|512|Wertet **CommandText** als einen Tabellennamen aus, dessen Spalten alle zurückgegeben werden. Wird nur mit " **Recordset. Open** " oder " **Requery** " verwendet. Um die [Seek](./seek-method.md) -Methode zu verwenden, muss das **Recordset** mit **adCmdTableDirect**geöffnet werden.<br /><br /> Dieser Wert kann nicht mit dem [executeoptionenumum](./executeoptionenum.md) -Wert **adAsyncExecute**kombiniert werden.|  
  
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

:::row:::
    :::column:::
        [CommandType-Eigenschaft (ADO)](./commandtype-property-ado.md)  
        [Execute-Methode (ADO-Befehl)](./execute-method-ado-command.md)  
    :::column-end:::
    :::column:::
        [Execute-Methode (ADO-Verbindung)](./execute-method-ado-connection.md)  
        [Open-Methode (ADO-Recordset)](./open-method-ado-recordset.md)  
    :::column-end:::
    :::column:::
        [Requery-Methode](./requery-method.md)  
    :::column-end:::
:::row-end:::