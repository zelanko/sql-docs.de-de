---
title: Erstellen einer Sitzung für erweiterte Ereignisse mit dem Dialogfeld "neue Sitzung" | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.SSMS.XEDISPLAY.GROUPING.F1
- SQL12.SSMS.XEDISPLAY.AGGREGATION.F1
- SQL12.SSMS.XEDISPLAY.NEWMERGEDCOLUMN.F1
- SQL12.SSMS.XENEWEVENTSESSION.GENERAL.F1
- SQL12.SSMS.XEDISPLAY.EDITCOLUMNS.F1
- SQL12.SSMS.XEDISPLAY.FILTERS.F1
helpviewer_keywords:
- Extended Events Dialog Box
ms.assetid: 6b2244bc-df6a-4b0a-990e-ddd8d42f7907
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 52b40b5fe3a43565acacfdc0b85f3404f9c10a88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056109"
---
# <a name="create-an-extended-events-session-using-the-new-session-dialog"></a>Erstellen einer Sitzung für erweiterte Ereignisse im Dialogfeld für neue Sitzungen
  Mit dem Dialogfeld "Neue Sitzung" können Sie eine Sitzung für erweiterte Ereignisse definieren, die Ihre Daten erfasst, anzeigt und analysiert. Mit dem Dialogfeld "Neue Sitzung" werden alle Funktionen erweiterter Ereignisse angezeigt.  
  
 Mit dem Assistenten für neue Sitzungen [](../ssms/object/object-explorer.md) können Sie zudem eine Sitzung für erweiterte Ereignisse definieren, mit der die meisten Funktionen erweiterter Ereignisse unterstützt werden.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Um das Dialogfeld für eine neue Sitzung im Objekt-Explorer zu öffnen, erweitern Sie den Knoten **Verwaltung** , und erweitern Sie dann **Erweiterte Ereignisse**. Klicken Sie mit der rechten Maustaste auf **Sitzungen**, und klicken Sie dann auf **Neue Sitzung**.  
  
##  <a name="BeforeYouBegin"></a> Berechtigungen  
 Zum Erstellen einer Sitzung für erweiterte Ereignisse müssen Sie über die ALTER ANY EVENT SESSION-Berechtigung verfügen.  
  
## <a name="to-create-an-extended-events-session-using-the-new-session-dialog"></a>So erstellen Sie eine Sitzung für erweiterte Ereignisse im Dialogfeld für neue Sitzungen  
 Verwenden Sie die Seite **Allgemein** , um eine Vorlage auszuwählen und eine Ereignissitzung zu planen.  
  
#### <a name="to-select-a-template-and-schedule-an-event-session"></a>So wählen Sie eine Vorlage aus und planen eine Ereignissitzung  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** , und erweitern Sie dann **Erweiterte Ereignisse**. Klicken Sie mit der rechten Maustaste auf **Sitzungen**, und klicken Sie dann auf **Neue Sitzung**.  
  
2.  Geben Sie auf der Seite **Allgemein** im Feld **Sitzungsname** einen aussagekräftigen Namen für die Ereignissitzung ein.  
  
3.  Wählen Sie im Feld **Vorlage** die gewünschte Vorlage aus der Dropdownliste aus.  
  
     Sie können aus einem Satz vorkonfigurierter Vorlagen auswählen, die für häufige Probleme entwickelt wurden, oder Sie können **Aus Datei** auswählen, um eine aus einer vorherigen Sitzungsdefinition exportierte Vorlagendatei zu verwenden. Beachten Sie, dass Sie auch die Konfiguration der Sitzung ändern können, nachdem Sie die Vorlage angewendet haben.  
  
4.  Wenn Sie möchten, dass die Sitzung gestartet wird, wenn Sie den Server starten, aktivieren Sie im Bereich **Zeitplan** das Kontrollkästchen **Ereignissitzung beim Serverstart starten** .  
  
     Wenn Sie die Sitzung starten möchten, nachdem Sie die Sitzung erstellt haben, aktivieren Sie das Kontrollkästchen **Ereignissitzung direkt nach dem Erstellen der Sitzung starten** .  
  
5.  Klicken Sie auf **Livedaten während der Aufzeichnung auf dem Bildschirm ansehen**, um Livedaten für die Ereignissitzung anzuzeigen. Unmittelbar nach der Erstellung der Sitzung wird für die Livedaten eine Ablaufverfolgung gestartet.  
  
