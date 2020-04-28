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
ms.openlocfilehash: 63323fd8ed18f57a68633dce0525d1d37e4978ae
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924708"
---
# <a name="persisting-data"></a>Beibehalten von Daten
Portable Computing (z. b. die Verwendung von Laptops) hat den Bedarf an Anwendungen generiert, die sowohl in einem verbundenen als auch in einem getrennten Zustand ausgeführt werden können. ADO bietet zusätzliche Unterstützung, da der Entwickler die Möglichkeit hat, ein Client Cursor- **Recordset** auf einem Datenträger zu speichern und später neu zu laden.  
  
 Es gibt mehrere Szenarien, in denen Sie diese Art von Feature verwenden können, einschließlich der folgenden:  
  
-   **Unterwegs:** Wenn Sie die Anwendung auf dem Weg nehmen, ist es wichtig, dass Sie die Möglichkeit bereitstellen, Änderungen vorzunehmen und neue Datensätze hinzuzufügen, die dann später wieder mit der Datenbank verbunden und committet werden können.  
  
-   **Selten aktualisierte Suchvorgänge:** Häufig werden Tabellen in einer Anwendung als Suchvorgänge verwendet, z. b. Zustands Steuertabellen. Sie werden nur selten aktualisiert und sind schreibgeschützt. Anstatt diese Daten bei jedem Start der Anwendung vom Server erneut zu lesen, kann die Anwendung die Daten einfach aus einem lokal beibehaltenen **Recordset**laden.  
  
 Verwenden Sie zum Speichern und Laden von **Recordsets**in ADO die Methoden **Recordset. Save** und **Recordset. Open (,,,, adcmdfile)** für das ADO- **Recordset** -Objekt.  
  
 Mit der **Recordset** -Methode Save können Sie das ADO- **Recordset** in einer Datei auf einem Datenträger speichern. (Sie können auch ein **Recordset** in einem ADO- **Streamobjekt** speichern. **Stream** -Objekte werden später in diesem Handbuch erläutert.) Später können Sie die **Open** -Methode verwenden, um das **Recordset** erneut zu öffnen, wenn Sie zur Verwendung bereit sind. Standardmäßig speichert ADO das **Recordset** im proprietären Microsoft-Format für erweiterte Daten tablegrams (ADTG). Dieses Binärformat wird mit dem Wert **adPersistADTG PersistFormatEnum** angegeben. Alternativ dazu können Sie auch auswählen, dass Sie das **Recordset** als XML speichern möchten, indem Sie stattdessen **adpersistxml**verwenden. Weitere Informationen zum Speichern von Recordsets als XML finden Sie unter [persistente Datensätze im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Die Syntax der **Save** -Methode lautet wie folgt:  
  
```  
  
recordset.  
Save  
Destination, PersistFormat  
  
```  
  
 Wenn Sie das **Recordset**zum ersten Mal speichern, ist es optional, das *Ziel*anzugeben. Wenn Sie das *Ziel*weglassen, wird eine neue Datei mit einem Namen erstellt, der auf den Wert der [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) -Eigenschaft des **Recordsets**festgelegt ist.  
  
 Wenn Sie den **Vorgang nach dem ersten Speichern oder** einem Laufzeitfehler ausführen, lassen Sie das *Ziel* aus. Wenn Sie anschließend **Speichern** mit einem neuen *Ziel*aufzurufen, wird das **Recordset** im neuen Ziel gespeichert. Allerdings sind das neue Ziel und das ursprüngliche Ziel beide geöffnet.  
  
 Durch **Speichern** wird das **Recordset** oder das *Ziel*nicht geschlossen, sodass Sie weiterhin mit dem **Recordset** arbeiten und die neuesten Änderungen speichern können. Das *Ziel* bleibt geöffnet, bis das **Recordset** geschlossen ist. während dieser Zeit können andere Anwendungen lesen, aber nicht in das *Ziel*schreiben.  
  
 Aus Sicherheitsgründen ermöglicht die **Save** -Methode nur die Verwendung von niedrigen und benutzerdefinierten Sicherheitseinstellungen aus einem Skript, das von Microsoft Internet Explorer ausgeführt wird.  
  
 Wenn die **Save** -Methode während des asynchronen **Recordsets** zum Abrufen, ausführen oder Aktualisieren aufgerufen wird, wird die Wartezeit bis zum Abschluss des asynchronen Vorgangs **gespeichert** .  
  
 Datensätze werden ab der ersten Zeile des **Recordsets**gespeichert. Wenn die **Save** -Methode abgeschlossen ist, wird die aktuelle Zeilen Position in die erste Zeile des **Recordsets**verschoben.  
  
 Um optimale Ergebnisse zu erzielen, legen Sie die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft mit **Save**auf **adUseClient** fest. Wenn Ihr Anbieter nicht alle Funktionen unterstützt, die zum Speichern von **Recordset** -Objekten erforderlich sind, stellt der Cursor Dienst diese Funktionalität bereit.  
  
 Wenn ein **Recordset** persistent ist und die Eigenschaft **Cursor Location** auf **adeeserver**festgelegt ist, ist die Aktualisierungs Funktion für das **Recordset** eingeschränkt. In der Regel sind nur Aktualisierungen der einzelnen Tabelle, Einfügungen und Löschungen zulässig (abhängig von der Anbieter Funktionalität). Die [Resync](../../../ado/reference/ado-api/resync-method.md) -Methode ist in dieser Konfiguration ebenfalls nicht verfügbar.  
  
 Da der *Destination* -Parameter jedes Objekt akzeptieren kann, das die OLE DB **IStream** -Schnittstelle unterstützt, können Sie ein **Recordset** direkt im ASP- **Antwort** Objekt speichern.  
  
 Im folgenden Beispiel werden die **Save** -Methode und die **Open** -Methode verwendet, um ein **Recordset** beizubehalten und später erneut zu öffnen:  
  
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
  
## <a name="remarks"></a>Bemerkungen  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Weitere Informationen zur Beibehaltung von Recordsets](../../../ado/guide/data/more-about-recordset-persistence.md)  
  
-   [Beibehalten von gefilterten und hierarchischen Recordsets](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md)  
  
-   [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
