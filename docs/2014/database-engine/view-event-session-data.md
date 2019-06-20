---
title: Anzeigen von Ereignissitzungsdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ac742a01-2a95-42c7-b65e-ad565020dc49
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e2fecf8a71854d7f8df160ba3ff63912086a34e5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "67131792"
---
# <a name="view-event-session-data"></a>Anzeigen von Ereignissitzungsdaten
  In diesem Thema wird beschrieben, wie Sie mithilfe der Anzeigebenutzeroberfläche erweiterte Ereignisdaten anzeigen und analysieren:  
  
-   Anzeigen von Zieldaten  
  
-   Arbeiten mit Daten  
  
## <a name="view-target-data"></a>Anzeigen von Zieldaten  
 Sie können die am angegebenen Ziel gesammelten Daten in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]anzeigen.  
  
### <a name="view-target-data"></a>Anzeigen von Zieldaten  
 So zeigen Sie Zieldaten an  
  
1.  Erweitern Sie im Objekt-Explorer **Verwaltung**, erweitern Sie **Erweiterte Ereignisse**, erweitern Sie **Sitzungen**und dann eine Sitzung.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Zielnamen, und klicken Sie dann auf **Zieldaten anzeigen** , um die Zieldaten anzuzeigen.  
  
     Das Zieldatenfenster wird auf der Standardansicht angezeigt und enthält die Zieldaten.  
  
 Hinweise zum Anzeigen von Zieldaten:  
  
-   Zieldaten sind für das ETW-Ziel nicht verfügbar.  
  
-   Um die ring_buffer-Daten im XML-Format anzuzeigen, klicken Sie im Zieldatenfenster auf den Link für die **ring_buffer-Zieldaten** . Die Datei ring_buffer.xml wird im XML-Editor angezeigt.  
  
