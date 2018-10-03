---
title: Kommentare zur HelloData | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: e3086eff0e4a774e7f63e7ff876a9675668d5912
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707878"
---
# <a name="comments-on-hellodata"></a>Kommentare zur HelloData
Die Anwendung für die HelloData erläutert die grundlegenden Vorgänge einer typischen ADO-Anwendung: Abrufen, untersuchen, bearbeiten und Aktualisieren von Daten. Wenn Sie die Anwendung starten, klicken Sie auf die erste Schaltfläche **Datenabruf**. Dies führt die **GetData** Unterroutine.  
  
## <a name="getdata"></a>GetData  
 **GetData** wird von einer gültigen Verbindungszeichenfolge in einer Variablen auf Modulebene *M_sConnStr*. Weitere Informationen zu Verbindungszeichenfolgen finden Sie unter [Erstellen der Verbindungszeichenfolge](../../../ado/guide/data/creating-a-connection-string.md).  
  
 Zuweisen ein fehlerhandlers, der mit einem Visual Basic **OnError** Anweisung. Weitere Informationen zur Fehlerbehandlung in ADO finden Sie unter [Fehlerbehandlung](../../../ado/guide/data/error-handling.md). Ein neues **Verbindung** -Objekt wird erstellt, und die **CursorLocation** -Eigenschaftensatz auf **AdUseClient** daran, dass die HelloData-Beispiel erstellt eine  *getrenntes Recordset*. Dies bedeutet, dass, sobald die Daten aus der Datenquelle abgerufen wurden, die physische Verbindung mit der Datenquelle unterbrochen ist, aber Sie können weiterhin mit den Daten, die lokal im zwischengespeichert werden arbeiten Ihre **Recordset** Objekt.  
  
 Nachdem die Verbindung geöffnet wurde, weisen Sie eine SQL-Zeichenfolge in eine Variable (SQL). Erstellen Sie dann eine Instanz eines neuen **Recordset** Objekt `m_oRecordset1`. Öffnen Sie in der nächsten Zeile des Codes der **Recordset** über die vorhandene **Verbindung**, und übergeben Sie `sSQL` als Quelle für die **Recordset**. Sie tragen Sie zu ADO die Feststellung, dass Sie die SQL-Zeichenfolge übergeben haben, als Quelle für die **Recordset** Textdefinition einen Befehl übergeben wird **AdCmdText** in das endgültige Argument für die **Recordset als offen** Methode. Diese Zeile legt auch fest. die **LockType** und **CursorType** zugeordneten der **Recordset**.  
  
 Die nächste Zeile der Code legt die **MarshalOptions** -Eigenschaft **AdMarshalModifiedOnly**. **MarshalOptions** gibt an, welche Datensätze auf der mittleren Ebene (oder einen Webserver) gemarshallt werden sollen. Weitere Informationen zu marshallen finden Sie unter der COM-Dokumentation. Bei Verwendung von **AdMarshalModifiedOnly** mit einem clientseitigen Cursor ([CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) = **AdUseClient**), nur Datensätze, die auf geändert wurden die Clients werden zurück an die mittlere Ebene geschrieben. Festlegen von **MarshalOptions** zu **AdMarshalModifiedOnly** kann die Leistung verbessern, da weniger Zeilen gemarshallt werden.  
  
 Trennen Sie die **Recordset** durch Festlegen seiner **ActiveConnection** -Eigenschaft **nichts**. Weitere Informationen finden Sie im Abschnitt "Trennen und Wiederherstellen der Verbindung das Recordset" in [wird aktualisiert und Beibehalten von Daten](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Schließen Sie die Verbindung mit der Datenquelle, und Löschen der vorhandenen **Verbindung** Objekt. Damit werden die Ressourcen, die sie verwendet.  
  
 Der letzte Schritt ist, legen Sie die **Recordset** als die **DataSource** für das Datenraster Microsoft Steuern für das Formular also, können Sie ganz einfach zeigen, auf die Daten aus der **Recordset** auf der Formular.  
  
 Klicken Sie auf die zweite Schaltfläche **Daten prüfen**. Dadurch wird ausgeführt, die **ExamineData** Unterroutine.  
  
## <a name="examinedata"></a>ExamineData  
 ExamineData verwendet wird, verschiedene Methoden und Eigenschaften der **Recordset** Objekt zum Anzeigen von Informationen zu den Daten in die **Recordset**. Es meldet die Anzahl der Datensätze mithilfe der **RecordCount** Eigenschaft. Es durchläuft die **Recordset** und gibt den Wert des der **AbsolutePosition** -Eigenschaft in das Textfeld angezeigt, auf dem Formular. Während Sie sich auch in der Schleife wird der Wert des der **Lesezeichen** -Eigenschaft für den dritten Datensatz befindet sich in einer Variablen vom Typ variant *vBookmark*, für die spätere Verwendung.  
  
 Die Routine navigiert direkt an der dritte Datensatz mit der Lesezeichen-Variable, die sie zuvor gespeichert. Die Routine Ruft die **WalkFields** -Unterroutine, die Schleife durchläuft die **Felder** Auflistung von der **Recordset** und zeigt Details zu den einzelnen **Feld**  in der Auflistung.  
  
 Schließlich **ExamineData** verwendet die **Filter** Eigenschaft der **Recordset** zum Bildschirm für die nur die Datensätze mit einem **CategoryId** gleich 2. Das Ergebnis dieses Filters ist sofort sichtbar, in das Raster auf das Formular anzeigen.  
  
 Weitere Informationen zu den Funktionen dargestellt, der **ExamineData** Unterroutine, finden Sie unter [Untersuchen von Daten](../../../ado/guide/data/examining-data.md).  
  
 Klicken Sie dann auf die dritte Schaltfläche **Daten bearbeiten**. Dies führt die **EditData** Unterroutine.  
  
## <a name="editdata"></a>EditData  
 Wenn der Code gibt die **EditData** Unterroutine, die **Recordset** weiterhin gefiltert **CategoryId** gleich 2, sodass nur die Elemente, die den Filterkriterien entsprechen sichtbar. Durchläuft es zuerst die **Recordset** und erhöht sich der Preis der einzelnen Elemente angezeigt, in der **Recordset** um 10 Prozent. Der Wert des der **Preis** Feld geändert wird, durch Festlegen der **Wert** -Eigenschaft für dieses Feld auf eine neue, gültige Menge gleich.  
  
 Beachten Sie, dass die **Recordset** nicht mit der Datenquelle verbunden ist. Die vorgenommenen Änderungen wurden **EditData** nur an der lokal zwischengespeicherte Kopie der Daten vorgenommen werden. Weitere Informationen finden Sie unter [Bearbeiten von Daten](../../../ado/guide/data/editing-data.md).  
  
 Die Änderungen werden in der Datenquelle nicht durchgeführt werden, bis Sie die vierte Schaltfläche, klicken Sie auf **Aktualisierungsdaten**. Dies führt die **UpdateData** Unterroutine.  
  
## <a name="updatedata"></a>UpdateData  
 UpdateData entfernt zuerst den Filter, die angewendet wurde die **Recordset**. Der Code entfernt, und setzt `m_oRecordset1` als die **DataSource** für das Microsoft gebunden DataGrid-Steuerelement im Formular, damit die ungefilterte **Recordset** werden im Raster angezeigt.  
  
 Der Code prüft dann, um festzustellen, ob Sie nach hinten, in verschieben können der **Recordset** mithilfe der **unterstützt** -Methode mit der **AdMovePrevious** Argument.  
  
 Die Routine verschoben wird, mit dem ersten Datensatz der **MoveFirst** Methode und zeigt der ursprünglichen und aktuellen Werte des Felds unter Verwendung der **OriginalValue** und **Wert** Eigenschaften der **Feld** Objekt. Diese Eigenschaften zusammen mit den **UnderlyingValue** Eigenschaft (hier nicht verwendet), finden Sie im [wird aktualisiert und Beibehalten von Daten](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Anschließend wird eine neue **Verbindung** Objekt erstellt und verwendet, um eine Verbindung mit der Datenquelle wiederhergestellt. Sie verbinden die **Recordset** an die Datenquelle durch Festlegen der neuen **Verbindung** als die **ActiveConnection** für die **Recordset**. Zum Senden von Updates auf dem Server, der Code ruft **UpdateBatch** auf die **Recordset**.  
  
 Wenn die Batchaktualisierung eine Variablen auf Modulebene Flag erfolgreich ist, `m_flgPriceUpdated`, auf "true" festgelegt ist. Dies erinnert Sie später auf, um alle Änderungen zu bereinigen, die in der Datenbank vorgenommen wurden.  
  
 Zum Schluss der Code wechselt zurück zum ersten Datensatz in die **Recordset** und zeigt die ursprünglichen und aktuellen Werte. Die Werte identisch sind, nach dem Aufruf von **UpdateBatch**.  
  
 Um ausführliche Informationen zum Aktualisieren von Daten, einschließlich der Vorgehensweise, wenn Daten auf Änderungen an den Server während Ihrer **Recordset** ist getrennt, finden Sie [wird aktualisiert und Beibehalten von Daten](../../../ado/guide/data/updating-and-persisting-data.md).  
  
## <a name="formunload"></a>Form_Unload  
 Die **Form_Unload** Unterroutine ist wichtig, verschiedene Ursachen haben. Da dies eine Beispiel-App ist, löscht Form_Unload zuerst um die Änderungen, die in der Datenbank vor dem Beenden der Anwendung vorgenommen wurden. Zweitens: der Code zeigt, wie ein Befehl direkt über ein offenes ausgeführt werden kann **Verbindung** -Objekt unter Verwendung der **Execute** Methode. Abschließend wird ein Beispiel der Ausführung einer Abfrage nicht Zeile zurückgibt (eine UPDATE-Abfrage), für die Datenquelle.
