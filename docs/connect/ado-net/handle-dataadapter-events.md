---
title: Verarbeiten von DataAdapter-Ereignissen
description: In diesem Artikel werden DataAdapter-Ereignisse und deren Verwendung beschrieben.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 003a8e77ad80f83c210ffb565ce4fac5c93c2166
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772221"
---
# <a name="handle-dataadapter-events"></a>Verarbeiten von DataAdapter-Ereignissen

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Der Microsoft SqlClient-Datenanbieter für SQL Server (<xref:Microsoft.Data.SqlClient.SqlDataAdapter>) verfügt über drei Ereignisse, die Sie verwenden können, um auf Änderungen zu reagieren, die an Daten in der Datenquelle vorgenommen wurden. In der folgenden Tabelle finden Sie eine Beschreibung dieser `DataAdapter`-Ereignisse.

|Ereignis|BESCHREIBUNG|  
|-----------|-----------------|  
|`RowUpdating`|Es wird gerade ein Aktualisierungs-, Einfüge- oder Löschvorgang für eine Zeile eingeleitet (durch Aufrufen einer der `Update`-Methoden).|  
|`RowUpdated`|Ein Update-, Einfüge- oder Löschvorgang für eine Zeile ist abgeschlossen (durch Aufrufen einer der `Update`-Methoden).|  
|`FillError`|Während eines `Fill`-Vorgangs ist ein Fehler aufgetreten.|  

## <a name="rowupdating-and-rowupdated-events"></a>RowUpdating- und RowUpdated-Ereignisse

`RowUpdating` wird ausgelöst, bevor ein Update einer Zeile des <xref:System.Data.DataSet>-Objekts in der Datenquelle verarbeitet wurde. `RowUpdated` wird ausgelöst, nachdem ein Update einer Zeile des `DataSet`-Objekts in der Datenquelle verarbeitet wurde. Folglich können Sie mit dem `RowUpdating`-Ereignis das Verhalten von Updates ändern, bevor sie vorgenommen werden, zusätzliche Behandlungsoptionen beim Auftreten eines Updates anbieten, einen Verweis auf eine aktualisierte Zeile beibehalten, das aktuelle Update abbrechen und es für die spätere Verarbeitung in einem Stapelverarbeitungsprozess einplanen usw. `RowUpdated` ist hilfreich bei der Reaktion auf Fehler und Ausnahmen, die während des Updates auftreten. Sie können der `DataSet`-Klasse unter anderem **Fehlerinformationen** und **Wiederholungslogik** hinzufügen.

Die Argumente <xref:System.Data.Common.RowUpdatingEventArgs> und <xref:System.Data.Common.RowUpdatedEventArgs>, die an die Ereignisse `RowUpdating` und `RowUpdated` übergeben werden, enthalten Folgendes: eine `Command`-Eigenschaft, die auf das `Command`-Objekt verweist, das zur Ausführung des Updates verwendet wird, eine `Row`-Eigenschaft, die auf das `DataRow`-Objekt verweist, dass die aktualisierten Informationen enthält, eine `StatementType`-Eigenschaft zur Angabe der auszuführenden Updatestypen, die `TableMapping`, sofern zutreffend, und den `Status` des Vorgangs.

Mit der `Status`-Eigenschaft können Sie ermitteln, ob während des Vorgangs ein Fehler aufgetreten ist, und gegebenenfalls die Aktionen für die aktuellen und die resultierenden Zeilen steuern. Wenn das Ereignis eintritt, entspricht die `Status`-Eigenschaft entweder `Continue` oder `ErrorsOccurred`. In der folgenden Tabelle sind die Werte dargestellt, die Sie für die `Status`-Eigenschaft festlegen können, um nachfolgende Aktionen während des Updates zu steuern.

|Status|BESCHREIBUNG|  
|------------|-----------------|  
|`Continue`|Setzt den Aktualisierungsvorgang fort.|  
|`ErrorsOccurred`|Bricht den Updatevorgang ab und löst eine Ausnahme aus.|  
|`SkipCurrentRow`|Ignoriert die aktuelle Zeile und setzt den Aktualisierungsvorgang fort.|  
|`SkipAllRemainingRows`|Bricht den Aktualisierungsvorgang ab, löst jedoch keine Ausnahme aus.|  

Durch das Festlegen der `Status`-Eigenschaft auf `ErrorsOccurred` wird eine Ausnahme ausgelöst. Welche Ausnahme ausgelöst wird, können Sie steuern, indem Sie für die `Errors`-Eigenschaft die gewünschte Ausnahme angeben. Wenn Sie einen der anderen Werte für `Status` verwenden, wird keine Ausnahme ausgelöst.

