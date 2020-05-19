---
title: Execute-Methode (ADO-Befehl) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f595938fba37e2529f95b763d18dd91731c0b39
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755109"
---
# <a name="execute-method-ado-command"></a>Execute-Methode (ADO-Befehl)
Führt die Abfrage, SQL-Anweisung oder die gespeicherte Prozedur aus, die in der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft oder der [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) -Eigenschaft des [Command-Objekts](../../../ado/reference/ado-api/command-object-ado.md)angegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset = command.Execute( RecordsAffected, Parameters, Options )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt Verweis, einen Stream oder **nichts**zurück.  
  
#### <a name="parameters"></a>Parameter  
 *RecordsAffected*  
 Dies ist optional. Eine **lange** Variable, in der der Anbieter die Anzahl der Datensätze zurückgibt, auf die sich der Vorgang ausgewirkt hat. Der *recordsafffiziert* -Parameter gilt nur für Aktions Abfragen oder gespeicherte Prozeduren. *Recordsaff.* gibt nicht die Anzahl von Datensätzen zurück, die von einer Ergebnis Rückgabe Abfrage oder gespeicherten Prozedur zurückgegeben werden. Um diese Informationen zu erhalten, verwenden Sie die [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) -Eigenschaft. Die **Execute** -Methode gibt bei der Verwendung mit **adAsyncExecute**nicht die richtigen Informationen zurück, weil die Anzahl der betroffenen Datensätze möglicherweise noch nicht bekannt ist, wenn ein Befehl asynchron ausgeführt wird.  
  
 *Parameter*  
 Dies ist optional. Ein **Variant** -Array von Parameterwerten, das in Verbindung mit der in **CommandText** oder **CommandStream**angegebenen Eingabe Zeichenfolge oder dem Stream verwendet wird. (Ausgabeparameter geben bei der Übergabe in dieses Argument keine korrekten Werte zurück.)  
  
 *Optionen*  
 Dies ist optional. Ein **Long** -Wert, der angibt, wie der Anbieter die [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft oder die [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) -Eigenschaft des [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekts auswerten soll. Kann ein Bitmasken Wert sein, der mithilfe von [commandtypeenumund](../../../ado/reference/ado-api/commandtypeenum.md) /oder [executeoptionenumum](../../../ado/reference/ado-api/executeoptionenum.md) -Werten erstellt wird. Beispielsweise können Sie **adCmdText** und **adExecuteNoRecords** kombinieren, wenn ADO den Wert der **CommandText** -Eigenschaft als Text auswerten soll und angeben soll, dass der Befehl Datensätze verwerfen und nicht zurückgeben soll, die bei der Ausführung des Befehls Texts generiert werden könnten.  
  
> [!NOTE]
>  Verwenden Sie den **ExecuteOptionEnum** -Wert **adExecuteNoRecords** , um die Leistung zu verbessern, indem die interne Verarbeitung minimiert wird. Wenn " **adExecuteStream** " angegeben wurde, werden die Optionen " **adasyncfetch** " und " **adAsynchFetchNonBlocking** " ignoriert. Verwenden Sie den **commandtypeenumum** -Wert von **adcmdfile** oder **adCmdTableDirect** nicht mit **Execute**. Diese Werte können nur als Optionen mit den [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -und [Requery](../../../ado/reference/ado-api/requery-method.md) -Methoden eines **Recordsets**verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie die **Execute** -Methode für ein **Command** -Objekt verwenden, wird die in der **CommandText** -Eigenschaft oder der **CommandStream** -Eigenschaft des-Objekts angegebene Abfrage ausgeführt.  
  
 Ergebnisse werden in einem **Recordset** (standardmäßig) oder als Datenstrom binärer Informationen zurückgegeben. Zum Abrufen eines binären Streams geben Sie **adExecuteStream** in *Optionen*an, und geben Sie dann einen Stream durch Festlegen von **Command. Properties ("Ausgabestream")** an. Zum Empfangen der Ergebnisse kann ein ADO- **Stream** -Objekt angegeben werden, oder es kann ein anderes Datenstrom Objekt angegeben werden, z. b. das IIS-Antwortobjekt. Wenn kein Stream vor dem Aufruf von **Execute** with **adExecuteStream**angegeben wurde, tritt ein Fehler auf. Die Position des Streams bei der Rückgabe von **Execute** ist Anbieter spezifisch.  
  
 Wenn der Befehl keine Ergebnisse zurückgeben soll (z. b. eine SQL-Update Abfrage), gibt der Anbieter **nichts** zurück, solange die Option **adExecuteNoRecords** angegeben ist. Andernfalls wird von Execute ein geschlossenes **Recordset**zurückgegeben. Einige Anwendungs Sprachen ermöglichen es Ihnen, diesen Rückgabewert zu ignorieren, wenn kein **Recordset** gewünscht wird.  
  
 **Execute** löst einen Fehler aus, wenn der Benutzer einen Wert für **CommandStream** angibt, wenn der **CommandType** **adCmdStoredProc**, **adCmdTable**oder **adCmdTableDirect**ist.  
  
 Wenn die Abfrage Parameter enthält, werden die aktuellen Werte für die Parameter des **Befehls** Objekts verwendet, es sei denn, Sie überschreiben diese mit Parameterwerten, die mit dem **Execute** -Befehl übergeben werden. Sie können eine Teilmenge der Parameter überschreiben, indem Sie beim Aufrufen der **Execute** -Methode neue Werte für einige Parameter weglassen. Die Reihenfolge, in der Sie die Parameter angeben, entspricht der Reihenfolge, in der die Methode Sie übergibt. Wenn beispielsweise vier (oder mehr) Parameter vorhanden sind und Sie neue Werte nur für den ersten und vierten Parameter übergeben möchten, übergeben Sie `Array(var1,,,var4)` als *Parameter* Argument.  
  
> [!NOTE]
>  Ausgabeparameter geben keine korrekten Werte zurück, wenn Sie im *Parameter* Argument angegeben werden.  
  
 Ein [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md) -Ereignis wird ausgegeben, wenn dieser Vorgang abgeschlossen wird.  
  
> [!NOTE]
>  Bei der Ausgabe von Befehlen, die das http-Schema verwenden, wird automatisch der [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung aufgerufen](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Execute, Requery und Clear Methods (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Beispiel für Execute, Requery und Clear Methods (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Beispiel für Execute, Requery und Clear Methods (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandStream-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Commandtypeaufumum](../../../ado/reference/ado-api/commandtypeenum.md)   
 [Execute-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [ExecuteComplete-Ereignis (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)
