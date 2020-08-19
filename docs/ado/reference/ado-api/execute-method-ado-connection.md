---
description: Execute-Methode (ADO-Verbindung)
title: Execute-Methode (ADO-Verbindung) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Execute
- Connection15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 03c69320-96b2-4d85-8d49-a13b13e31578
author: rothja
ms.author: jroth
ms.openlocfilehash: 1acbdc4966f46d5e155dab3fac059568699d4727
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443912"
---
# <a name="execute-method-ado-connection"></a>Execute-Methode (ADO-Verbindung)
Führt die angegebene Abfrage, die SQL-Anweisung, die gespeicherte Prozedur oder den anbieterspezifischen Text aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen ADO-Objekt Verweis [(Recordset Object)](../../../ado/reference/ado-api/recordset-object-ado.md) zurück.  
  
#### <a name="parameters"></a>Parameter  
 *CommandText*  
 Ein **Zeichen** folgen Wert, der die SQL-Anweisung, die gespeicherte Prozedur, eine URL oder einen anbieterspezifischen Text enthält, der ausgeführt werden soll. **Optional**können Tabellennamen verwendet werden, aber nur, wenn der Anbieter SQL unterstützt. Wenn z. b. ein Tabellenname mit dem Namen "Customers" verwendet wird, stellt ADO automatisch die standardmäßige SQL SELECT-Syntax zum bilden voran und übergibt "SELECT * FROM Customers" als [!INCLUDE[tsql](../../../includes/tsql-md.md)] Anweisung an den Anbieter.  
  
 *RecordsAffected*  
 Optional. Eine **lange** Variable, in der der Anbieter die Anzahl der Datensätze zurückgibt, auf die sich der Vorgang ausgewirkt hat.  
  
 *Optionen*  
 Optional. Ein **Long** -Wert, der angibt, wie der Anbieter das CommandText-Argument auswerten soll. Kann eine Bitmaske mit einem oder mehreren [commandtypeenumerationswerten](../../../ado/reference/ado-api/commandtypeenum.md) oder [executeoptionenumum](../../../ado/reference/ado-api/executeoptionenum.md) -Werten sein.  
  
 **Hinweis** Verwenden Sie den **ExecuteOptionEnum** -Wert **adExecuteNoRecords** , um die Leistung zu verbessern, indem Sie die interne Verarbeitung minimieren und Anwendungen, die Sie aus Visual Basic 6,0 portieren.  
  
 Verwenden Sie nicht **adExecuteStream** mit der **Execute** -Methode eines **Connection** -Objekts.  
  
 Verwenden Sie den commandtypeenumum-Wert von adcmdfile oder adCmdTableDirect nicht mit Execute. Diese Werte können nur als Optionen mit den Methoden der [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) und der [Requery-Methode](../../../ado/reference/ado-api/requery-method.md) eines **Recordsets**verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Verwendung der Execute-Methode für ein [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt führt jede **beliebige** Abfrage aus, die Sie im CommandText-Argument der angegebenen Verbindung an die-Methode übergeben. Wenn das CommandText-Argument eine Abfrage mit Zeilen Rückgabe angibt, werden alle von der Ausführung generierten Ergebnisse in einem neuen **Recordset** -Objekt gespeichert. Wenn der Befehl keine Ergebnisse zurückgeben soll (z. b. eine SQL-Update Abfrage), gibt der Anbieter **nichts** zurück, solange die Option **adExecuteNoRecords** angegeben ist. Andernfalls wird von Execute ein geschlossenes **Recordset**zurückgegeben.  
  
 Das zurückgegebene **Recordset** -Objekt ist immer ein Schreib geschützter Vorwärts Cursor. Wenn Sie ein **Recordset** -Objekt mit mehr Funktionalität benötigen, erstellen Sie zunächst ein **Recordset** -Objekt mit den gewünschten Eigenschafts Einstellungen, und verwenden Sie dann die [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode des **Recordset** -Objekts, um die Abfrage auszuführen und den gewünschten Cursortyp zurückzugeben.  
  
 Der Inhalt des *CommandText* -Arguments ist spezifisch für den Anbieter und kann eine SQL-Standard Syntax oder ein beliebiges spezielles Befehls Format sein, das der Anbieter unterstützt.  
  
 Ein ExecuteComplete-Ereignis wird ausgegeben, wenn dieser Vorgang abgeschlossen wird.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