6.  Aktivieren Sie im Abschnitt **Kausalitätsverfolgung** das Kontrollkästchen **Nachverfolgen, in welcher Beziehung Ereignisse zueinander stehen** , um die Arbeit über mehrere Tasks nachzuverfolgen.  
  
     Weitere Informationen zur Kausalitätsverfolgung finden Sie unter "Sitzungsinhalt und -eigenschaften" im Thema [SQL Server Extended Events Sessions](../relational-databases/extended-events/sql-server-extended-events-sessions.md) .  
  
     Um der Sitzung Ereignisse hinzuzufügen, klicken Sie im Bereich **Seite auswählen** auf **Ereignisse**.  
  
    > [!NOTE]  
    >  Klicken Sie erst auf **OK** , wenn Sie mit dem Erstellen der Ereignissitzung fertig sind.  
  
 Die Seite **Ereignisse** wird verwendet, um die Ereignisse, die Sie für die Sitzung aufzeichnen möchten, zu suchen und hinzuzufügen.  
  
#### <a name="to-add-events-to-a-session"></a>So fügen Sie einer Sitzung Ereignisse hinzu  
  
1.  Wählen Sie im Dialogfeld für die neue Sitzung im Bereich **Seite auswählen** die Option **Ereignisse**aus.  
  
2.  Klicken Sie auf der Seite **Ereignisse** auf **Auswählen** (die Schaltfläche **Auswählen** ist abgeblendet, wenn Sie sich bereits auf dem Bildschirm **Ereignisse auswählen, die Sie aufzeichnen möchten** befinden).  
  
     Sie können in der Tabelle nach einem beliebigen Wort suchen, indem Sie im Feld **Ereignisbibliothek** den Text eingeben, den Sie suchen möchten. Wenn Sie z. B. das Ereignis **lock_acquired** suchen möchten, können Sie **lock** oder **lock acquire**eingeben.  
  
3.  Wählen Sie im Abschnitt **Ereignisbibliothek** aus der Dropdownliste aus, wie Sie nach den Ereignissen suchen möchten, die Sie aufzeichnen möchten. Sie können beispielsweise nach Ereignisnamen oder Ereignisnamen und ihren Beschreibungen suchen. Geben Sie die Suchkriterien im Feld **Suchen** ein.  
  
    > [!NOTE]  
    >  Ereignisse aus dem Kanal **Debuggen** sind standardmäßig ausgeblendet. Um Debugereignisse anzuzeigen, wählen Sie **Debuggen** aus der Dropdownliste **Kanal** aus.  
  
     Details für die ausgewählten Ereignisse werden im Detailbereich unter der **Ereignisbibliothek**angezeigt.  
  
     Die Ereignisse sind nach Namen in alphabetischer Reihenfolge sortiert. Sie können nach anderen Ereignisdetails sortieren, indem Sie auf die entsprechende Spaltenüberschrift klicken. Sie können z. B. nach der Spalte **Kategorie** oder **Kanal** sortieren.  
  