Sie können auch die `ContinueUpdateOnError`-Eigenschaft verwenden, um Fehler für aktualisierte Zeilen zu behandeln. Wenn für `DataAdapter.ContinueUpdateOnError` der Wert `true` angegeben ist und das Updates einer Zeile eine Ausnahme auslöst, wird der Text der Ausnahme in die `RowError`-Information der entsprechenden Zeile aufgenommen. Die Verarbeitung wird fortgesetzt, ohne dass eine Ausnahme ausgelöst wird. Auf diese Weise können Sie auf Fehler reagieren, wenn `Update` abgeschlossen wurde. Dagegen können Sie beim `RowUpdated`-Ereignis auf den Fehler reagieren, sobald er festgestellt wird.

Im folgenden Codebeispiel wird dargestellt, wie Ereignishandler hinzugefügt und entfernt werden. Der `RowUpdating`-Ereignishandler schreibt ein Protokoll aller gelöschten Datensätze und versieht die Löschvorgangaufzeichnungen jeweils mit einem Timestamp. Der `RowUpdated`-Ereignishandler fügt der `RowError`-Eigenschaft der Zeile in der `DataSet`-Klasse Fehlerinformationen hinzu, unterdrückt die Ausnahme und setzt die Verarbeitung fort (entspricht dem Verhalten von `ContinueUpdateOnError` = `true`).

[!code-csharp[SqlDataAdapter_Events#1](~/../sqlclient/doc/samples/SqlDataAdapter_Events.cs#1)]

## <a name="fillerror-event"></a>FillError-Ereignis

Der `DataAdapter` gibt das `FillError`-Ereignis aus, wenn während des `Fill`-Vorgangs ein Fehler auftritt. Dieser Fehlertyp tritt häufig auf, wenn die Daten in der hinzugefügten Zeile nicht ohne Genauigkeitsverlust in einen .NET-Typ konvertiert werden konnten.

Wenn während eines `Fill`-Vorgangs ein Fehler auftritt, wird der `DataTable` die aktuelle Zeile nicht hinzugefügt. Mit dem `FillError`-Ereignis können Sie den Fehler auflösen und die Zeile hinzufügen oder die betreffende Zeile ignorieren und den `Fill`-Vorgang fortsetzen.

Die an das <xref:System.Data.FillErrorEventArgs>-Ereignis übergebenen `FillError` können mehrere Eigenschaften enthalten, mit denen Sie auf Fehler reagieren und diese auflösen können. In der folgenden Tabelle werden die Eigenschaften des `FillErrorEventArgs`-Objekts dargestellt.

|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|`Errors`|Die `Exception`, die aufgetreten ist.|  
|`DataTable`|Das `DataTable`-Objekt, das ausgefüllt wurde, als der Fehler auftrat.|  
|`Values`|Ein Array aus Objekten, das die Werte der beim Eintreten des Fehlers hinzugefügten Zeile enthält. Die Ordinalzahlverweise des `Values`-Arrays entsprechen den Ordinalzahlverweisen der Spalten der hinzugefügten Zeile. So ist z. B. `Values[0]` der Wert, der als erste Spalte der Zeile hinzugefügt wurde.|  
|`Continue`|Sie können festlegen, ob eine Ausnahme ausgelöst werden soll oder nicht. Durch das Festlegen der `Continue`-Eigenschaft auf `false` wird der aktuelle `Fill`-Vorgang angehalten, und es wird eine Ausnahme ausgelöst. Durch das Festlegen der `Continue`-Eigenschaft auf `true` wird der `Fill`-Vorgang trotz des Fehlers fortgesetzt.|  

Im folgenden Codebeispiel wird ein Ereignishandler für das `FillError`-Ereignis `DataAdapter` hinzugefügt. Im `FillError`-Ereigniscode bestimmt das Beispiel, ob die Möglichkeit von Präzisionsverlust besteht, und bietet die Chance, auf die Ausnahme zu reagieren.

[!code-csharp[SqlDataAdapter_Events#2](~/../sqlclient/doc/samples/SqlDataAdapter_Events.cs#2)]

## <a name="see-also"></a>Weitere Informationen

- ["DataAdapters" und "DataReaders"](dataadapters-datareaders.md)
- [Ereignisse](/dotnet/standard/events/index.md)
- [Microsoft ADO.NET für SQL Server](microsoft-ado-net-sql-server.md)
