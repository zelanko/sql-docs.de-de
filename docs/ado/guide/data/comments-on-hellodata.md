---
title: Kommentare zu HelloData | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hellodata sample application [ADO]
ms.assetid: a2831d77-7040-4b73-bbae-fe0bf78107ed
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2c4897f82ff8562c031ec3522f47cddebfb56eb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925808"
---
# <a name="comments-on-hellodata"></a>Kommentare zur HelloData
Die HelloData-Anwendung durchläuft die grundlegenden Vorgänge einer typischen ADO-Anwendung: das erhalten, untersuchen, bearbeiten und Aktualisieren von Daten. Wenn Sie die Anwendung starten, klicken Sie auf die erste Schaltfläche, **Daten erhalten**. Dadurch wird die **GetData** -Unterroutine ausgeführt.  
  
## <a name="getdata"></a>GetData  
 **GetData** platziert eine gültige Verbindungs Zeichenfolge in eine Variable auf Modulebene, *m_sConnStr*. Weitere Informationen zu Verbindungs Zeichenfolgen finden Sie unter [Erstellen der Verbindungs Zeichenfolge](../../../ado/guide/data/creating-a-connection-string.md).  
  
 Weisen Sie mithilfe einer Visual Basic **OnError** -Anweisung einen Fehlerhandler zu. Weitere Informationen zur Fehlerbehandlung in ADO finden Sie unter [Fehlerbehandlung](../../../ado/guide/data/error-handling.md). Ein neues **Verbindungs** Objekt wird erstellt, und die **Cursor Location** -Eigenschaft wird auf **adUseClient** festgelegt, da im HelloData-Beispiel ein nicht *verbundenes Recordset*erstellt wird. Dies bedeutet, dass nach dem Abrufen der Daten aus der Datenquelle die physische Verbindung mit der Datenquelle getrennt ist, Sie aber weiterhin mit den Daten arbeiten können, die lokal in Ihrem **Recordset** -Objekt zwischengespeichert werden.  
  
 Nachdem die Verbindung geöffnet wurde, weisen Sie einer Variablen (SSQL) eine SQL-Zeichenfolge zu. Erstellen Sie dann eine Instanz eines neuen **Recordset** -Objekts `m_oRecordset1`. Öffnen Sie in der nächsten Codezeile das **Recordset** über die vorhandene **Verbindung**, und übergeben Sie `sSQL` als Quelle des **Recordsets**. Sie helfen ADO bei der Bestimmung, dass die als Quelle für das **Recordset** übergebene SQL-Zeichenfolge eine Text Definition eines Befehls ist, indem Sie **adCmdText** im Final-Argument an die **Recordset Open** -Methode übergibt. Diese Zeile legt auch den **LockType** und den **Cursor Type** fest, der dem **Recordset**zugeordnet ist.  
  
 In der nächsten Codezeile wird die Eigenschaft " **MarshalOptions** " auf " **adMarshalModifiedOnly**" festgelegt. **MarshalOptions** gibt an, welche Datensätze an die mittlere Ebene (oder den Webserver) gemarshallt werden sollen. Weitere Informationen zum Marshalling finden Sie in der com-Dokumentation. Wenn Sie **adMarshalModifiedOnly** mit einem Client seitigen Cursor ([CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) = **adUseClient**) verwenden, werden nur Datensätze, die auf dem Client geändert wurden, zurück in die mittlere Ebene geschrieben. Das Festlegen von **MarshalOptions** auf **adMarshalModifiedOnly** kann die Leistung verbessern, da weniger Zeilen gemarshallt werden.  
  
 Trennen Sie als nächstes das **Recordset** , indem Sie die zugehörige **ActiveConnection** -Eigenschaft auf " **Nothing**" festlegen. Weitere Informationen finden Sie im Abschnitt "Trennen der Verbindung und erneutes Verbinden des Recordsets" in [aktualisieren und](../../../ado/guide/data/updating-and-persisting-data.md)beibehalten von Daten.  
  
 Schließen Sie die Verbindung mit der Datenquelle, und zerstören Sie das vorhandene **Verbindungs** Objekt. Dadurch werden die verwendeten Ressourcen freigegeben.  
  
 Der letzte Schritt besteht darin, das **Recordset** als **Daten** Quelle für das Microsoft DataGrid-Steuerelement auf dem Formular festzulegen, damit Sie die Daten auf einfache Weise aus dem **Recordset** im Formular anzeigen können.  
  
 Klicken Sie auf die zweite Schaltfläche, unter **Suchen Sie Daten** Dadurch wird die Untersuchungs **Daten** -Unterroutine ausgeführt.  
  