4.  Wählen Sie das Ereignis (s) aus, das Sie aufzeichnen möchten, und klicken Sie dann auf die NACH-RECHTS-TASTE, um das Ereignis/die Ereignisse in den Abschnitt **Ausgewählte Ereignisse** zu verschieben.  
  
    > [!NOTE]  
    >  Mit der STRG- oder der UMSCHALTTASTE können Sie mehrere Ereignisse gleichzeitig aus der **Ereignisbibliothek** auswählen.  
  
     Um die ausgewählten Ereignisse zu konfigurieren, klicken Sie auf **Konfigurieren**.  
  
    > [!NOTE]  
    >  Klicken Sie erst auf **OK** , wenn Sie mit dem Erstellen der Ereignissitzung fertig sind.  
  
 Die Seite **Datenspeicher** wird verwendet, um einer Ereignissitzung Ziele hinzuzufügen. Ziele speichern Ereignisdaten und können Aktionen, wie z. B. das Speichern von Ereignissen in eine Datei zum späteren Anzeigen und Aggregieren von Ereignisdaten für die Sitzung, ausführen. Weitere Informationen zu Zielen für erweiterter Ereignisse finden Sie unter [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
 Die folgenden Ziele werden zur Verwendung in einer Sitzung für erweiterte Ereignisse bereitgestellt:  
  
-   **etw_classic_sync_target**. Wird eingesetzt, um SQL Server-Ereignisse mit Ereignisdaten von Anwendungen oder des Windows-Betriebssystems zu korrelieren.  
  
-   **event_counter**. Zählt alle angegebenen Ereignisse, die auftreten, nachdem eine Sitzung für erweiterte Ereignisse gestartet wurde. Wird eingesetzt, um Informationen über Merkmale der Arbeitsauslastung ohne den Aufwand einer vollständigen Ereignisauflistung zu sammeln.  
  
-   **event_file**. Wird eingesetzt, um die Ereignissitzungsausgabe aus vollständigen Speicherpuffern auf die Festplatte zu schreiben.  
  
-   **histogram**. Dient dazu, die Häufigkeit eines bestimmten Ereignisses auf Grundlage einer bestimmten Ereignisspalte oder Aktion zu zählen.  
  
-   **pair_matching**. Ereignispaarbildung wird eingesetzt, um zu bestimmen, wann ein spezifisches, kombiniertes Ereignis nicht als Paar auftritt.  
  
-   **ring_buffer**. Wird verwendet, um die Ereignisdaten auf Basis der FIFO-Reihenfolge (First-In-First-Out) oder auf Basis der ereignisbezogenen FIFO-Reihenfolge im Speicher zu behalten.  
  
#### <a name="to-configure-global-fields-for-a-session"></a>So konfigurieren Sie globale Felder für eine Sitzung  
  
1.  Klicken Sie, nachdem Sie das Ereignis bzw. die Ereignisse, die Sie der Ereignissitzung hinzufügen möchten, ausgewählt haben, auf der Seite **Ereignisse** auf **Konfigurieren**.  
  
     Nachdem Sie auf **Konfigurieren**geklickt haben, wird der Abschnitt **Ereignisbibliothek** reduziert, und der Abschnitt **Ausgewählte Ereignisse** wird an den linken Rand der Seite verschoben. Der Abschnitt **Optionen für die Ereigniskonfiguration** , in dem Sie die Ereignisse konfigurieren, wird auf der rechten Seite der Seite angezeigt. Verwenden Sie die Registerkarten auf dieser Seite, um Aktionen für die Ereignissitzung zu konfigurieren.  
  
2.  Wählen Sie auf der Registerkarte **Globale Felder** die Felder aus, die Sie auf die ausgewählten Ereignisse anwenden möchten.  
  
     Sie können mehrere Felder für jedes Ereignis auswählen.  
  
    > [!NOTE]  
    >  Wenn zwei Ereignisse, die bereits ausgewählt wurden, über unterschiedliche konfigurierte Aktionen verfügen, werden von Erweiterte Ereignisse die teilweise überprüften Aktionen angezeigt. Um schnell herauszufinden, welche Aktionen Sie aktiviert haben, können Sie nach dem aktivierten/deaktivierten Status sortieren, indem Sie auf die Spaltenüberschrift über den Kontrollkästchen klicken.  
  
3.  Wenden Sie auf der Registerkarte  **Filter** die Filter (auch als Prädikate bezeichnet) an, um die Ereignisse, die Sie aufzeichnen möchten, einzuschränken.  
  
     Wenn ein Filter auf das ausgewählte Ereignis angewendet wird, wird in der Spalte ein Häkchen angezeigt.  
  
    > [!NOTE]  
    >  Sie können mithilfe der STRG-Taste oder der UMSCHALTTASTE mehrere Ereignisse auswählen, auf die Sie einen Filter anwenden möchten. Es werden jedoch nur häufig verwendete Ereignisfelder für die Konfiguration angezeigt. Wenn zwei ausgewählte Ereignisse bereits über unterschiedliche Filter verfügen, die für sie konfiguriert wurden, wird der Filter nicht angezeigt. Durch erneutes Konfigurieren von Filtern werden vorhandene Filterwerte überschrieben.  
  
    > [!NOTE]  
    >  Wenn Sie eine Gruppenklausel für den Filter konfigurieren, werden redundante Klammern aus dem Filter entfernt, nachdem das Ergebnis gespeichert wurde. Wenn Sie z. B. einen Filter erstellen, der **Klausel 1** und **Klausel 2**gruppiert, werden Klammern um die Klauseln angezeigt. Nachdem Sie den Filter gespeichert haben, werden die redundanten Klammern entfernt. Das Entfernen der Klammern hat keine Auswirkungen auf die Filterlogik.  
  
4.  Auf der Registerkarte **Ereignisfelder** wählen Sie die Ereignisfelder aus, die Sie auf ein ausgewähltes Ereignis anwenden möchten.  
  
     Ereignisse enthalten eine Reihe von Feldern, die immer gesammelt werden, und die auf der Registerkarte **Ereignisfelder** ohne Kontrollkästchen angezeigt werden. Ein Ereignis kann auch über optionale Felder verfügen, die nicht standardmäßig gesammelt werden (aufwändige optionale Felder werden beispielsweise nicht ausgewählt). Optionale Felder sind auch auf der Registerkarte **Ereignisfelder** mit Kontrollkästchen aufgeführt. Um ein optionales Feld zu sammeln, aktivieren Sie das Kontrollkästchen vor dem optionalen Feld.  
  
    > [!NOTE]  
    >  In den Optionen für die Ereignisfelder werden Felder angezeigt, die in den Ablaufverfolgungsergebnissen aufgezeichnet und angezeigt werden. (Erweiterte Ereignisse zeigt nur Datentypen der Ereignisfelder an. Schreibgeschützte Ereignisfelder werden beispielsweise nicht angezeigt.) Wenn Sie zwei oder mehr Ereignisse auswählen, wird im Dialogfeld für die neue Sitzung eine leere Stelle auf der Registerkarte **Ereignisfelder** angezeigt.  
  
5.  Um einer Ereignissitzung Ziele hinzuzufügen, wählen Sie im Abschnitt **Seite auswählen** die Option **Datenspeicher**aus.  
  
    > [!NOTE]  
    >  Klicken Sie erst auf **OK** , wenn Sie mit dem Erstellen der Ereignissitzung fertig sind.  
  
#### <a name="to-add-targets-to-an-event-session"></a>So fügen Sie einer Ereignissitzung Ziele hinzu  
  
1.  Wählen Sie im Dialogfeld für die neue Sitzung im Bereich **Seite auswählen** die Option **Datenspeicher**aus.  
  
2.  Wählen Sie auf der Seite **Datenspeicher** den Zieltyp aus der Dropdownliste aus.  
  
     Nachdem Sie den Zieltyp ausgewählt haben, wird die Zielbeschreibung angezeigt. Sie können ein Ziel nur einmal hinzufügen. Wenn Sie das Ziel der Sitzung bereits hinzugefügt haben, wird es nicht in der Dropdownliste angezeigt.  
  
3.  Klicken Sie auf **Hinzufügen** , um ein Ziel für die Ereignissitzung hinzuzufügen. Wenn Sie ein Ziel entfernen möchten, klicken Sie auf **Entfernen**.  
  
     Zieleigenschaften werden in Abhängigkeit von dem ausgewählten Ziel unter dem Abschnitt **Ziele** angezeigt.  
  
4.  Nachfolgend finden Sie die Eigenschaften, die Sie je nach den ausgewählten Zielen angeben können:  
  
    |Ziel|Zieleigenschaften|  
    |------------|-----------------------|  
    |**etw_classic_sync_target**|**Name der Sitzungsprotokolldatei auf Server**. Geben Sie den Protokolldateinamen und das Verzeichnis auf dem Server ein, oder klicken Sie auf **Durchsuchen** , um die Protokolldatei zu suchen und auszuwählen.<br /><br /> **Maximale Protokolldateigröße**. Geben Sie die maximale Protokolldateigröße für das ETW-Ereignis (Ereignisablaufverfolgung für Windows) ein. Der Standardwert ist 20 MB. Sie können aus der Dropdownliste eine andere Speichereinheit auswählen.<br /><br /> **Puffergröße**. Geben Sie die Puffergröße im Arbeitsspeicher für die Ereignissitzung ein. Der Standardwert ist 128 KB. Sie können aus der Dropdownliste eine andere Speichereinheit auswählen.<br /><br /> **Sitzungsname**. Geben Sie einen aussagekräftigen Namen für die ETW-Sitzung ein.<br /><br /> **Bei Schreibfehler in ETW wiederholen**. Aktivieren Sie dieses Kontrollkästchen, um die Veröffentlichung des Ereignisses im ETW-Subsystem erneut zu versuchen.<br /><br /> **Maximale Anzahl von Wiederholungen**. Geben Sie die maximale Anzahl von erneuten Versuchen für die Veröffentlichung des Ereignisses im ETW-Subsystem an, bevor das Ereignis gelöscht wird. Die Standardanzahl von Wiederholungen beträgt 0 (null). Für diese Zieleigenschaft bedeuten 0 (null) keine Wiederholungen.|  
    |**event_counter**|Es gibt keine Zieleigenschaften für den Ereigniszähler.|  
    |**event_file**|**Dateiname auf Server**. Geben Sie das Verzeichnis und den Zieldateinamen auf dem Server ein, oder klicken Sie auf **Durchsuchen** , um die Zieldatei zu suchen und auszuwählen.<br /><br /> **Maximale Dateigröße**. Geben Sie die maximale Dateigröße für das Dateiziel an. Wenn Sie keine maximale Dateigröße angeben, wird die Datei immer größer, bis der Speicherplatz auf dem Datenträger erschöpft ist. Die Standarddateigröße beträgt 1 Gigabyte (GB). Sie können aus der Dropdownliste eine andere Speichereinheit auswählen.<br /><br /> **Dateirollover aktivieren**. Aktivieren Sie dieses Kontrollkästchen, um einen Dateirollover für das Dateiziel zu aktivieren.<br /><br /> **Maximale Anzahl von Rolloverdateien**. Geben Sie die maximale Anzahl der Dateien an, die Sie im Dateisystem beibehalten möchten.|  
    |**Histogramm**|**Ereignis, nach dem gefiltert werden soll**. Wählen Sie das Ereignis, nach dem gefiltert werden soll aus der Dropdownliste aus. Sie können nach einen beliebigen Ereignis filtern, das in der Ereignissitzung vorhanden ist. Sie können auch auswählen  **\<None >** aus der Dropdownliste aus, um alle Ereignisse und die basisbuckets für die Aktion einzuschließen.<br /><br /> **Buckets basieren auf: Aktion**. Aktivieren Sie diese Option, um die Buckets auf dem Aktionsnamen zu basieren, der als Datenquelle verwendet wird, und wählen Sie dann die Aktion aus der Dropdownliste aus.<br /><br /> **Buckets basieren auf: Feld**. Aktivieren Sie diese Option, um die Buckets auf dem Ereignisfeld zu basieren, das als Datenquelle verwendet wird, und wählen Sie dann das Feld aus der Dropdownliste aus.<br /><br /> **Maximale Bucketanzahl**. Geben Sie die maximale Anzahl von Buckets ein, die Sie beibehalten möchten. Wenn dieser Wert erreicht wird, ignoriert die Ereignissitzung alle neuen Ereignisse, die nicht zu den vorhandenen Buckets gehören.|  
    |**pair_matching**|**Ereignisse: Beginnen mit**. Wählen Sie den Ereignisnamen, der das Anfangsereignis in einer paarweise zugeordneten Sequenz angibt, aus der Dropdownliste aus.<br /><br /> **Ereignisse: Enden mit**. Wählen Sie den Ereignisnamen, der das Endereignis in einer paarweise zugeordneten Sequenz angibt, aus der Dropdownliste aus.<br /><br /> **Felder und Aktionen: Beginnen mit**. Wählen Sie das Anfangsfeld und/oder eine Aktion in einer paarweise zugeordneten Sequenz aus der Dropdownliste aus.<br /><br /> **Felder und Aktionen: Enden mit**. Wählen Sie das Endfeld und/oder eine Aktion in einer paarweise zugeordneten Sequenz aus der Dropdownliste aus.<br /><br /> **Neue nicht gepaarte Ereignisse bei ungenügendem Arbeitsspeicher verwerfen**. Aktivieren Sie dieses Kontrollkästchen, um die Sammlung von Ereignissen für das pair_matching-Ziel zu beenden, wenn nicht genügend Arbeitsspeicher vorhanden ist. Wenn wieder mehr Arbeitsspeicher vorhanden ist, wird die Sammlung von Ereignissen fortgesetzt.<br /><br /> **Maximale verwaiste Ereignisse**. Geben Sie die maximale Anzahl verwaister Ereignisse an, die Sie im Arbeitsspeicher beibehalten möchten.|  
    |**ring_buffer**|**Anzahl beizubehaltender Ereignisse**. Geben Sie mithilfe der NACH-OBEN-TASTE und der NACH-UNTEN-TASTE die Anzahl von Ereignissen an, die Sie beibehalten möchten. Der Standardwert lautet 1000.<br /><br /> **Maximale Pufferspeichergröße**. Geben Sie die Höchstmenge des verfügbaren Arbeitsspeichers ein. Vorhandene Ereignisse werden gelöscht, wenn dieser Wert erreicht wird. Die Standardspeichergröße beträgt 0 Megabyte (MB) (bedeutet unbeschränkt). Sie können aus der Dropdownliste eine andere Speichereinheit auswählen.<br /><br /> **Angegebene Anzahl von Ereignissen (pro Typ) bei vollem Puffer beibehalten**. Aktivieren Sie diese Option, um eine angegebene Anzahl von Ereignissen jedes Typs im Puffer beizubehalten.<br /><br /> **Anzahl beizubehaltender Ereignisse (pro Typ)**. Geben Sie die gewünschte Anzahl von Ereignissen jedes Typs ein, die im Puffer gespeichert werden soll.|  
  
5.  Wenn Sie erweiterte Konfigurationseigenschaften festlegen möchten, wählen Sie im Abschnitt **Seite auswählen** die Option **Erweitert** aus.  
  
    > [!NOTE]  
    >  Klicken Sie erst auf **OK** , wenn Sie mit dem Erstellen der Ereignissitzung fertig sind.  
  
#### <a name="to-set-advanced-configurations"></a>So legen Sie erweiterte Konfigurationen fest  
  
1.  Wählen Sie im Dialogfeld für die neue Sitzung im Bereich **Seite auswählen** die Option **Erweitert**aus.  
  
2.  Gehen Sie auf der Seite **Erweitert** wie folgt vor, um die Optionen für den **Ereignisbeibehaltungsmodus** für die Ereignissitzung festzulegen:  
  
    1.  **Verlust einzelner Ereignisse**. Aktivieren Sie diese Option, um den Verlust eines einzelnen Ereignisses zuzulassen.  
  
    2.  **Verlust mehrerer Ereignisse**. Aktivieren Sie diese Option, um den Verlust mehrerer Ereignisse zuzulassen.  
  
    3.  **Kein Ereignisverlust**. Aktivieren Sie diese Option, wenn Sie den Verlust von Ereignissen verhindern möchten. Diese Option wird nicht empfohlen.  
  
        > [!NOTE]  
        >  Einige Ereignisse, z. B. das **sqlos.wait_info** -Ereignis, sind nicht kompatibel mit dem Ereignisbeibehaltungsmodus **Kein Ereignisverlust** .  
  
3.  Gehen Sie wie folgt vor, um die Optionen für die **Maximale Verteilungslatenzzeit** für die Ereignissitzung anzugeben:  
  
    1.  **In Sekunden**. Aktivieren Sie diese Option, um die maximale Verteilungslatenzzeit zu verlängern oder zu verkürzen. Geben Sie mithilfe der NACH-OBEN- und der NACH-UNTEN-TASTE die maximale Verteilungslatenzzeit in Sekunden an.  
  
    2.  **Unbegrenzt**. Aktivieren Sie diese Option, wenn Sie möchten, dass Ereignisse nur verteilt werden, wenn der Puffer voll ist.  
  
4.  Geben Sie im Feld **Max. Arbeitsspeichergröße** die maximale Speichergröße ein. Vorhandene Ereignisse werden gelöscht, wenn dieser Wert erreicht wird. Sie können aus der Dropdownliste eine andere Speichereinheit auswählen.  
  
5.  Geben Sie im Feld **Max. Ereignisgröße** die maximale Ereignisgröße für Ereignisse an, die aufgrund ihrer Größe nicht in **Max. Arbeitsspeichergröße**passen. Wenn Sie keine sehr großen Ereignisse sammeln, müssen Sie diese Option nicht konfigurieren. Sie können aus der Dropdownliste eine andere Speichereinheit auswählen.  
  
6.  Gehen Sie wie folgt vor, um die Optionen für den **Speicherpartitionsmodus** anzugeben:  
  
    1.  **Keiner**. Aktivieren Sie diese Option, wenn Sie keinen Speicherpartitionsmodus benötigen.  
  
    2.  **Pro Knoten**. Aktivieren Sie diese Option, wenn Sie den Speicher pro Knoten partitionieren möchten.  
  
    3.  **Pro CPU**. Aktivieren Sie diese Option, wenn Sie den Speicher pro CPU partitionieren möchten.  
  
 Um die Konfigurationsstandardwerte für die vorherigen Sitzungseigenschaften wiederherzustellen, klicken Sie auf **Standardwerte wiederherstellen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Sitzung für erweiterte Ereignisse mittels Abfrage-Editor](../../2014/database-engine/create-an-extended-events-session-using-query-editor.md)   
 [Erstellen einer Sitzung für erweiterte Ereignisse mithilfe des Assistenten &#40;Objekt-Explorer&#41;](../ssms/object/object-explorer.md)   
 [Schreiben einer Sitzung für erweiterte Ereignisse](../../2014/database-engine/script-an-extended-event-session.md)  
  
  