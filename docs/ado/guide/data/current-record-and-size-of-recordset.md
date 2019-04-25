---
title: Aktueller Datensatz und Größe des Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e63ff331-8655-4be7-82c6-e6cd6cc9d16d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bde55939e974c6c879dcd126fac863ef0a866487
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472603"
---
# <a name="current-record-and-size-of-recordset"></a>Aktueller Datensatz und Größe des Recordsets
In diesem Abschnitt wird beschrieben, wie Sie die aktuelle Position des Cursors im Beispiel finden **Recordset** in [JScript-Codebeispiel zum Zurückgeben eines Recordsets](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md).  
  
## <a name="current-record"></a>Aktueller Datensatz  
 Der aktuelle Datensatz im Dataset entspricht, die durch die Position des Cursors von gezeigt die **Recordset** Objekt. Wenn eine **Recordset** Objekt wird aus der Datenquelle zurückgegeben, als das Ergebnis des Aufrufs **Recordset.Open**, **Recordset.Open**, oder **Connection.Execute**  (einschließlich **Connection.NamedCommand** und **Connection.StoredProcedure**), der Cursor auf den ersten Datensatz festgelegt ist. In der Beispiel-Dataset ist der anfänglichen aktuelle Datensatz "Onkel Bobs organische Dried Birnen" Element.  
  
## <a name="size-of-recordset"></a>Größe des Recordsets  
 Zum Ermitteln der Größe einer **Recordset** Objekt, rufen Sie den Wert von der **Recordset.RecordCount** Eigenschaft. Dieser Wert ist eine lange ganze Zahl, die gibt die Anzahl der Datensätze in der **Recordset**. Wenn das Dataset aus der OLE DB-Anbieter für Microsoft SQL Server zurückgegeben wird, wird mit diesem Wert die Anzahl der zurückgegebenen Zeilen. Lesen der **RecordCount** Eigenschaft für ein geschlossenes **Recordset** verursacht einen Fehler.  
  
 Wenn die Anzahl der Datensätze nicht bestimmt werden kann, ist es sich bei der Wert der Eigenschaft um 1.  
  
 Der Wert des der **RecordCount** Eigenschaft hängt auch von den Funktionen des Anbieters und den Typ des Cursors verwendet. Für einen Vorwärtscursor ist der Wert-1 auf. Für einen statischen oder einen Keyset-Cursor, der Wert ist die tatsächliche Anzahl der zurückgegebenen Datensätze in der **Recordset** Objekt. Für einen dynamischen Cursor ist der Wert entweder-1 oder die tatsächliche Anzahl der Datensätze, abhängig von der Datenquelle.  
  
 Ein Cursor, der unterstützt **Recordcount** müssen Arbeit schwieriger und aus diesem Grund erfordert mehr rechenleistung als ein Cursor nicht unterstützt **Recordcount**. Wenn Sie nicht benötigen, die Anzahl der Datensätze zu wissen, können verschiedene Cursortyp Informationen verbessert die Leistung Ihrer Anwendung, insbesondere dann, wenn Sie ein großes DataSet behandelt werden müssen.  
  
 In einigen Fällen ein Anbieter oder der Cursor kann nicht feststellen der **RecordCount** Wert ohne zuerst alle Datensätze aus der Datenquelle abgerufen. Aufrufen, um sicherzustellen, dass genau zählen, die **Recordset**. **MoveLast** Methode vor dem Aufruf **Recordset.RecordCount**.  
  
 Das Beispiel **Recordset** Objekt abgerufen, mit der [JScript-Codebeispiel](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md) verwendet einen Vorwärtscursor, daher ist das Aufrufen **RecordCount** für dieses Objekt führt immer-1. Wenn Sie die Zeile des Codes ändern, die Aufrufe der **Recordset**. **Open** Methode, wie im folgenden Beispiel gezeigt die **RecordCount** Eigenschaft gibt die tatsächliche Anzahl der abgerufenen Datensätze zurück.  
  
```  
oRs.Open sSQL, sCnStr, adOpenStatic, adLockOptimistic, adCmdText   
```  
  
 Grund hierfür ist, statische Cursor mit dem [Microsoft OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) unterstützen **RecordCount**. In diesem Beispiel fünf Datensätze vorhanden sind und somit **RecordCount** sollte den Wert 5 ergibt.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
 [Grenzen eines Recordsets](../../../ado/guide/data/boundaries-of-a-recordset.md)
