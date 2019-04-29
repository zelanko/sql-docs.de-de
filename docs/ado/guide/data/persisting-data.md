---
title: Beibehalten von Daten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: 21c162ca-2845-4dd8-a49d-e715aba8c461
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b89f05822ee23f5ad62c627b8bc6d67ebe401a2e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63130210"
---
# <a name="persisting-data"></a>Beibehalten von Daten
Tragbare Computer (z. B. mit Laptops) hat die Notwendigkeit für Anwendungen erstellt werden, die in einem verbundenen sowie im getrennten Zustand ausgeführt werden kann. ADO wurde Unterstützung für dieses hinzugefügt, indem dem Entwickler die Möglichkeit zum Speichern eines Clientcursors **Recordset** auf dem Datenträger, und Laden Sie es später erneut.  
  
 Es gibt mehrere Szenarien, in denen Sie diese Art von Funktion, einschließlich der folgenden verwenden können:  
  
-   **Unterwegs:** Wenn die Anwendung auf Reisen nehmen zu können, ist es wichtig, geben Sie die Möglichkeit, um Änderungen vorzunehmen, und fügen Sie neue Datensätze, die weiter unten in der Datenbank wiederhergestellt und ein Commit ausgeführt werden können.  
  
-   **Selten aktualisiert Suchvorgänge an:** Häufig in einer Anwendung Tabellen dienen als Suchvorgänge – z. B. Steuertabellen. Sie werden nur selten aktualisiert und sind schreibgeschützt. Anstelle von erneutes Lesen dieser Daten vom Server jedes Mal, die die Anwendung wird gestartet, die Anwendung kann einfach Laden der Daten aus lokal gespeicherten **Recordset**.  
  
 In ADO, zum Speichern und Laden von **Recordsets**, verwenden Sie die **Recordset.Save** und **Recordset.Open(,,,adCmdFile)** Methoden für das ADO **Recordset**Objekt.  
  
 Können Sie die **Recordset speichern** Methode zum Beibehalten von Ihrem ADO **Recordset** in eine Datei auf einem Datenträger. (Sie können auch speichern eine **Recordset** auf ein ADO- **Stream** Objekt. **Stream** Objekte werden weiter unten in der Anleitung erläutert.) Später können Sie die **öffnen** Methode zum Öffnen der **Recordset** Wenn Sie bereit sind, verwenden Sie es. Standardmäßig speichert ADO die **Recordset** in das proprietäre Format von Microsoft Advanced Data TableGram (ADTG). Diese binäre Format angegeben ist, mit der **AdPersistADTG PersistFormatEnum** Wert. Alternativ können Sie auch zum Speichern Ihrer **Recordset** Out als XML stattdessen mit **AdPersistXML**. Weitere Informationen zum Speichern von Recordsets im XML-Format finden Sie unter [beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Die Syntax der **speichern** -Methode lautet wie folgt:  
  
```  
  
recordset.  
Save  
Destination, PersistFormat  
  
```  
  
 Beim ersten Sie speichern die **Recordset**, ist er optional an *Ziel*. Wenn Sie weglassen *Ziel*, eine neue Datei mit einem Namen, legen Sie auf den Wert der erstellt werden die [Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md) Eigenschaft der **Recordset**.  
  
 Lassen Sie *Ziel* beim anschließend Aufruf **speichern** nach dem ersten Speichern oder ein Laufzeitfehler auftritt. Wenn Sie anschließend einen Aufruf **speichern** mit einem neuen *Ziel*, **Recordset** auf das neue Ziel gespeichert wird. Allerdings werden das neue Ziel und das ursprüngliche Ziel sowohl geöffnet sein.  
  
 **Speichern** schließt nicht die **Recordset** oder *Ziel*, sodass Sie fortfahren können, um die Arbeit mit der **Recordset** und die neuesten Änderungen zu speichern. *Ziel* bleibt bestehen, bis die **Recordset** wird geschlossen, während dieses Zeitraums können andere Anwendungen lesen aber nicht hineinschreiben *Ziel*.  
  
 Aus Gründen der Sicherheit der **speichern** Methode lässt nur die Verwendung von niedrigen und benutzerdefinierte Einstellungen aus einem Skript, das von Microsoft Internet Explorer ausgeführt werden.  
  
 Wenn die **speichern** Methode wird aufgerufen, während eines asynchronen **Recordset** abzurufen, ausführen oder Aktualisieren der Vorgang wird ausgeführt, **speichern** wartet, bis der asynchrone Vorgang ist Führen Sie.  
  
 Datensätze gespeichert werden, beginnend mit der ersten Zeile der **Recordset**. Wenn die **speichern** -Methode abgeschlossen ist, wird die aktuelle Zeilenposition verschoben, in die erste Zeile des der **Recordset**.  
  
 Legen Sie für optimale Ergebnisse die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft **AdUseClient** mit **speichern**. Wenn Ihr Anbieter nicht alle Funktionen zum Speichern von unterstützt **Recordset** Objekten, die der Cursor-Dienst wird diese Funktionalität bereitstellen.  
  
 Wenn eine **Recordset** wird beibehalten, mit der **CursorLocation** -Eigenschaft auf festgelegt **AdUseServer**, die Updatefunktion für die **Recordset**ist beschränkt. In der Regel nur für einzelne Tabellen Updates, einfügungen und löschungen (je nach Anbieterfunktionen) sind. Die [Resync](../../../ado/reference/ado-api/resync-method.md) Methode ist auch in dieser Konfiguration nicht verfügbar.  
  
 Da die *Ziel* Parameter sind jedes Objekt, das die OLE DB unterstützt **IStream** -Schnittstelle, die Sie speichern einen **Recordset** direkt mit dem ASP  **Antwort** Objekt.  
  
 Im folgenden Beispiel die **speichern** und **öffnen** dienen zum Beibehalten einer **Recordset** und es später erneut öffnen:  
  
```  
'BeginPersist  
   conn.ConnectionString = _  
   "Provider=SQLOLEDB;Data Source=MySQLServer;" _  
      & "Integrated Security=SSPI;Initial Catalog=pubs"  
   conn.Open  
  
   conn.Execute "create table testtable (dbkey int " & _  
      "primary key, field1 char(10))"  
   conn.Execute "insert into testtable values (1, 'string1')"  
  
   Set rst.ActiveConnection = conn  
   rst.CursorLocation = adUseClient  
  
   rst.Open "select * from testtable", conn, adOpenStatic, _  
      adLockBatchOptimistic  
  
   'Change the row on the client  
   rst!field1 = "NewValue"  
  
   'Save to a file--the .dat extension is an example; choose  
   'your own extension. The changes will be saved in the file  
   'as well as the original data.  
   MyFile = Dir("c:\temp\temptbl.dat")  
   If MyFile <> "" Then  
       Kill "c:\temp\temptbl.dat"  
   End If  
  
   rst.Save "c:\temp\temptbl.dat", adPersistADTG  
   Set rst = Nothing  
  
   'Now reload the data from the file  
   Set rst = New ADODB.Recordset  
   rst.Open "c:\temp\temptbl.dat", , adOpenStatic, _  
      adLockBatchOptimistic, adCmdFile  
  
   Debug.Print "After Loading the file from disk"  
   Debug.Print "   Current Edited Value: " & rst!field1.Value  
   Debug.Print "   Value Before Editing: " & rst!field1.OriginalValue  
  
   'Note that you can reconnect to a connection and  
   'submit the changes to the data source  
   Set rst.ActiveConnection = conn  
   rst.UpdateBatch  
'EndPersist  
```  
  
## <a name="remarks"></a>Hinweise  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Weitere Informationen zur Recordset-Beibehaltung](../../../ado/guide/data/more-about-recordset-persistence.md)  
  
-   [Beibehalten von gefilterten und hierarchischen Recordsets](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md)  
  
-   [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
