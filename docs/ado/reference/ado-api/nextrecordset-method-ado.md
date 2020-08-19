---
description: NextRecordset-Methode (ADO)
title: NextRecordset-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- NextRecordset
- Recordset15::NextRecordset
- Recordset15::raw_NextRecordset
helpviewer_keywords:
- NextRecordset method [ADO]
ms.assetid: ab1fa449-a695-4987-b1ee-bc68f89418dd
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ec3bb3a6c5f7e4f6d6654ca059e7ace7d97d9da
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443092"
---
# <a name="nextrecordset-method-ado"></a>NextRecordset-Methode (ADO)
Löscht das aktuelle [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt und gibt das nächste **Recordset** zurück, indem eine Reihe von Befehlen durchlaufen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein **Recordset** -Objekt zurück. Im Syntax Modell können *Recordset1* und *Recordset2* dasselbe **Recordset** -Objekt sein, oder Sie können separate Objekte verwenden. Wenn Sie separate **Recordset** -Objekte verwenden, generiert das Zurücksetzen der **ActiveConnection** -Eigenschaft für das ursprüngliche **Recordset** (*Recordset1*) nach dem Aufrufen von **NextRecordset** einen Fehler.  
  
#### <a name="parameters"></a>Parameter  
 *RecordsAffected*  
 Optional. Eine **lange** Variable, in der der Anbieter die Anzahl der Datensätze zurückgibt, auf die sich der aktuelle Vorgang ausgewirkt hat.  
  
> [!NOTE]
>  Dieser Parameter gibt nur die Anzahl der Datensätze zurück, die von einem Vorgang betroffen sind. Sie gibt nicht die Anzahl von Datensätzen aus einer SELECT-Anweisung zurück, die zum Generieren des **Recordsets verwendet wurde**.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **NextRecordset** -Methode, um die Ergebnisse des nächsten Befehls in einer Verbund Befehls Anweisung oder einer gespeicherten Prozedur zurückzugeben, die mehrere Ergebnisse zurückgibt. Wenn Sie ein **Recordset** -Objekt auf der Grundlage einer Verbund Befehls Anweisung öffnen (z. b \* . "SELECT FROM table1; Select \* from table2 ") mithilfe der [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -Methode für einen [Befehl](../../../ado/reference/ado-api/command-object-ado.md) oder der [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode in einem **Recordset**führt ADO nur den ersten Befehl aus und gibt die Ergebnisse an *Recordset*zurück. Um auf die Ergebnisse der nachfolgenden Befehle in der Anweisung zuzugreifen, müssen Sie die **NextRecordset** -Methode aufrufen.  
  
 Solange zusätzliche Ergebnisse vorhanden sind und das **Recordset** , das die Verbund Anweisungen enthält, nicht getrennt oder über Prozess Grenzen hinweg gemarshallt wird, gibt die **NextRecordset** -Methode weiterhin **Recordset** -Objekte zurück. Wenn ein Zeilen Rückgabe Befehl erfolgreich ausgeführt wird, aber keine Datensätze zurückgibt, ist das zurückgegebene **Recordset** -Objekt geöffnet, aber leer. Testen Sie diesen Fall, indem Sie überprüfen, ob die Eigenschaften [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) und [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) beide **zutreffen**. Wenn ein Befehl, der keine Zeilen zurückgibt, erfolgreich ausgeführt wird, wird das zurückgegebene **Recordset** -Objekt geschlossen, das Sie überprüfen können, indem Sie die [State](../../../ado/reference/ado-api/state-property-ado.md) -Eigenschaft des **Recordsets**testen. Wenn keine weiteren Ergebnisse vorliegen, wird *Recordset* auf " *Nothing*" festgelegt.  
  
 Die **NextRecordset** -Methode ist für ein nicht verbundenes **Recordset** -Objekt nicht verfügbar, bei dem [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) auf ' **Nothing** ' (in Microsoft Visual Basic) oder auf NULL (in anderen Sprachen) festgelegt wurde.  
  
 Wenn im sofortigen Update Modus eine Bearbeitung ausgeführt wird, generiert der Aufruf der **NextRecordset** -Methode einen Fehler. nennen Sie zuerst die [Update](../../../ado/reference/ado-api/update-method.md) -oder [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) -Methode.  
  
 Um Parameter für mehr als einen Befehl in der Verbund Anweisung zu übergeben, indem Sie die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung ausfüllen oder ein Array mit dem ursprünglichen **Open** -oder **Execute** -Befehl übergeben, müssen die Parameter in der gleichen Reihenfolge wie die entsprechenden Befehle in der Befehls Reihe in der Auflistung oder im Array vorliegen. Sie müssen das Lesen aller Ergebnisse abschließen, bevor Sie Ausgabeparameter Werte lesen.  
  
 Der OLE DB-Anbieter bestimmt, wann jeder Befehl in einer Verbund Anweisung ausgeführt wird. Der [Microsoft OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)führt z. b. alle Befehle in einem Batch aus, wenn die Verbund Anweisung empfangen wird. Die sich ergebenden **Recordsets** werden einfach zurückgegeben, wenn Sie **NextRecordset**aufruft.  
  
 Andere Anbieter führen den nächsten Befehl jedoch möglicherweise nur in einer Anweisung aus, nachdem NextRecordset aufgerufen wurde. Wenn Sie für diese Anbieter das **Recordset** -Objekt explizit schließen, bevor Sie die gesamte Befehls Anweisung durchlaufen, führt ADO die verbleibenden Befehle nie aus.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [NextRecordset-Methode (Beispiel) (VB)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [NextRecordset-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   
