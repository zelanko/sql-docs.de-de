---
title: Konfigurieren der Sammlung von Verwendungs Daten für (PowerPivot für SharePoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 955ca6d6-9d5b-47a4-a87c-59bd23f1bf74
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b62bcdd7bb492a877572621bd7cfe9a3b150d04
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547522"
---
# <a name="configure-usage-data-collection-for-powerpivot-for-sharepoint"></a>Konfigurieren der Sammlung von Verwendungsdaten für PowerPivot für SharePoint
  Die Sammlung von Verwendungsdaten ist eine SharePoint-Funktion auf Farmebene. Dieses System wird durch PowerPivot für SharePoint verwendet und ergänzt, indem Berichte im PowerPivot-Management-Dashboard bereitgestellt werden, die die Verwendung von PowerPivot-Daten und -Diensten aufzeigen. Abhängig davon, wie SharePoint installiert wird, kann die Sammlung von Verwendungsdaten für die Farm deaktiviert sein. Ein Farmadministrator muss die Verwendungsprotokollierung aktivieren, damit operative Verwendungsdaten für die Darstellung im PowerPivot-Management-Dashboard generiert werden.  
  
 Informationen zu den Verwendungsdaten im PowerPivot-Management-Dashboard finden Sie unter [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
 **In diesem Thema:**  
  
 [Aktivieren der Sammlung von Verwendungsdaten und Auswählen der Ereignisse, durch die die Datensammlung ausgelöst wird](#events)  
  
 [Festlegen des Protokolldateispeicherorts](#configdb)  
  
 [Konfigurieren der Zeitgeberaufträge, die bei der Sammlung von Verwendungsdaten verwendet werden](#jobs)  
  
 [Begrenzen der Speicherdauer des Verwendungsdatenverlaufs](#confighist)  
  
 [Definieren schneller, mittlerer und langsamer Abfrageantwortkategorien für die Berichterstellung](#qrh)  
  
 [Festlegen der Häufigkeit, mit der Abfragestatistiken an das System für die Sammlung von Verwendungsdaten gemeldet werden](#ttr)  
  
 [Öffnen der Seite "PowerPivot-Dienstanwendung", um auf Konfigurationseinstellungen zuzugreifen](#openconfig)  
  
 [Standardkonfiguration für die Sammlung von PowerPivot-Verwendungsdaten](#defaultconfig)  
  
> [!IMPORTANT]  
>  Verwendungsdaten geben Einblick in die Daten- und Ressourcenzugriffe durch Benutzer, liefern aber keine zuverlässigen, dauerhaften Daten zu Servervorgängen und Benutzerzugriffen. Bei einem Serverneustart gehen Verwendungsdaten zu Ereignissen beispielsweise verloren und können nicht wiederhergestellt werden. Auch wenn die temporären Protokolldateien ihre maximale Größe erreichen, werden erst wieder neue Daten hinzugefügt, nachdem die Dateien gelöscht wurden. Falls Sie Überwachungsfunktion benötigen, sollten Sie die Verwendung von Funktionen für Workflow- und Inhaltstypen in Erwägung ziehen, die SharePoint zum Aufbau eines Überwachungssubsystems für die Farm bereitstellt. Weitere Informationen finden Sie in Produkt- und Communitydokumentationen im Web.  
  
##  <a name="enable-usage-data-collection-and-choose-events-that-trigger-data-collection"></a><a name="events"></a>Sammlung von Verwendungs Daten aktivieren und Ereignisse auswählen, die die Datensammlung auslöst  
 Konfigurieren Sie die Sammlung von Verwendungsdaten in der SharePoint-Zentraladministration.  
  
1.  Klicken Sie in der Zentraladministration auf **Überwachung**.  
  
2.  Klicken Sie im Abschnitt **Berichterstellung**auf **Verwendungs- und Integritätsdatenerfassung konfigurieren**.  
  
3.  Aktivieren Sie **Verwendungsdatenerfassung aktivieren**.  
  
4.  Aktivieren oder deaktivieren Sie im Abschnitt **Zu protokollierende Ereignisse** die entsprechenden Kontrollkästchen, um die folgenden Analysis Services-Ereignisse zu aktivieren oder zu deaktivieren:  
  
    |Ereignis|Beschreibung|  
    |-----------|-----------------|  
    |**PowerPivot-Verbindungen**|Das PowerPivot-Verbindungsereignis wird zum Überwachen von PowerPivot-Serververbindungen verwendet, die im Namen eines Benutzers hergestellt werden.|  
    |**Verwendung von PowerPivot-Datenladevorgängen**|Die Funktion PowerPivot Load Data Usage wird zum Überwachen von Anforderungen verwendet, durch die PowerPivot-Daten in den Serverarbeitsspeicher geladen werden. Ein Ladeereignis wird für PowerPivot-Datendateien generiert, die aus einer Inhaltsdatenbank oder dem Cache geladen werden.|  
    |**Verwendung von PowerPivot-Datenentladevorgängen**|Die Funktion PowerPivot Unload Data Usages wird zur Überwachung von Anfragen zum Entladen einer PowerPivot-Datenquelle nach einem bestimmten Zeitraum der Inaktivität verwendet. Das Zwischenspeichern einer PowerPivot-Datenquelle auf einem Datenträger wird als Entladeereignis gemeldet.|  
    |**Verwendung von PowerPivot-Abfragen**|Mithilfe der Funktion Verwendung von PowerPivot-Abfragen werden Abfrageverarbeitungszeiten für Daten überwacht, die in eine [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] -Instanz geladen werden.|  
  
    > [!NOTE]  
    >  Obwohl Serverzustands- und Datenaktualisierungsvorgänge auch Verwendungsdaten generieren, ist diesen Prozessen kein Ereignis zugeordnet.  
  
5.  Sie können auch den Speicherort der Protokolldatei aktualisieren. Weitere Informationen finden Sie im nächsten Abschnitt.  
  
6.  Klicken Sie auf **OK** , um die Änderungen zu speichern.  
  
7.  Optional können Sie angeben, ob alle Meldungen oder nur Fehler protokolliert werden. Weitere Informationen zum Einschränken von Ereignismeldungen finden Sie unter [Konfigurieren und Anzeigen von SharePoint-Protokolldateien und Diagnoseprotokollierung &#40;PowerPivot für SharePoint&#41;](configure-and-view-sharepoint-and-diagnostic-logging.md).  
  
##  <a name="set-log-file-location"></a><a name="configdb"></a>Festlegen des Protokolldatei Speicher Orts  
 PowerPivot-Verwendungsdaten werden anfänglich in Verwendungsprotokolldateien auf dem lokalen Server gespeichert und anschließend in regelmäßigen Abständen in die Datenbanken der PowerPivot-Dienstanwendung verschoben. Der Speicherort der Protokolldatei wird in der Zentraladministration festgelegt. Dies ist der Standardspeicherort:  
  
 `C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\logs`  
  
 Um diese Eigenschaften anzuzeigen oder zu ändern, verwenden Sie die Seite **Sammlung von Integritäts- und Verwendungsdaten** .  
  
1.  Klicken Sie auf der Homepage in der Zentraladministration auf **Überwachung**.  
  
2.  Klicken Sie im Abschnitt Überwachung auf **Verwendungs- und Integritätsdatenerfassung konfigurieren**.  
  
3.  Zeigen Sie unter Verwendungsdatensammlungseinstellungen den Speicherort, den Namen oder die maximale Größe der Datei an oder ändern Sie sie. Wenn Sie eine zu geringe Dateigröße angeben, erreicht die Datei schnell die maximale Größe und kann erst wieder neue Einträge aufnehmen, nachdem ihr Inhalt in die zentrale Datenbank für Verwendungsdaten verschoben wurde.  
  
##  <a name="configure-the-timer-jobs-used-in-usage-data-collection"></a><a name="jobs"></a>Konfigurieren der in der Sammlung von Verwendungs Daten verwendeten Zeit Geber Aufträge  
 Die Serverstatus-und Verwendungsdaten von PowerPivot werden durch zwei Zeitgeberaufträge an unterschiedliche Stellen im System zur Sammlung von Verwendungsdaten verschoben:  
  
-   Der Zeit Geber Auftrag "Microsoft SharePoint Foundation-Verwendungsdatenimport" verschiebt die Power Pivot-Verwendung in die Datenbank der Power Pivot-Dienst Anwendung.  
  
-   Der Zeit Geber Auftrag für die Verarbeitung des Power Pivot-Management-Dashboards stellt die Daten für die Power Pivot-Arbeitsmappe dar, die die Datenquelle für integrierte administrative Berichte ist.  
  
 Wenn Sie die Administratorberichte aktualisieren müssen, die häufiger im PowerPivot-Management-Dashboard angezeigt werden, führen Sie die folgenden Schritte aus.  
  
1.  Klicken Sie in der Zentraladministration auf **Überwachung**.  
  
2.  Klicken Sie auf **Zeitgeberaufträge** Klicken Sie im Abschnitt **Auftragsdefinitionen überprüfen** .  
  
3.  Klicken Sie auf **Import der Microsoft SharePoint Foundation-Verwendungsdaten**.  
  
4.  Klicken Sie auf **jetzt ausführen**. Wenn die Schaltfläche **Jetzt ausführen** deaktiviert ist, klicken Sie auf **Aktivieren** und dann auf **Jetzt ausführen**.  
  
5.  Klicken Sie in der Liste **Auftragsdefinitionen**auf den Management-Dashboard-Zeitgeberauftrag für die Verarbeitung von PowerPivot-Daten.  
  
6.  Klicken Sie auf **jetzt ausführen**.  
  
7.  Überprüfen Sie die Berichte, um die aktualisierten Daten anzuzeigen. Weitere Informationen finden Sie unter [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
##  <a name="limit-how-long-usage-data-history-is-stored"></a><a name="confighist"></a>Beschränken der Speicherung von Verwendungs Daten Verlauf  
 Der Verwendungsdatenverlauf wird für Ereignisse (Verbindungen, Lade-, Entladevorgänge und bedarfsgesteuerte Abfrageverarbeitung) sowie Datenaktualisierungen (geplante Datenverarbeitung) gespeichert. Obwohl Verwendungsdaten durch das SharePoint-System für die Sammlung von Verwendungsdaten gesammelt werden, werden die Berichtsdaten zur längerfristigen Speicherung in eine PowerPivot-Anwendungsdatenbank und eine Berichtsdatenbank verschoben. Die Einstellung für den Verwendungsdatenverlauf steuert, wie lange Verwendungsdaten in den PowerPivot-Anwendungsdatenbanken beibehalten werden. Für alle Typen gespeicherter Verwendungsdaten in einer PowerPivot-Dienstanwendungs-Datenbank gilt der gleiche Grenzwert.  
  
1.  [Öffnen Sie die Seite "PowerPivot-Dienstanwendung"](#openconfig).  
  
2.  Geben Sie im Abschnitt **Sammlung von Verwendungsdaten** unter **Verwendungsdatenverlauf**ein, wie viele Tage ein Datensatz der Datenaktualisierungsaktivitäten für die einzelnen Arbeitsmappen beibehalten werden soll.  
  
    -   Die Standardeinstellung beträgt 365 Tage.  
  
    -   0 gibt eine unbegrenzte Speicherdauer an, bei der Verwendungsdaten unbegrenzt beibehalten werden.  
  
    -   Alternativ können Sie auch einen Bereich zwischen 1 und 5000 angeben.  
  
     Indem Sie die Beibehaltungsdauer auf eine geringere Anzahl von Tagen festlegen, werden Daten gelöscht, die die neue Begrenzung überschreiten. Wenn Sie den Wert beispielsweise von 365 in 30 ändern, werden Verwendungsdaten für alle Verlaufsinformationen gelöscht, die mehr als 30 Tage zurückliegen. Es werden nur Daten der letzten 30 Tage beibehalten.  
  
     Die Daten werden tatsächlich gelöscht, wenn das nächste Ereignis eintritt. Die Begrenzung des Verwendungsdatenverlaufs wird nur überprüft, wenn das System ein Ereignis verarbeitet.  
  
3.  Klicken Sie auf **OK**.  
  
 Weitere Informationen dazu, wie Verwendungs Daten gesammelt und gespeichert werden, finden Sie unter [Sammlung von Power Pivot-Verwendungs Daten](power-pivot-usage-data-collection.md).  
  
##  <a name="define-fast-medium-and-slow-query-response-categories-for-reporting-purposes"></a><a name="qrh"></a>Definieren schneller, mittlerer und langsamer Abfrage Antwortkategorien für Berichts Zwecke  
 Die Leistung der Abfrageverarbeitung wird anhand vordefinierter Kategorien gemessen, in denen ein Anforderung/Antwort-Zyklus durch dessen Ausführungsdauer definiert wird. Die vordefinierten Kategorien lauten: Trivial, Schnell, Erwartet, Lange Ausführung und Überschritten. Jede an einen PowerPivot-Server übermittelte Anforderung wird abhängig von ihrer Ausführungsdauer in eine der Kategorien eingeteilt.  
  
 Die Abfrageantwortinformationen werden in Aktivitätsberichten verwendet. Alle Kategorien werden innerhalb der Berichte unterschiedlich behandelt, um die Leistungstrends des PowerPivot-Systems besser zu verdeutlichen. Beispielsweise werden triviale Anforderungen völlig ausgeschlossen, um unwesentliche Daten herauszufiltern und mithilfe der verbleibenden Kategorien aussagekräftigere Trends aufzuzeigen. Im Gegensatz dazu sind Statistiken zu Anforderungen mit langer oder überschrittener Ausführungszeit im Bericht gut erkennbar, damit Administratoren oder Arbeitsmappenbesitzer unverzüglich Korrekturmaßnahme ergreifen können.  
  
 Sie können keine Kategorien hinzufügen oder löschen, haben jedoch die Möglichkeit Ober- und Untergrenzen zu definieren, die bestimmen, wo eine Kategorie aufhört und die nächste beginnt. Wenn Ihre Organisation Vereinbarungen zum Servicelevel (SLAs, Service Level Agreements) zur Festlegung akzeptabler Serververfügbarkeits- und Leistungsebenen verwendet, können Sie diese Kategorien in Anpassung an die erstellte SLA optimieren.  
  
1.  [Öffnen Sie die Seite "PowerPivot-Dienstanwendung"](#openconfig).  
  
2.  Geben Sie im Abschnitt **Sammlung von Verwendungsdaten** unter **Obergrenze für triviale Antworten** einen Wert (in Millisekunden) ein, der angibt, in welcher Zeit eine triviale Antwort maximal abgeschlossen sein muss. Zu Anforderungen aus dieser Kategorie gehören normalerweise Ping-Signale an den Server, Sitzungseinleitungen und Metadatenabfragen. Der Standardwert beträgt 500 Millisekunden (oder eine halbe Sekunde).  
  
3.  Geben Sie unter Obergrenze für schnelle Anforderungen einen Wert (in Millisekunden) ein, der die Obergrenze zum Abschließen einer schnellen Anforderung festlegt. Zu Anforderungen aus dieser Kategorie gehören Abfragen sehr kleiner Datasets oder Metadatenserver großer Datasets. Der Standardwert beträgt 1000 Millisekunden (oder eine Sekunde).  
  
4.  Geben Sie unter **Obergrenze für erwartete Antwortdauer**einen Wert (in Millisekunden) ein, der die Obergrenze zum Abschließen einer Antwort in einem erwarteten oder durchschnittlichen Zeitrahmen festlegt. Zu Anforderungen aus dieser Kategorie gehört das Laden von Daten in einen Viewer. Der Standardwert beträgt 3000 Millisekunden (oder drei Sekunden).  
  
5.  Geben Sie unter **Obergrenze für lange Antworten**einen Wert (in Millisekunden) ein, der die Obergrenze zum Abschließen einer Antwort mit langer Ausführungsdauer festlegt. Anforderungen aus dieser Kategorie werden länger als erwartet, aber immer noch innerhalb eines akzeptablen Bereichs ausgeführt. Der Standardwert beträgt 10000 Millisekunden (oder zehn Sekunden).  
  
     Alle Anforderungen, die diese Grenze überschreiten, werden als *Überschritten*kategorisiert. Für *Überschritten*kann kein Schwellenwert konfiguriert werden. Er wird von der Obergrenze abgeleitet, die Sie unter Obergrenze für lange Anforderungen angeben. Anforderungen aus der Kategorie Überschritten werden länger ausgeführt als in einer von Ihnen definierten SLA zulässig.  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="specify-how-often-query-statistics-are-reported-to-the-usage-data-collection-system"></a><a name="ttr"></a>Angeben, wie oft Abfrage Statistiken an das System für die Sammlung von Verwendungs Daten gemeldet werden  
 Das Intervall für die Berichterstellung gibt an, wie häufig Abfragestatistiken im System für die Sammlung von Verwendungsdaten erfasst werden. Abfragestatistiken werden in einem Prozess gesammelt und in regelmäßigen Intervallen als einzelnes Ereignis gemeldet. Sie können das Intervall anpassen, um häufiger oder seltener eine Protokolldatei zu erstellen.  
  
1.  [Öffnen Sie die Seite "PowerPivot-Dienstanwendung"](#openconfig).  
  
2.  Geben Sie im Abschnitt **Sammlung von Verwendungsdaten** unter **Berichtsintervall für Abfragen**ein, nach wie vielen Sekunden der Server die Abfragestatistiken für alle Kategorien (trivial, schnell, erwartet, mit langer Ausführungsdauer und überschritten) als einzelnes Ereignis an das System für die Sammlung von Verwendungsdaten meldet.  
  
    -   Der Bereich liegt zwischen 1 und einer beliebigen positiven ganzen Zahl.  
  
    -   Der Standardwert beträgt 300 Sekunden (oder fünf Minuten). Dieser Wert wird für dynamische Farmumgebungen empfohlen, in denen eine Vielzahl von Anwendungen und Diensten ausgeführt wird.  
  
     Wenn Sie diesen Wert wesentlich heraufsetzen, können statistische Daten verloren gehen, bevor sie gemeldet werden. Ein Dienstneustart bewirkt z. B., dass Abfragestatistikdaten verloren gehen. Umgekehrt können die integrierten Aktivitätsberichte jedoch auch zu wenig Daten enthalten. In diesem Fall können Sie das Intervall verringern, damit Ereignisse für die Berichterstellung häufiger gemeldet werden.  
  
3.  Klicken Sie auf **OK**.  
  
##  <a name="open-the-powerpivot-service-application-page-to-access-configuration-settings"></a><a name="openconfig"></a>Öffnen der Seite "Power Pivot-Dienst Anwendung", um auf Konfigurationseinstellungen zuzugreifen  
 Nur Farm- oder Dienstadministratoren können Einstellungen für Dienstanwendungen ändern. Wenn Sie mehrere PowerPivot-Dienstanwendungen in der Farm definiert haben, muss jede Anwendung einzeln geändert werden.  
  
1.  Klicken Sie in der SharePoint-Zentraladministration unter **Anwendungsverwaltung**auf **Dienstanwendungen verwalten**.  
  
2.  Suchen Sie die PowerPivot-Dienstanwendung. Sie erkennen eine Dienstanwendung an ihrem Typ. Ein PowerPivot-Dienstanwendungstyp ist **PowerPivot-Dienstanwendung**.  
  
3.  Klicken Sie auf den Namen der PowerPivot-Dienstanwendung. Das PowerPivot-Management-Dashboard wird geöffnet.  
  
4.  Klicken Sie unter **Aktionen**auf **Einstellungen für Dienstanwendung konfigurieren**. Die Seite mit den Einstellungen der PowerPivot-Dienstanwendung wird geöffnet.  
  
##  <a name="the-default-configuration-for-powerpivot-usage-data-collection"></a><a name="defaultconfig"></a>Die Standardkonfiguration für die Sammlung von Power Pivot-Verwendungs Daten  
 Die Sammlung von Verwendungsdaten für PowerPivot-Dienstvorgänge kann mit Standardeinstellungen aktiviert werden, um sie in Anwendungen, die die Analysis Services-Integrationsfunktion unterstützen, direkt verfügbar zu machen. Die Standardeinstellungen umfassen Ereignisse, durch die die Sammlung von Verwendungsdaten ausgelöst wird, Grenzwerte für die Speicherdauer von Verwendungsdaten und Schwellenwerte zum Kategorisieren von Abfrageantwortzeiten.  
  
 Die folgende Tabelle enthält die Standardwerte für die Konfiguration der Sammlung von Verwendungsdaten.  
  
|Einstellung|Standardwert|type|Gültiger Bereich|  
|-------------|-------------------|----------|-----------------|  
|**Analysis Services-Verwendungsereignisse** (Verbinden, Laden, Entladen, Anforderungen)|\<enabled>|Boolesch|Diese Werte werden entweder aktiviert oder deaktiviert.|  
|**Berichtsintervall für Abfragen**|300 (in Sekunden)|Integer|Zwischen 1 und einer beliebigen positiven ganzen Zahl. Die Standardeinstellung ist 5 Minuten.|  
|**Verwendungsdatenverlauf**|365 (in Tagen)|Integer|0 gibt eine unbegrenzte Dauer an, Sie können jedoch auch eine Obergrenze festlegen, damit Verlaufsdaten ablaufen und automatisch gelöscht werden. Gültige Werte für eine begrenzte Beibehaltungsdauer betragen 1 bis 5000 (Tage).|  
|Obergrenze für triviale Antworten|500 (in Millisekunden)|Integer|Legt eine Obergrenze fest, die den Austausch einer trivialen Anforderung/Antwort definiert. Jede Anforderung, die innerhalb von 0 bis 500 Millisekunden abgeschlossen wird, ist eine triviale Anforderung und wird bei der Berichterstellung ignoriert.|  
|Obergrenze für schnelle Antworten|1000 (in Millisekunden)|Integer|Legt eine Obergrenze fest, die den Austausch einer schnellen Anforderung/Antwort definiert.|  
|Obergrenze für erwartete Antwortdauer|3000 (in Millisekunden)|Integer|Legt eine Obergrenze fest, die die erwartete Dauer für den Austausch einer Anforderung/Antwort definiert.|  
|Obergrenze für lange Antworten|10000 (in Millisekunden)|Integer|Legt eine Obergrenze fest, die den Austausch einer Anforderung/Antwort mit langer Laufzeit definiert. Alle Anforderungen, die diese Obergrenze überschreiten, gehören zur Kategorie Überschritten, die keinen oberen Schwellenwert aufweist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Die Konfigurations Einstellungs Referenz &#40;PowerPivot für SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Sammlung von PowerPivot-Verwendungsdaten](power-pivot-usage-data-collection.md)  
  
  