-   Zeigen Sie für ein event_file-Ziel die Dateizieldaten (XEL-Datei) mithilfe einer der folgenden Methoden an:  
  
    -   Verwenden Sie eine Datei -> Öffnen in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].
    
    -   Ziehen und Ablegen die Datei in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. 
    
    -   Doppelklicken Sie auf die XEL-Datei.  
    
    -   Klicken Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf eine aktive Sitzung für erweiterte Ereignisse, und wählen Sie Zieldaten anzeigen aus. 
    
    -   [fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).
    
    -   Verwenden von Powershell-lesen-SQLXevent in [SQLServer.XEvent Modul](https://www.powershellgallery.com/packages/SqlServer.XEvent).
    
    -   Programmgesteuert mithilfe von XEvents nutzen die [XELite NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite).
    
    -   Sie können mehrere anzeigen. XEL-Datei dazu **Dateien für erweiterte Ereignisse zusammenführen** aus der Datei -> "Menü öffnen".

### <a name="watching-live-data"></a>Beobachten von Livedaten  
 Sie können Livedaten während der Erfassung anzeigen.  
  
-   Erweitern Sie im Objekt-Explorer die Knoten **Verwaltung**, **Erweiterte Ereignisse**und dann **Sitzungen** .  

-   Klicken Sie mit der rechten Maustaste auf den Sitzungsnamen, und klicken Sie dann auf **Livedaten ansehen** , um die Ablaufverfolgungsdaten anzuzeigen.  
  
     Die Standardanzeigespalten sind **Ereignisname** und **TimeStamp**.  
  
     Um dem Ablaufverfolgungsfenster zusätzliche Spalten hinzuzufügen, klicken Sie auf der Symbolleiste für erweiterte Ereignisse auf die Schaltfläche **Spalten auswählen** . Die Registerkarte **Details** zeigt alle Ereignisdetails für das ausgewählte Ereignis an.  
  
     Ereignisse werden normalerweise in ungefähr 30 Sekunden angezeigt. Um den Latenzzeitraum zu ändern, können Sie den Wert für **Maximale Verteilungslatenzzeit** auf der Seite **Erweitert** des Dialogfelds **Neue Sitzung** ändern.  
     
-    Live-Daten können gestreamt werden, indem die [SqlServer.XEvent-PowerShell-Modul](https://www.powershellgallery.com/packages/SqlServer.XEvent).
     
### <a name="to-refresh-target-data"></a>So aktualisieren Sie Zieldaten  
 Das Aktualisieren der Zieldaten wird für event_files-Ziele nicht unterstützt:  
  
1.  Um die Zieldaten automatisch zu aktualisieren, klicken Sie mit der rechten Maustaste auf die Zieldaten, wählen Sie die Option **Aktualisierungsintervall**und anschließend das Aktualisierungsintervall aus der Intervallliste aus.  
  
2.  Klicken Sie zum Anhalten oder Fortsetzen der automatischen Aktualisierung mit der rechten Maustaste auf die Zieldaten, und wählen Sie dann die Option **Anhalten** oder **Fortsetzen**aus.  
  
3.  Um die Zieldaten manuell zu aktualisieren, klicken Sie mit der rechten Maustaste auf die Zieldaten, und wählen Sie dann **Aktualisieren**aus.  
  
## <a name="working-with-data"></a>Arbeiten mit Daten  
 Sie können die Analysefunktionen der Benutzeroberfläche für erweiterte Ereignisse verwenden, um Probleme zu identifizieren.  
  
### <a name="details-pane"></a>Detailbereich  
 Der **Detailbereich** enthält alle Spalten für das ausgewählte Ereignis, einschließlich Feldern und Aktionen. Sie können der Zieldatentabelle eine Spalte hinzufügen, indem Sie mit der rechten Maustaste auf eine Zeile im Bereich **Details** klicken und **Spalte in Tabelle anzeigen**auswählen.  
  
### <a name="create-modify-or-delete-merged-columns"></a>Erstellen, Ändern oder Löschen zusammengeführter Spalten  
 In einer zusammengeführten Spalte können Sie einen Satz von Feldern kombinieren, der in einer einzelnen Spalte angezeigt werden soll. Die zusammengeführte Spalte enthält die Daten aus dem ersten Nicht-NULL-Feld, und zwar in der Reihenfolge, in der sie der Feldliste hinzugefügt wurden. Dies ist vergleichbar mit der Anzeige im [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler, in dem eine bestimmte Spalte je nach Ereignis verschiedene Daten enthalten kann (das häufigste Beispiel ist das TextData-Feld im [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler). Beispielsweise können Sie das statement-Feld und das batch_text-Feld aus dem sql_statement_completed-Ereignis bzw. dem sql_batch_completed-Ereignis im Feld myStatement zusammenführen. Wenn Sie die myStatement-Spalte in der Tabelle anzeigen, werden die entsprechenden Daten für das zugeordnete Ereignis angezeigt.  
  
 Sie können die zusammengeführten Spalten erstellen, ändern oder löschen:  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen. (Sie können auch mit der rechten Maustaste auf den Sitzungsnamen klicken und dann **Livedaten ansehen**auswählen.)  
  
2.  Klicken Sie im Fenster für die Ablaufverfolgungsergebnisse mit der rechten Maustaste auf den Spaltenheader, und klicken Sie dann auf **Spalten auswählen**.  
  
 Um eine zusammengeführte Spalte zu erstellen, klicken Sie im Dialogfeld **Spalten auswählen** auf **Neu** .  Geben Sie der zusammengeführten Spalte im Dialogfeld **Neue zusammengeführte Spalte** einen Namen, und wählen Sie die ursprünglichen Spalten aus, die in die zusammengeführte Spalte aufgenommen werden sollen.  
  
 Um eine zusammengeführte Spalte zu bearbeiten, wählen Sie im Dialogfeld **Spalten auswählen** eine zusammengeführte Spalte aus, und klicken Sie auf **Bearbeiten**. Benennen Sie die zusammengeführte Spalte im Dialogfeld **Zusammengeführte Spalte bearbeiten** um, oder ändern Sie die ursprünglichen Spalten, die in die zusammengeführte Spalte aufgenommen werden sollen.  
  
 Um eine zusammengeführte Spalte zu löschen, wählen Sie im Dialogfeld **Spalten auswählen** eine zusammengeführte Spalte aus, und klicken Sie auf **Löschen**.  
  
### <a name="filter-results"></a>Filtern von Ergebnissen  
 Sie können Ablaufverfolgungsergebnisse anzeigen und dann Filter anwenden, um die Ablaufverfolgungsergebnisse einzugrenzen, die im Ablaufverfolgungsfenster angezeigt werden. Der Anzeigefilter umfasst einen Zeitfilter und einen erweiterten Filter. Sie filtern mithilfe des Zeitfilters die Ablaufverfolgungsergebnisse nach Ereigniszeitstempel und erstellen mithilfe des erweiterten Filters Filterbedingungen mit Ereignisfeldern und -aktionen. Zwischen Zeit- und erweitertem Filter besteht eine Und-Beziehung.  
  
 So erstellen Sie einen Filter  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen. (Sie können auch mit der rechten Maustaste auf den Sitzungsnamen klicken und dann **Livedaten ansehen**auswählen.)  
  
2.  Wählen Sie im Fenster mit den Ablaufverfolgungsergebnissen die Ergebnisse aus, die Sie filtern möchten, und klicken Sie dann auf der Symbolleiste **Erweiterte Ereignisse** auf die Schaltfläche **Filter**.  
  
3.  Wählen Sie im Dialogfeld **Filter** zum Festlegen des Zeitfilters die Option **Zeitfilter festlegen** aus, und ziehen Sie die Schieberegler, oder ändern Sie die Zeit im Bearbeitungsfeld.  
  
4.  Wenden Sie im Abschnitt **Zusätzliche Filter** die Filterkriterien an, und klicken Sie dann auf **Anwenden**.  
  
### <a name="sort-results"></a>Sortieren von Ergebnissen  
 So sortieren Sie die Ergebnisse in aufsteigender oder absteigender Reihenfolge  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen. (Sie können auch mit der rechten Maustaste auf den Sitzungsnamen klicken, **Livedaten ansehen**auswählen und dann auf der Symbolleiste auf die Schaltfläche **Datenfeed beenden** klicken.)  
  
2.  Klicken Sie im Fenster für die Ablaufverfolgungsergebnisse mit der rechten Maustaste auf die Überschrift der Spalte, die Sie sortieren möchten, und klicken Sie auf **Aufsteigend sortieren** oder **Absteigend sortieren**.  
  
 Sie können auch auf die Spaltenüberschrift klicken, um die Sortierreihenfolge umzukehren.  
  
 Bei gruppierten Spalten werden bei Sortierung der Spalte nur die Daten innerhalb der Gruppe sortiert.  
  
### <a name="group-results"></a>Gruppieren von Ergebnissen  
 Gruppierte Ergebnisse entsprechen der Funktionalität der `GROUP BY`-Klausel in [!INCLUDE[tsql](../includes/tsql-md.md)]. Die Zieldatentabelle enthält die gruppierten Daten, die Sie erweitern und reduzieren können.  
  
 Vor dem Aggregieren müssen Sie die Daten gruppieren. Beispielsweise können Sie nach dem query_hash-Wert, in absteigender Folge nach Dauer, nach der durchschnittlichen Dauer jeder Gruppe und in absteigender Folge nach Aggregation sortieren.  Dadurch erhalten Sie eine Liste, in der die eindeutigen Anweisungen von der längsten bis zur kürzesten durchschnittlichen Dauer enthalten sind. Wenn Sie die oberste Gruppe erweitern, sehen Sie die einzelnen Ausführungen dieser bestimmten Abfrage von der längsten bis zur kürzesten sortiert.  
  
 Sie können Ergebnisse nach einer einzelnen Spalte oder mehreren Spalten gruppieren.  
  
 Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen. (Sie können auch mit der rechten Maustaste auf den Sitzungsnamen klicken, **Livedaten ansehen**auswählen und dann auf der Symbolleiste auf die Schaltfläche **Datenfeed beenden** klicken.)  
  
 Um Ergebnisse nach einer einzelnen Spalte zu gruppieren, klicken Sie mit der rechten Maustaste auf die Spaltenüberschrift im Fenster für die Ablaufverfolgungsergebnisse und klicken auf **Nach dieser Spalte gruppieren**. Um die Gruppierung rückgängig zu machen, wählen Sie eine der Zeilen aus, und klicken Sie auf **Alle Gruppierungen entfernen**.  
  
 Um Ergebnisse nach mehreren Spalten zu gruppieren, klicken Sie auf der Symbolleiste **Erweiterte Ereignisse** auf die Schaltfläche **Gruppierung** . Wählen Sie im Dialogfeld **Gruppierung** im Feld **Verfügbare Spalten** die Spalten aus, die Sie gruppieren möchten, und verschieben Sie sie in das Feld **Spalten gruppiert nach** . Um die Reihenfolge zu ändern, klicken Sie im Feld **Spalten gruppiert nach** auf den nach oben oder unten weisenden Pfeil.  
  
### <a name="aggregate-results"></a>Aggregieren der Ergebnisse  
 Sie können die Ablaufverfolgungsergebnisse anzeigen und dann die Ereignisdaten weiter analysieren, indem Sie Spalten in den Ergebnissen aggregieren. Erweiterte Ereignisse unterstützen fünf Aggregationsfunktionen:  
  
-   sum  
  
-   min  
  
-   max  
  
-   Durchschnitt  
  
-   count  
  
 Sum, Min, Max und Average können nur mit numerischen Spalten verwendet werden. Count ist die Anzahl von Werten ungleich NULL, die für die ausgewählte Spalte in der Gruppe vorhanden sind.  
  
 Die Aggregation wird für eine Gruppe ausgeführt, deshalb müssen Sie die Ergebnisse gruppieren, bevor Sie die Aggregation ausführen können. So aggregieren Sie Ergebnisse  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen. (Sie können auch mit der rechten Maustaste auf den Sitzungsnamen klicken, **Livedaten ansehen**auswählen und dann auf der Symbolleiste auf die Schaltfläche **Datenfeed beenden** klicken.)  
  
2.  Klicken Sie auf der Symbolleiste **Erweiterte Ereignisse** auf die Schaltfläche **Aggregation** . Das Dialogfeld Aggregation wird mit den für die Aggregation verfügbaren Spalten angezeigt.  
  
3.  Wählen Sie in der Spalte **Aggregationstyp** den Aggregationstyp aus.  
  
4.  Wählen Sie im Feld **Aggregation sortieren nach** den Sortierausdruck aus. Wählen Sie dann die aufsteigende oder absteigende Reihenfolge aus.  
  
### <a name="search-for-text-in-columns"></a>Textsuche in Spalten  
 Sie können Text in Spalten suchen:  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen. (Sie können auch mit der rechten Maustaste auf den Sitzungsnamen klicken und dann **Livedaten ansehen**auswählen.)  
  
2.  Klicken Sie auf der Symbolleiste **Erweiterte Ereignisse** auf die Schaltfläche **Suchen** .  
  
3.  Geben Sie im Dialogfeld **In erweiterten Ereignissen suchen** im Feld **Suchen nach** den Suchtext ein. In der Dropdownliste können Sie eine der letzten 20 Suchzeichenfolgen auswählen.  
  
4.  Wählen Sie im Feld **Suchen in** den Ort für die Suche nach dem angegebenen Text aus. Verwenden Sie zum Suchen die folgenden Optionen:  
  
    -   Tabellenspalten. Verwenden Sie diese Option, um alle sichtbaren Spalten im Ablaufverfolgungsfenster zu durchsuchen.  
  
    -   Details. Verwenden Sie diese Option zum Durchsuchen von allen Spalten (höhergestuften und nicht höhergestuften) im Ablaufverfolgungsfenster angezeigt werden, die vor dem Öffnen ausgewählt wurden die **in erweiterten Ereignissen suchen** Dialogfeld.  
  
    -   *Event_column_name*. Verwenden Sie diese Option, um in einer bestimmten Ereignisspalte aus der Dropdownliste zu suchen.  
  
5.  Verwenden Sie die folgenden Optionen, um anzugeben, wie Sie die Suche definieren möchten:  
  
    -   Groß-/Kleinschreibung beachten. Verwenden Sie diese Option, um für den im Feld Suchen nach eingegebenen Text die Suchergebnisse anzuzeigen, die in Inhalt und Schreibweise übereinstimmen.  
  
    -   Nur ganzes Wort suchen. Verwenden Sie diese Option, um nur die Suchergebnisse für den Text anzuzeigen, die mit vollständigen Wörtern übereinstimmen.  
  
    -   Suchrichtung nach oben. Verwenden Sie diese Option, um ab der Cursorposition zum Anfang der Ergebnisse zu suchen.  
  
    -   Verwendung. Verwenden Sie diese Option, um die Sonderzeichen und die regulären Ausdrücke zu interpretieren, die Sie im Feld Suchen nach eingegeben haben. Sonderzeichen zählen die Platzhalterzeichen (*) und (?), mit denen Sie ein oder mehrere Zeichen darstellen. Reguläre Ausdrücke sind besondere Schreibweisen, die verwendet wurden, um Muster im Suchtext zu definieren.  
  
    -   Klicken Sie auf **Weitersuchen** , um nach dem nächsten Vorkommen des Texts zu suchen, den Sie im Feld **Suchen nach** eingegeben haben.  
  
### <a name="bookmarks"></a>Lesezeichen  
 Um das Zurückkehren in eine Zeile zu erleichtern, können Sie eine oder mehrere Zeile(n) in den Zieldaten mit einem Lesezeichen versehen. Klicken Sie mit der rechten Maustaste auf eine Zeile, um das Lesezeichen zu ändern. Verwenden Sie auf der Symbolleiste **Erweiterte Ereignisse** die Schaltflächen Zurück und Weiter, um zu den mit Lesezeichen markierten Zeilen zu navigieren.  
  
### <a name="change-display-settings"></a>Ändern der Anzeigeeinstellungen  
 Sie können Spalteninformationen (Spaltenreihenfolge, Mergespalte und Spaltenbreite) und Filterinformationen eines Ablaufverfolgungsergebnisses in einer Anzeigeeinstellungsdatei (VIEWSETTING-Datei) für erweiterte Ereignisse speichern. Nach dem Speichern der Datei können Sie sie auf die Ablaufverfolgungsergebnisse anwenden, um die Ansicht zu ändern.  
  
 So ändern Sie die Anzeigeeinstellungen  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen. (Sie können auch mit der rechten Maustaste auf den Sitzungsnamen klicken und dann **Livedaten ansehen**auswählen.)  
  
2.  Wählen Sie auf der Symbolleiste **Erweiterte Ereignisse** die Option **Anzeigeeinstellungen**aus. Wählen Sie eine der folgenden Optionen aus der Dropdownliste aus:  
  
    -   Speichern unter. Speichern Sie die Spalten- und Filterinformationen eines Ablaufverfolgungsergebnisses in einer VIEWSETTING-Datei.  
  
    -   Öffnen Öffnen Sie eine vorhandene VIEWSETTING-Datei.  
  
    -   Zuletzt verwendete öffnen. Öffnen Sie eine vor kurzem gespeicherte VIEWSETTING-Datei.  
  
### <a name="copy-or-export-trace-results"></a>Kopieren oder Exportieren von Ablaufverfolgungsergebnissen  
 Sie können Zellen, Zeilen und Details in ausgewählten Zeilen aus Ablaufverfolgungsergebnissen kopieren. Sie können die Ablaufverfolgungsergebnisse auch in folgende Komponenten exportieren:  
  
-   XEL-Datei  
  
-   -Tabelle  
  
-   CSV-Datei  
  
 Um Ablaufverfolgungsergebnisse zu kopieren, wählen Sie eine Zelle bzw. mindestens eine Zeile aus, klicken mit der rechten Maustaste und wählen **Kopieren** und dann **Zelle**, **Zeile**oder **Details**aus. Erweiterte Ereignisse unterstützen das Kopieren von bis zu 1.000 Zeilen.  
  
 Sie können die Ablaufverfolgungsergebnisse in eine XEL-Datei, Tabelle oder CSV-Datei exportieren, indem Sie in der Menüoption **Erweiterte Ereignisse** in **die Option** Exportieren nach [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]auswählen.  
  
### <a name="view-a-deadlock-graph-and-query-plans"></a>Anzeigen von einem Deadlockdiagramm und von Abfrageplänen  
 Zur einfacheren Behebung von Deadlockfehlern können Sie das Deadlockdiagramm für **xml_deadlock_report** im Detailbereich anzeigen. Sie können auch Abfrageplandiagramme für die folgenden Ereignisse anzeigen:  
  
-   query_post_compilation_showplan  
  
-   query_pre_execution_showplan  
  
-   query_post_execution_showplan  
  
 So zeigen Sie das Deadlockdiagramm an  
  
-   Erweitern Sie im Objekt-Explorer die Knoten **Verwaltung**, **Erweiterte Ereignisse**und dann **Sitzungen** .  
  
-   Klicken Sie mit der rechten Maustaste auf die Sitzung, die das anzuzeigende konfigurierte Deadlockereignis enthält, und wählen Sie dann **Livedaten ansehen**aus.  
  
-   Wählen Sie das Deadlockereignis aus, und zeigen Sie das Diagramm im Detailbereich auf der Registerkarte **Deadlock** an.  
  
 So zeigen Sie Abfrageplandiagramme an  
  
1.  Erweitern Sie im Objekt-Explorer die Knoten **Verwaltung**, **Erweiterte Ereignisse**und dann **Sitzungen** .  
  
2.  Klicken Sie mit der rechten Maustaste auf die Sitzung mit dem Abfrageplandiagramm, das Sie anzeigen möchten (beispielsweise query_post_compilation_showplan), und wählen Sie dann die Option **Livedaten ansehen**aus.  
  
3.  Wählen Sie das Abfrageplandiagrammereignis aus (z. B. query_post_compilation_showplan), und zeigen Sie das Diagramm im Detailbereich auf der Registerkarte **Abfrageplan** an.  
  
  
