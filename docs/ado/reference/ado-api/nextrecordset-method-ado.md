---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c7af4f5d217670ab23e71a3c53ccd5cf7944b0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932036"
---
# <a name="nextrecordset-method-ado"></a>NextRecordset-Methode (ADO)
Löscht das aktuelle [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt und gibt die nächste **Recordset** durch eine Reihe von Befehlen gelangt sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Recordset** Objekt. Im Syntaxmodell *recordset1* und *recordset2* gleich sein **Recordset** -Objekt, oder Sie können separate Objekte. Verwendung von separaten **Recordset** Objekte, die Zurücksetzen der **ActiveConnection** -Eigenschaft im ursprünglichen **Recordset** (*recordset1*) nach dem **NextRecordset** wird aufgerufen wurde ein Fehler generiert.  
  
#### <a name="parameters"></a>Parameter  
 *RecordsAffected*  
 Optional. Ein **lange** Variablen zu dem der Anbieter gibt die Anzahl der Datensätze, die der aktuelle Vorgang betroffen.  
  
> [!NOTE]
>  Dieser Parameter gibt nur die Anzahl der Datensätze, die von einem Vorgang betroffen; Es werden keine Anzahl der Datensätze zurückgegeben, von einer select-Anweisung zum Generieren der **Recordset**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **NextRecordset** -Methode zur Rückgabe der Ergebnisse von den nächsten Befehl in einer zusammengesetzten Command-Anweisung oder einer gespeicherten Prozedur, die mehrere Ergebnisse zurückgibt. Beim Öffnen einer **Recordset** Objekt auf Grundlage einer zusammengesetzten-befehlsanweisung (z. B. "wählen \* von table1; SELECT \* von table2 ") mit der [ausführen](../../../ado/reference/ado-api/execute-method-ado-command.md) Methode für eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) oder [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methode für eine **Recordset**, ADO führt nur den ersten Befehl und gibt die Ergebnisse an *Recordset*. Um die Ergebnisse der nachfolgenden Befehle in der Anweisung zuzugreifen, rufen die **NextRecordset** Methode.  
  
 Als zusätzliche Ergebnisse vorhanden sind und die **Recordset** nicht getrennt oder Prozessgrenzen, gemarshallt wird, enthält die verbundanweisungen der **NextRecordset** Methode weiterhin zurückgeben **Recordset** Objekte. Wenn ein Zeile zurückgeben-Befehl erfolgreich ausgeführt wird, aber keine Datensätze, die den zurückgegebenen gibt **Recordset** Objekt wird geöffnet, aber leer sein. Tests für diesen Fall, indem Sie überprüfen, ob die [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) und [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) Eigenschaften sind beide **"true"** . Wenn ein Befehl nicht auf Zeilen zurückgebende erfolgreich zurückgegebenen ausgeführt wird **Recordset** -Objekt geschlossen, dies kann durch Tests überprüfen, die [Zustand](../../../ado/reference/ado-api/state-property-ado.md) Eigenschaft für die **Recordset**. Wenn es keine weiteren Ergebnisse sind, *Recordset* festgelegt *nichts*.  
  
 Die **NextRecordset** Methode ist nicht verfügbar, auf einem nicht verbundenen **Recordset** Objekt, in denen [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) festgelegt wurde **nichts**(in Microsoft Visual Basic) oder NULL (in anderen Sprachen).  
  
 Wenn ein Bearbeitungsvorgang ausgeführt, während er sich im sofortupdatemodus ist, wird beim Aufrufen der **NextRecordset** Methode wird ein Fehler generiert, rufen Sie die [aktualisieren](../../../ado/reference/ado-api/update-method.md) oder [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) Methode erste.  
  
 Zum Übergeben von Parametern, für mehr als einen Befehl in die verbundanweisung durch Ausfüllen der [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Sammlung oder durch Übergeben eines Arrays mit dem ursprünglichen **öffnen** oder **Execute** aufrufen, müssen die Parameter in der gleichen Reihenfolge in der Auflistung oder ein Array als den dazugehörigen Befehlen in der Reihe Befehl sein. Sie müssen das Einlesen aller Ergebnisse vor dem Lesen von Ausgabeparameterwerte beenden.  
  
 OLE DB-Anbieter bestimmt, wann jeder Befehl in einer verbundanweisung ausgeführt wird. Die [Microsoft OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), z. B. alle Befehle in einem Batch nach dem Empfang der verbundanweisung ausführt. Die resultierende **Recordsets** werden einfach zurückgegeben werden, wenn Sie aufrufen **NextRecordset**.  
  
 Jedoch können andere Anbieter den nächsten Befehl in einer Anweisung ausführen, nur nach NextRecordset aufgerufen wird. Bei diesen Anbietern, wenn Sie explizit schließen die **Recordset** object, bevor der gesamte Befehl-Anweisung durchlaufen ADO wird nie die restlichen Befehle ausgeführt.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [NextRecordset-Methode – Beispiel (VB)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [NextRecordset-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   
