---
title: Erstellen einer Sitzung für erweiterte Ereignisse mithilfe des Assistenten (Objekt-Explorer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- Sql12.ssms.XeWizard.Summary.f1
- Sql12.ssms.XeWizard.SetSessionProperties.f1
- Sql12.ssms.XeWizard.CaptureAddFields.f1
- Sql12.ssms.XeWizard.SelectEvents.f1
- Sql12.ssms.XeWizard.SpecifySessionTargets.f1
- Sql12.ssms.XeWizard.Welcome.f1
- sql12.ssms.XeWizard.Welcome.f1
- Sql12.ssms.XeWizard.ChooseTemplate.f1
- Sql12.ssms.XeWizard.SetSessionEventFilters.f1
- Sql12.ssms.XeWizard.Results.f1
helpviewer_keywords:
- Sql11.ssms.XeWizard.CaptureAddFields.f1
- Sql11.ssms.XeWizard.SetSessionEventFilters.f1
- Sql11.ssms.XeWizard.SpecifySessionTargets.f1
- Sql11.ssms.XeWizard.Results.f1
- Sql11.ssms.XeWizard.ChooseTemplate.f1
- Sql11.ssms.XeWizard.SetSessionProperties.f1
- Sql11.ssms.XeWizard.Welcome.f1
- Sql11.ssms.XeWizard.Summary.f1
- Sql11.ssms.XeWizard.SelectEvents.f1
ms.assetid: 80c0456f-17c0-41d8-b2aa-502a2f3bb6de
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cdc50e81bcc58722a3c04fc8516b9158072533cf
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66065062"
---
# <a name="create-an-extended-events-session-using-the-wizard-object-explorer"></a>Erstellen einer Sitzung für erweiterte Ereignisse mithilfe des Assistenten (Objekt-Explorer)
  Um Ihnen bei der Auswahl und Aufzeichnung von Ereignissen auf dem Server behilflich zu sein, umfasst Erweiterte Ereignisse einen Assistenten für neue Sitzungen, der Sie durch die Schritte der Erstellung einer Sitzung für erweiterte Ereignisse führt. Mit dem Assistenten für neue Sitzungen die meisten Funktionen erweiterter Ereignisse angezeigt. Mit dem Dialogfeld [Neue Sitzung](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md) können Sie zudem eine Sitzung für erweiterte Ereignisse definieren, die Ihre Daten erfasst, anzeigt und analysiert. Mit dem Dialogfeld "Neue Sitzung" werden alle Funktionen erweiterter Ereignisse angezeigt.  
  
### <a name="to-open-the-new-session-wizard"></a>So öffnen Sie den Assistenten für neue Sitzungen  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** , und erweitern Sie dann **Erweiterte Ereignisse**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Sitzungen**, und klicken Sie dann auf **Assistent für neue Sitzungen**.  
  
### <a name="use-the-following-new-session-wizard-pages-to-create-an-event-session"></a>Verwenden der folgenden Seiten des Assistenten für neue Sitzungen zum Erstellen einer Ereignissitzung  
  
-   [Einführung](#BKMK_Welcome)  
  
-   [Festlegen von Sitzungseigenschaften](#BKMK_SetSessionProperties)  
  
-   [Wählen Sie aus](#BKMK_ChooseTemplate)  
  
-   [Aufzuzeichnende Ereignisse auswählen](#BKMK_SelectEventsToCapture)  
  
-   [Globale Felder aufzeichnen](#BKMK_CaptureGlobalFields)  
  
-   [Filter für Sitzungsereignisse festlegen](#BKMK_SetSessionEventFilters)  
  
-   [Sitzungsdatenspeicher angeben](#BKMK_SpecifySessionDataOutput)  
  
-   [Zusammenfassung](#BKMK_Summary)  
  
-   [Ereignissitzung erstellen](#BKMK_CreateEventSession)  
  
##  <a name="BKMK_Welcome"></a> Einführung  
 Gehen Sie auf der Seite **Einführung** wie folgt vor:  
  
-   Klicken Sie auf der Seite **Einführung** des Assistenten für neue Sitzungen auf **Weiter**.  
  
     Aktivieren Sie das Kontrollkästchen **Diese Seite nicht mehr anzeigen**, wenn Sie den Assistenten mehrmals verwenden werden und nicht bei jedem Start des Assistenten die Einführung lesen möchten.  
  
##  <a name="BKMK_SetSessionProperties"></a> Festlegen von Sitzungseigenschaften  
 Geben Sie auf der Seite **Sitzungseigenschaften festlegen** die folgenden Werte ein:  
  
-   Geben Sie im Feld **Sitzungsname** einen aussagekräftigen Namen für die Ereignissitzung ein.  
  
     Wenn Sie möchten, dass die Sitzung gestartet wird, wenn Sie den Server starten, aktivieren Sie das Kontrollkästchen **Ereignissitzung beim Serverstart starten** , und klicken Sie dann auf **Weiter**.  
  
##  <a name="BKMK_ChooseTemplate"></a> Wählen Sie aus  
 Führen Sie auf der Seite **Vorlage auswählen** die folgenden Schritte aus:  
  
-   Aktivieren Sie die Option **Diese Ereignissitzungsvorlage verwenden** , um aus einem Satz vorkonfigurierter Vorlagen für häufig auftretende Probleme eine Auswahl zu treffen. Wählen Sie die gewünschte Vorlage aus der Dropdownliste aus, und klicken Sie dann auf **Weiter**.  
  
     -oder-  
  
-   Aktivieren Sie die Option **Keine Vorlage verwenden** , wenn Sie keine vorkonfigurierte Vorlage verwenden möchten, und klicken Sie dann auf **Weiter**.  
  
##  <a name="BKMK_SelectEventsToCapture"></a> Aufzuzeichnende Ereignisse auswählen  
 Gehen Sie auf der Seite **Aufzuzeichnende Ereignisse auswählen** wie folgt vor:  
  
1.  Wählen Sie die Ereignisse, die Sie aufzeichnen möchten, aus der **Ereignisbibliothek**aus, und klicken Sie auf den Pfeil nach rechts. Durch UMSCHALT+Klicken oder STRG+Klicken können Sie mehrere Ereignisse in der Ereignisbibliothek auswählen.  
  
     Sie können in der Dropdownliste auswählen, wie nach den Ereignissen gesucht werden soll, die Sie aufzeichnen möchten. Sie können beispielsweise nach Ereignisnamen oder Ereignisnamen und ihren Beschreibungen suchen. Sie können in der Tabelle nach einem beliebigen Wort suchen, indem Sie im Feld **Ereignisbibliothek** den Text eingeben, den Sie suchen möchten. Wenn Sie z. B. das Ereignis **lock_acquired** suchen möchten, können Sie **lock**oder **lock acquire**eingeben.  
  
     Die Ereignisse, die Sie auswählen, werden im Feld **Ausgewählte Ereignisse** angezeigt. Um Ereignisse aus dem Feld **Ausgewählte Ereignisse** zu entfernen, klicken Sie auf die NACH-LINKS-TASTE.  
  
2.  Nachdem Sie die Ereignisse ausgewählt haben, die Sie aufzeichnen möchten, klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Ereignisse aus dem Kanal **Debuggen** sind standardmäßig ausgeblendet. Um Debugereignisse anzuzeigen, wählen Sie **Debuggen** aus der Dropdownliste **Kanal** aus.  
  
##  <a name="BKMK_CaptureGlobalFields"></a> Globale Felder aufzeichnen  
 Globale Felder (auch als Aktionen bezeichnet) werden verwendet, um einzelne oder mehrere Aktionen für die ausgewählten Ereignisse zuzuordnen. Wenn Sie auf der Seite **Vorlage auswählen** eine Vorlage auswählten, werden alle globalen Felder, die in der Vorlage definiert sind, auf dieser Seite angezeigt.  
  
 Gehen Sie auf der Seite **Globale Felder aufzeichnen** wie folgt vor:  
  
-   Wählen Sie die globalen Felder aus, die Sie für die Ereignissitzung aufzeichnen möchten, und klicken Sie dann auf **Weiter**.  
  
     Sie können globale Felder hinzufügen oder entfernen, indem Sie das Kontrollkästchen neben dem globalen Feld aktivieren bzw. deaktivieren.  
  
    > [!NOTE]  
    >  Die ausgewählten Aktionen werden nach **Namen** sortiert, sodass Sie die Möglichkeit haben, die zugeordneten Aktionen in alphabetischer Reihenfolge anzuzeigen. Sie können nach auch nach Beschreibung oder dem Aktivierungs-/Deaktivierungsstatus sortieren, indem Sie auf die Spaltenüberschrift neben dem Feldnamen klicken.  
  
##  <a name="BKMK_SetSessionEventFilters"></a> Filter für Sitzungsereignisse festlegen  
 Sie können Filter (auch als Prädikate bezeichnet) anwenden, um die Ereignisse, die Sie aufzeichnen möchten, einzuschränken. Gehen Sie auf der Seite **Filter für Sitzungsereignisse festlegen** wie folgt vor:  
  
1.  Wenn Sie keine vorkonfigurierte Vorlage verwenden, erstellen die Filterkriterien, und klicken dann auf **Weiter**.  
  
     Wenn Sie eine vorkonfigurierte Vorlage verwenden, werden im Abschnitt **Filter aus Vorlage (schreibgeschützt)** vom Assistenten für neue Sitzungen bereits aus der Vorlage erstellte Filter aufgeführt.  
  
2.  Im Abschnitt **Zusätzliche Filter** können Sie zusätzliche Filter für die Ereignissitzung konfigurieren.  
  
     Die Filter, die Sie konfigurieren, gelten für alle ausgewählten Ereignisse. Vom Assistenten für neue Sitzungen wird das Konfigurieren von Filtern für jedes einzelne Ereignis nicht unterstützt.  
  
    > [!NOTE]  
    >  Wenn Sie eine Gruppenklausel für den Filter konfigurieren, werden redundante Klammern aus dem Filter entfernt, nachdem das Ergebnis gespeichert wurde. Wenn Sie z. B. einen Filter erstellen, der **Klausel 1** und **Klausel 2**gruppiert, werden Klammern um die Klauseln angezeigt. Nachdem Sie den Filter gespeichert haben, werden die redundanten Klammern entfernt. Das Entfernen der Klammern hat keine Auswirkungen auf die Filterlogik.  
  
##  <a name="BKMK_SpecifySessionDataOutput"></a> Sitzungsdatenspeicher angeben  
 Auf der Seite **Sitzungsdatenspeicher angeben** geben Sie an, wie Daten für die Analyse erfasst werden sollen. SQL Server Erweiterte Ereignisse verwendet Ziele für die Datenausgabe. Ziele speichern Ereignisdaten und können Aktionen, wie z. B. das Schreiben in eine Datei und das Aggregieren von Ereignisdaten, ausführen. Überlegen Sie sich, wie Sie die Daten für die Analyse erfassen möchten, und gehen Sie auf der Seite **Sitzungsdatenspeicher angeben** folgendermaßen vor:  
  
1.  Bei großen Datasets und beim Erstellen von historischen Datensätzen aktivieren Sie das Kontrollkästchen **Daten zur späteren Analyse in einer Datei speichern** , und gehen Sie dann wie folgt vor:  
  
    1.  Geben Sie im Feld **Dateiname auf Server** den Pfad und den Dateinamen ein, oder klicken Sie auf **Durchsuchen** , um das Dateiverzeichnis, in dem Sie die Daten speichern möchten, auf dem Server anzugeben.  
  
    2.  Aktivieren Sie das Kontrollkästchen **Maximale Dateigröße** , und geben Sie die maximale Dateigröße für die Zieldatei an. Wenn Sie keine maximale Dateigröße angeben, wird die Datei immer größer, bis der Speicherplatz auf dem Datenträger erschöpft ist. Die Standarddateigröße beträgt 1 Gigabyte (GB).  
  
    3.  Aktivieren Sie das Kontrollkästchen **Dateirollover aktivieren** , um Dateirollover für das Dateiziel zu aktivieren.  
  
    4.  Geben Sie im Feld **Maximale Anzahl von Dateien** die maximale Anzahl von Dateien an, die Sie im Dateisystem beibehalten möchten.  
  
2.  Aktivieren Sie zum Erfassen der neuesten Daten das Kontrollkästchen **Nur die neuesten Daten verwenden (ring_buffer-Ziel)** , und gehen Sie dann wie folgt vor:  
  
    1.  Im Feld **Anzahl beizubehaltender Ereignisse** geben Sie mithilfe der NACH-OBEN- und der NACH-UNTEN-TASTE die Anzahl der Ereignisse ein, die Sie beibehalten möchten, oder wählen diese aus.  
  
    2.  Geben Sie im Feld **Max. Pufferspeichergröße** die maximale Menge Pufferspeicher an, die verwendet werden soll. Die vorhandenen Ereignisse werden gelöscht, wenn dieser Wert erreicht wird.  
  
    3.  Wenn Sie eine bestimmte Anzahl von Ereignissen jedes Typs im Puffer beibehalten möchten, aktivieren Sie das Kontrollkästchen **Angegebene Anzahl von Ereignissen (pro Typ) bei vollem Puffer beibehalten** .  
  
    4.  Im Feld **Anzahl beizubehaltender Ereignisse (pro Typ)** geben Sie mithilfe der NACH-OBEN- und der NACH-UNTEN-TASTE die Anzahl der Ereignisse (pro Typ) ein, die Sie beibehalten möchten, oder wählen diese aus.  
  
##  <a name="BKMK_Summary"></a> Zusammenfassung  
 Gehen Sie auf der Seite **Zusammenfassung** wie folgt vor:  
  
1.  Stellen Sie sicher, dass die Auswahl richtig ist. Erweitern Sie die Ereignissitzungsknoten, um zu überprüfen, dass die gesamte Auswahl in die Ereignissitzung eingeschlossen wird.  
  
2.  Klicken Sie auf **Skript** , um das Sitzungserstellungsskript in ein neues Abfrage-Editor-Fenster zu exportieren.  
  
3.  Klicken Sie auf **Fertig stellen** , um die Ereignissitzung zu erstellen.  
  
##  <a name="BKMK_CreateEventSession"></a> Ereignissitzung erstellen  
 Nachdem die Ereignissitzung erfolgreich erstellt wurde, gehen Sie auf der Seite **Ereignissitzung erstellen** folgendermaßen vor:  
  
1.  Klicken Sie auf **Ereignissitzung direkt nach dem Erstellen der Sitzung starten** , um die Sitzung zu starten, nachdem Sie den Assistenten geschlossen haben. Sie müssen die Ereignissitzung unmittelbar nach dem Erstellen der Sitzung starten, damit Sie die Livedaten beobachten können.  
  
2.  Klicken Sie auf **Livedaten während der Aufzeichnung auf dem Bildschirm ansehen** , um Livedaten für die Ereignissitzung anzuzeigen. Unmittelbar nach der Erstellung der Sitzung wird für die Livedaten eine Ablaufverfolgung gestartet.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Sitzung für erweiterte Ereignisse im Dialogfeld für neue Sitzungen](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)  
  
  
