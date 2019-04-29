---
title: Execute-Methode (ADO Command) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::Execute
- Command15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: f84a5ff3-0528-4ad7-9bea-9a15103378dd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9508b85bc73ebbec82ad7d3bea5af5148d7c674
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184806"
---
# <a name="execute-method-ado-command"></a>Execute-Methode (ADO-Befehl)
Führt die Abfrage, SQL-Anweisung oder gespeicherte Prozedur, die im angegebenen die [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) oder [' CommandStream '](../../../ado/reference/ado-api/commandstream-property-ado.md) Eigenschaft der [Befehlsobjekt](../../../ado/reference/ado-api/command-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset = command.Execute( RecordsAffected, Parameters, Options )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objektverweis, einen Stream oder **nichts**.  
  
#### <a name="parameters"></a>Parameter  
 *RecordsAffected*  
 Dies ist optional. Ein **lange** Variablen zu dem der Anbieter gibt die Anzahl der Datensätze, die der Vorgang betroffen. Die *RecordsAffected* Parameter gilt nur für die Aktionsabfragen oder gespeicherte Prozeduren. *RecordsAffected* ist nicht die Anzahl der von einer Abfrage zurückgeben oder der gespeicherten Prozedur zurückgegebenen Datensätze zurück. Verwenden Sie zum Abrufen dieser Informationen die [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) Eigenschaft. Die **Execute** Methode gibt nicht die richtige Informationen bei Verwendung mit **AdAsyncExecute**, einfach weil bei ein Befehl asynchron ausgeführt wird, die Anzahl der betroffenen Datensätze möglicherweise noch nicht bekannt zum Zeitpunkt zurückgegeben der Methode.  
  
 *Parameter*  
 Dies ist optional. Ein **Variant** Array von Parameterwerten, die zusammen mit der Eingabezeichenfolge oder den Stream, die im angegebenen **CommandText** oder **' CommandStream '**. (Output-Parameter gibt nicht korrekten Werte, wenn dieses Argument übergeben.)  
  
 *Optionen*  
 Dies ist optional. Ein **lange** Wert, der angibt, wie der Anbieter auswerten soll, die [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) oder [' CommandStream '](../../../ado/reference/ado-api/commandstream-property-ado.md) Eigenschaft der [Befehl](../../../ado/reference/ado-api/command-object-ado.md) -Objekt. Ein Bitmaskenwert mit möglich [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) und/oder [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) Werte. Beispielsweise können Sie **AdCmdText** und **AdExecuteNoRecords** in Verbindung, wenn Sie den Wert des ADO möchten die **CommandText** -Eigenschaft, wie Text, und Geben Sie an, dass der Befehl sollte verwerfen und keine Datensätze, die ausgegeben werden könnten zurück, wenn der Befehlstext ausgeführt wird.  
  
> [!NOTE]
>  Verwenden der **ExecuteOptionEnum** Wert **AdExecuteNoRecords** zur Verbesserung der Leistung durch Minimierung der internen Verarbeitung. Wenn **AdExecuteStream** angegeben wurde, die Optionen **AdAsyncFetch** und **AdAsynchFetchNonBlocking** werden ignoriert. Verwenden Sie nicht die **CommandTypeEnum** Werte **AdCmdFile** oder **AdCmdTableDirect** mit **Execute**. Diese Werte können nur verwendet werden, als Optionen, mit der [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) und [Requery](../../../ado/reference/ado-api/requery-method.md) Methoden eine **Recordset**.  
  
## <a name="remarks"></a>Hinweise  
 Mit der **ausführen** Methode für eine **Befehl** -Objekt ausgeführt wird, die Abfrage der **CommandText** Eigenschaft oder **' CommandStream '** die Eigenschaft des Objekts.  
  
 Ergebnisse werden zurückgegeben, einem **Recordset** (standardmäßig) oder als zeichendatenstrom an binären Informationen. Geben Sie zum Abrufen eines binären Streams **AdExecuteStream** in *Optionen*, geben Sie dann einen Datenstrom durch Festlegen von **Command.Properties ("Output Stream")**. Ein ADO **Stream** Objekt angegeben werden, um die Ergebnisse zu erhalten, oder einen anderen Stream-Objekt, z. B. das IIS-Response-Objekt angegeben werden. Wenn kein Stream vor dem Aufruf angegeben wurde **Execute** mit **AdExecuteStream**, ein Fehler auftritt. Die Position des Streams bei der Rückgabe von **Execute** ist Anbieter spezifisch.  
  
 Der Anbieter gibt zurück, wenn der Befehl nicht beabsichtigt ist, Zurückgeben von Ergebnissen (z. B. ein UPDATE für SQL-Abfrage) **nichts** so lange wie die Option **AdExecuteNoRecords** angegeben ist; andernfalls ausführen gibt ein geschlossen **Recordset**. Einige Sprachen können Sie diesen Rückgabewert ignoriert werden sollen, wenn kein **Recordset** erwünscht ist.  
  
 **Führen Sie** löst einen Fehler aus, wenn der Benutzer einen Wert für angibt **' CommandStream '** bei der **CommandType** ist **AdCmdStoredProc**,  **AdCmdTable**, oder **AdCmdTableDirect**.  
  
 Wenn die Abfrage Parameter enthält, die aktuellen Werte von der **Befehl** des Objekts Parameter werden verwendet, es sei denn, Sie diese mit Parameterwerten, die mit übergebenen außer Kraft setzen der **Execute** aufrufen. Sie können eine Teilmenge der Parameter überschreiben, indem Sie neue Werte für einige der Parameter ausgelassen wird, beim Aufrufen der **Execute** Methode. Die Reihenfolge, in der Sie die Parameter angeben, wird der gleichen Reihenfolge, in der Sie die Methode übergibt. Wenn vier (oder mehr) Parameter verfügt, sind und Sie neue Werte für die nur die erste und vierte Parameter übergeben möchten, übergeben Sie z. B. `Array(var1,,,var4)` als die *Parameter* Argument.  
  
> [!NOTE]
>  Output-Parameter werden nicht als Rückgabewerte korrekt beim Übergeben der *Parameter* Argument.  
  
 Ein [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md) Ereignis wird ausgegeben werden, wenn dieser Vorgang abgeschlossen ist.  
  
> [!NOTE]
>  Befehle, die mit den URLs ausgegeben wird, ruft solche, die das HTTP-Schema verwenden automatisch die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Execute, Requery und Clear-Methode – Beispiel (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery und Clear-Methode – Beispiel (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery und Clear-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandStream-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)   
 [Execute-Methode (ADO Connection)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [ExecuteComplete-Ereignis (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)