## <a name="examinedata"></a>ExamineData  
 ExamineData verwendet verschiedene Methoden und Eigenschaften des **Recordset** -Objekts, um Informationen zu den Daten im **Recordset**anzuzeigen. Er meldet die Anzahl der Datensätze mithilfe der **RecordCount** -Eigenschaft. Sie durchläuft das **Recordset** und druckt den Wert der **AbsolutePosition** -Eigenschaft im Anzeige Textfeld des Formulars. Außerdem wird der Wert der **Bookmark** -Eigenschaft für den dritten Datensatz für die spätere Verwendung in eine Variant-Variable, *vBookmark*, eingefügt.  
  
 Die Routine navigiert mithilfe der zuvor gespeicherten Lesezeichen Variable direkt zurück zum dritten Datensatz. Die-Routine ruft die **walkfields** -Unterroutine auf, die durch die **Fields** -Auflistung des **Recordsets** durchläuft und Details zu jedem **Feld** in der Auflistung anzeigt.  
  
 Und schließlich verwendet **ExamineData** die **Filter** -Eigenschaft des **Recordsets** , um nur für die Datensätze mit einem **CategoryID** gleich 2 anzuzeigen. Das Ergebnis der Anwendung dieses Filters ist im Anzeige Raster auf dem Formular sofort sichtbar.  
  
 Weitere Informationen zu den Funktionen, die in der Unterroutine " **ExamineData** " angezeigt werden, finden Sie unter unter [Suchen von Daten](../../../ado/guide/data/examining-data.md).  
  
 Klicken Sie anschließend auf die dritte Schaltfläche, und bearbeiten Sie die **Daten**. Dadurch wird die **EditData** -Unterroutine ausgeführt.  
  
## <a name="editdata"></a>EditData  
 Wenn der Code in die **EditData** -Unterroutine eintritt, wird das **Recordset** nach wie **vor mit 2** gefiltert, sodass nur die Elemente sichtbar sind, die den Filterkriterien entsprechen. Sie durchläuft zuerst das **Recordset** und erhöht den Preis für jedes sichtbare Element im **Recordset** um 10 Prozent. Der Wert des Felds **Price** wird geändert, indem die **value** -Eigenschaft für dieses Feld auf einen neuen, gültigen Betrag festgelegt wird.  
  
 Beachten Sie, dass das **Recordset** von der Datenquelle getrennt ist. Die Änderungen, die in **EditData** vorgenommen wurden, werden nur an der lokal zwischengespeicherten Kopie der Daten vorgenommen. Weitere Informationen finden Sie unter [Bearbeiten von Daten](../../../ado/guide/data/editing-data.md).  
  
 Die Änderungen werden erst in der Datenquelle vorgenommen, wenn Sie auf die vierte Schaltfläche, **Aktualisieren von Daten**, klicken. Dadurch wird die **UpdateData** -Unterroutine ausgeführt.  
  
## <a name="updatedata"></a>UpdateData  
 UpdateData entfernt zuerst den Filter, der auf das **Recordset**angewendet wurde. Der Code entfernt und setzt `m_oRecordset1` als **Daten** Quelle für das von Microsoft gebundene DataGrid auf dem Formular zurück, sodass das ungefilterte **Recordset** im Raster angezeigt wird.  
  
 Der Code prüft dann, ob Sie im **Recordset** rückwärts wechseln können, indem Sie die **unterstützte** Methode mit dem **admoveprevious** -Argument verwenden.  
  
 Die Routine wechselt zum ersten Datensatz mithilfe der Methode " **muvefirst** " und zeigt die ursprünglichen und aktuellen Werte des Felds an, indem die **OriginalValue** -Eigenschaft und die **value** -Eigenschaft des **Field** -Objekts verwendet werden. Diese Eigenschaften werden in Verbindung mit der **UnderlyingValue** -Eigenschaft (hier nicht verwendet) in [aktualisieren und](../../../ado/guide/data/updating-and-persisting-data.md)beibehalten von Daten erläutert.  
  
 Im nächsten Schritt wird ein neues **Verbindungs** Objekt erstellt und verwendet, um eine Verbindung mit der Datenquelle wiederherzustellen. Sie verbinden das **Recordset** erneut mit der Datenquelle, indem Sie die neue **Verbindung** als **ActiveConnection** für das **Recordset**festlegen. Um die Updates an den Server zu senden, ruft der Code **UpdateBatch** für das **Recordset**auf.  
  
 Wenn das Batch Update erfolgreich ist, wird die Flag-Variable `m_flgPriceUpdated`auf Modulebene auf true festgelegt. Dadurch werden Sie später daran erinnert, alle Änderungen zu bereinigen, die an der Datenbank vorgenommen wurden.  
  
 Schließlich wechselt der Code zurück zum ersten Datensatz im **Recordset** und zeigt die ursprünglichen und aktuellen Werte an. Die Werte sind nach dem Aufrufen von **UpdateBatch**identisch.  
  
 Ausführliche Informationen zum Aktualisieren von Daten, einschließlich der Vorgehensweise beim Ändern von Daten auf dem Server, während das **Recordset** getrennt wird, finden Sie unter [aktualisieren und](../../../ado/guide/data/updating-and-persisting-data.md)beibehalten von Daten.  
  
## <a name="form_unload"></a>Form_Unload  
 Die **Form_Unload** Unterroutine ist aus verschiedenen Gründen wichtig. Erstens: da es sich hierbei um eine Beispielanwendung handelt, werden die Änderungen, die vor dem Beenden der Anwendung an der Datenbank vorgenommen wurden, Form_Unload bereinigt. Zweitens zeigt der Code, wie ein Befehl direkt aus einem geöffneten **Verbindungs** Objekt mithilfe der **Execute** -Methode ausgeführt werden kann. Schließlich wird ein Beispiel für die Ausführung einer Abfrage, die keine Zeilen Rückgabe ist, (eine Update-Abfrage) für die Datenquelle angezeigt.
