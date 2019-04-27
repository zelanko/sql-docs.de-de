---
title: Details zu verwalteten Instanzen (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 6e51b7bb-a733-4852-8c33-7f4dbdf931c2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d2b01eceff763d554644065fdb5137695bd82f69
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62774342"
---
# <a name="managed-instance-details-sql-server-utility"></a>Details zu verwalteten Instanzen (SQL Server-Hilfsprogramm)
  Die Informationen in der Listenansicht Verwaltete Instanzen des Hilfsprogramm-Explorers enthalten Auslastungsdaten für einzelne Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Verlaufsdaten zur CPU-Auslastung sowie Details zur Speicherplatzauslastung auf Dateiebene. Zudem können Sie hier Richtlinienschwellenwerte anzeigen und aktualisieren. Richtlinienschwellenwerte können auf der Ebene von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanzen, per Computer, für Datenbank- und Protokolldateien sowie auf der Ebene von Speichervolumes gesteuert werden. Darüber hinaus können Sie Eigenschaftendetails für einzelne verwaltete Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]anzeigen.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 Listenansicht  
 Die Listenansicht im oberen Bereich enthält Daten zu einzelnen Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die zeilenweise nach ComputerName\InstanceName aufgeführt sind.  
  
 Zustandssymbole zeigen den Zusammenfassungsstatus für die einzelnen Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nach Auslastungskategorie an:  
  
-   Grünes Häkchen ![](../../2014/database-engine/media/well-utilized.gif "Normal ausgelastet"): Die Anzahl verwalteter Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], die gegen keine Richtlinien zur Ressourcenverwendung verstoßen. Die Ressourcen sind normal ausgelastet.  
  
-   Grüner Abwärtspfeil ![](../../2014/database-engine/media/utility-down-arrow.gif "Hilfsprogramm_Abwärtspfeil"): Die Ressourcen sind unterausgelastet.  
  
-   Roter Aufwärtspfeil ![](../../2014/database-engine/media/utility-up-arrow.gif "Hilfsprogramm_Aufwärtspfeil"): Die Ressourcen sind überausgelastet.  
  
 Die Abfolge der Spalten in der Listenansicht kann geändert werden, indem Sie sie nach links oder nach rechts ziehen. Sie können Spalten in der Listenansicht hinzufügen oder löschen, indem Sie mit der rechten Maustaste auf die Spaltenüberschriften klicken und die Spalten auswählen bzw. deren Auswahl aufheben. Darüber hinaus enthält das Kontextmenü Sortieroptionen. Die Sortierung kann auch aktiviert werden, indem Sie oben auf den Spaltennamen klicken.  
  
 Um auf Filteroptionen für die Listenansicht des Hilfsprogramms zuzugreifen, klicken Sie mit der rechten Maustaste im Navigationsbereich des Hilfsprogramm-Explorers auf den Knoten **Verwaltete Instanzen** und wählen **Filtern**aus. Nachdem die Filtereinstellungen implementiert wurden, hat der Knoten **Verwaltete Instanzen** im Hilfsprogramm-Explorer die Beschriftung **Verwaltete Instanzen (gefiltert)**. Weitere Informationen finden Sie unter [Filtereinstellungen &#40;Objekt-Explorer und Hilfsprogramm-Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).  
  
 Die folgenden Spalten enthalten standardmäßig Zustandsinformationen zu den einzelnen verwalteten Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Instanz-CPU: Zeigt den Zustand der Prozessorauslastung für diese Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]an. Der Zustand dieses Parameters wird anhand der Richtlinie zur CPU-Auslastung bestimmt, die für die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] festgelegt wurde, und anhand der Konfigurationseinstellung der Auswertungsrichtlinie für veränderliche Ressourcen. Weitere Informationen finden Sie unter [ Reduzieren von Informationsrauschen bei Richtlinien zur CPU-Auslastung &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
     Um den Verlauf der Prozessorauslastung für diese Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]anzuzeigen bzw. die Richtliniengrenzwerte einzusehen oder zu ändern, klicken Sie auf die Registerkarte **CPU-Auslastung** .  
  
-   Computer-CPU: Zeigt den Zustand der Prozessorauslastung für den Computer an. Der Zustand dieses Parameters wird anhand der Richtlinie zur CPU-Auslastung bestimmt, die für den Computer festgelegt wurde, und anhand der Konfigurationseinstellung der Auswertungsrichtlinie für veränderliche Ressourcen. Weitere Informationen finden Sie unter [ Reduzieren von Informationsrauschen bei Richtlinien zur CPU-Auslastung &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
     Um den Verlauf der Prozessorauslastung für diese Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]anzuzeigen bzw. die Richtliniengrenzwerte einzusehen oder zu ändern, klicken Sie auf die Registerkarte **CPU-Auslastung** .  
  
-   Dateispeicherplatz: Zeigt eine Zusammenfassung der Zustände der Dateispeicherplatzauslastung für alle Datenbanken an, die der ausgewählten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]angehören. Wenn der Zustand einer beliebigen Datenbank überausgelastet ist, wird der Zustand des Dateispeicherplatzes in der Listenansicht als überausgelastet angezeigt. Wenn der Zustand einer beliebigen Datenbank unterausgelastet und keine Datenbank überausgelastet ist, wird der Zustand des Dateispeicherplatzes in der Listenansicht als unterausgelastet angezeigt. Andernfalls wird der Zustand des Dateispeicherplatzes in der Listenansicht als normal angezeigt. Um die Richtliniengrenzwerte anzuzeigen oder zu ändern, klicken Sie auf die Registerkarte **Speicherauslastung** .  
  
-   Volumespeicherplatz – Zeigt eine Zusammenfassung der Zustände der Volumespeicherplatzauslastung für alle Volumes mit Datenbanken an, die der ausgewählten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]angehören. Wenn der Zustand eines beliebigen Volumes überausgelastet ist, dann wird der Zustand des Volumespeicherplatzes in der Listenansicht als überausgelastet angezeigt. Wenn der Zustand eines beliebigen Volumes unterausgelastet und kein Volume überausgelastet ist, wird der Zustand des Volumespeicherplatzes in der Listenansicht als unterausgelastet angezeigt. Andernfalls wird der Zustand des Volumespeicherplatzes in der Listenansicht als normal angezeigt. Um die Richtliniengrenzwerte anzuzeigen oder zu ändern, klicken Sie auf die Registerkarte **Speicherauslastung** .  
  
-   Richtlinientyp – Gibt an, ob Standardrichtlinien (vom Typ "Global") oder benutzerdefinierte Richtlinien (vom Typ "Überschreibung") für die verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]wirksam sind.  
  
 Weitere Spalten können über das Kontextmenü im Spaltenüberschriftenbereich der Listenansicht angezeigt werden:  
  
-   Prozessorname:  
  
-   Prozessorgeschwindigkeit (MHz):  
  
-   Prozessoranzahl:  
  
-   Physischer Speicher (MB):  
  
-   Betriebssystemversion:  
  
-   SQL Server-Version:  
  
-   SQL Server-Edition:  
  
-   Gruppiert: ("True" oder "false")  
  
-   Sicherungsverzeichnis:  
  
-   Sortierung:  
  
-   Groß-/Kleinschreibung beachten: ("True" oder "false")  
  
-   Sprache:  
  
-   Zuletzt gemeldet: In dieser Spalte wird UCP lokale Datum und Uhrzeit, die mit dem Datentyp "DateTime". Weitere Informationen finden Sie unter dem Thema [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) in der SQL Server-Onlinedokumentation. Beachten Sie bei Verwendung des Hilfsprogramm-Objektmodells, dass SSMS den datetimeoffset-Datentyp verwendet. Weitere Informationen finden Sie unter dem Thema [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) in der SQL Server-Onlinedokumentation.  
  
 Registerkarte CPU-Auslastung  
 Die Registerkarte CPU-Auslastung enthält Vergleichsdiagramme mit Verlaufsdaten für die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz und die CPU-Auslastung des Computers.  
  
 Das Diagramm enthält Verlaufsdaten zur Prozessorauslastung. Diese beziehen sich auf den Zeitraum, der mithilfe der Optionsfelder auf der rechten Seite des Anzeigebereichs festgelegt wurde. Um das Anzeigeintervall zu ändern und das Dataset zu aktualisieren, aktivieren Sie ein Optionsfeld aus der Liste.  
  
 Folgende Intervalloptionen stehen zur Verfügung:  
  
-   1 Tag, in Intervallen von 15 Minuten  
  
-   1 Woche, in Intervallen von 1 Tag  
  
-   1 Monat, in Intervallen von 1 Woche  
  
-   1 Jahr, in Intervallen von 1 Monat  
  
 Registerkarte Speicherauslastung  
 Die Registerkarte Speicherauslastung verfügt über eine Strukturansicht, in der Details zur Speicherauslastung angezeigt werden. Die Zeitangaben zeigen das lokale Datum und die lokale Uhrzeit des UCPs unter Verwendung des datetime-Datentyps an. Weitere Informationen finden Sie unter dem Thema [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) in der SQL Server-Onlinedokumentation. Beachten Sie bei Verwendung des Hilfsprogramm-Objektmodells, dass SSMS den datetimeoffset-Datentyp verwendet. Weitere Informationen finden Sie unter dem Thema [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) in der SQL Server-Onlinedokumentation.  
  
 Die Informationen in der Anzeige können nach Datenbank oder nach Volume gruppiert werden. Um die Datenbankstrukturansicht zu verwenden, aktivieren Sie im Auswahlbereich **Dateien gruppieren nach** das Optionsfeld **Datenbank** . Um den Status der Speicherauslastung für einzelne Datenbankdateien anzuzeigen, klicken Sie neben einem Datenbanknamen in der Strukturansicht auf das Pluszeichen. Die aufgeführten Datenbankdateien enthalten alle System- und Benutzerdatenbanken, die der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] angehören, die Sie in der Listenansicht ausgewählt haben.  
  
 Die Baumstruktur entspricht der Speicherhierarchie. Der Stammknoten in der Strukturansicht entspricht der Datenbank. Die nächste Ebene der Strukturansicht enthält einen Dateigruppenknoten oder Knoten, die zur Datenbank gehören, sowie einen Protokolldateiknoten für die Protokolle, die der Datenbank zugeordnet sind. Die nächste Ebene enthält die Datendateien, die zur Dateigruppe gehören.  
  
 Welche Daten im Diagramm mit Verlaufsdaten zur Speicherauslastung angezeigt werden, hängt von dem Knoten ab, der in der Strukturansicht ausgewählt ist:  
  
-   Wählen Sie den Dateigruppenknoten aus, um den Dateispeicherplatz, der von allen Datendateien der ausgewählten Dateigruppe belegt wird, in einem Diagramm darzustellen.  
  
-   Wählen Sie den Protokolldateiknoten aus, um den Dateispeicherplatz, der von allen Protokolldateien der ausgewählten Datenbank belegt wird, in einem Diagramm darzustellen.  
  
-   Wählen Sie den Datenbankknoten aus, um ein Diagramm anzuzeigen, in dem der Dateispeicherplatz addiert wird, der von allen Datendateien und Protokolldateien belegt wird, die der ausgewählten Datenbank angehören.  
  
 Zustandssymbole liefern auf einen Blick Statusinformationen zu Datenbankdateien, Dateigruppen und Protokolldateien:  
  
 Datenbanken:  
  
-   Grünes Häkchen – Die Zustände aller Dateigruppen und Protokolldateien sind weder überausgelastet noch unterausgelastet.  
  
-   Grüner Pfeil nach unten – Der Zustand mindestens einer Dateigruppe oder Protokolldatei ist unterausgelastet, und keine Zustände sind überausgelastet.  
  
-   Roter Pfeil nach oben – Der Zustand mindestens einer Dateigruppe oder Protokolldatei ist überausgelastet.  
  
 Dateigruppen und Protokolldateien:  
  
-   Grünes Häkchen – Die Auslastung des Dateispeicherplatzes für alle Dateien in der Dateigruppe ist weder überausgelastet noch unterausgelastet.  
  
-   Grüner Pfeil nach unten – Die Auslastung des Dateispeicherplatzes für mindestens eine Datei in der Dateigruppe ist unterausgelastet, und keine Dateien in der Dateigruppe sind überausgelastet.  
  
-   Roter Pfeil nach oben – Die Auslastung des Dateispeicherplatzes für alle Datendateien in der Dateigruppe ist überausgelastet.  
  
 Um die Dateien nach Volume anzuzeigen, aktivieren Sie im Auswahlbereich **Dateien gruppieren nach** das Optionsfeld **Volume** . Im Diagramm mit Verlaufsdaten zur Speicherplatzauslastung wird der Dateispeicherplatz dargestellt, der von allen Datendateien und Protokolldateien auf dem Speichervolume belegt wird. Erweitern Sie die Struktur, um Details zu einzelnen Datenbankdatendateien und Protokolldateien anzuzeigen.  
  
 Statussymbole werden verwendet, um den Status der einzelnen Volumes anzuzeigen:  
  
-   Grünes Häkchen – Die Ressourcen sind normal ausgelastet.  
  
-   Grüner Pfeil nach unten – Die Ressourcen sind unterausgelastet.  
  
-   Roter Pfeil nach oben – Die Ressourcen sind überausgelastet.  
  
 Das Messgerät neben den einzelnen Dateinamen auf der Registerkarte Speicherauslastung zeigt die Speicherplatzkapazität an, die von der Datei relativ zur effektiven Kapazität der Datei belegt wird. Der neben dem Messgerät angezeigte Prozentwert gibt das Verhältnis des von der Datei belegten Speicherplatzes relativ zur effektiven Kapazität der Datei an. QuickInfos liefern Informationen, die zur Berechnung der Prozentwerte für jedes Volume und jede Datei im Vergleich zu deren effektiven Kapazität verwendet werden.  
  
 Wenn die Datei nicht für die automatische Vergrößerung konfiguriert ist, entspricht die effektive Kapazität der Speicherplatzkapazität, die der Datei zugewiesen ist. Wenn die Datei für die automatische Vergrößerung konfiguriert ist, entspricht die effektive Kapazität der Summe aus dem Speicherplatz, der derzeit von der Datei belegt wird, und dem freien Speicherplatz, der derzeit auf dem Volume verfügbar ist.  
  
 Richtlinien zur Speicherauslastung können für Datendateien und Protokolldateien konfiguriert werden. Um die Schwellenwerte der Richtlinien zur Speicherauslastung anzuzeigen oder zu ändern, klicken Sie auf den Link **Dateirichtlinie** unten im Bereich Speicherauslastung. Um die Schwellenwerte der Richtlinien zur Speicherauslastung für ein Speichervolume anzuzeigen oder zu ändern, klicken Sie auf den Link **Volumerichtlinie** unten im Bereich Speicherauslastung.  
  
 Um die Schwellenwerte für Standardrichtlinien zu überschreiben, klicken Sie auf das Optionsfeld **Standardrichtlinie überschreiben**, geben obere und untere Grenzwerte ein und klicken dann auf **OK**.  
  
 Weitere Informationen zum Ändern der Toleranz für Richtlinienverstöße finden Sie unter [Reduzieren von Informationsrauschen bei Richtlinien zur CPU-Auslastung &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
 Registerkarte Eigenschaftendetails  
 Die für Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aufgeführten Eigenschaftendetails umfassen die folgenden Kategorien:  
  
-   Prozessorname:  
  
-   Prozessorgeschwindigkeit (MHz):  
  
-   Prozessoranzahl:  
  
-   Physischer Speicher (MB):  
  
-   Betriebssystemversion:  
  
-   SQL Server-Version:  
  
-   SQL Server-Edition:  
  
-   Gruppiert: ("True" oder "false")  
  
-   Sicherungsverzeichnis:  
  
-   Sortierung:  
  
-   Groß-/Kleinschreibung beachten: ("True" oder "false")  
  
-   Sprache:  
  
## <a name="see-also"></a>Siehe auch  
 [Details zu bereitgestellten Datenebenenanwendungen &#40;SQL Server-Hilfsprogramm&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md)   
 [Dashboard des Hilfsprogramms &#40;SQL Server-Hilfsprogramm&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md)   
 [Überwachen von SQL Server-Instanzen im SQL Server-Hilfsprogramm](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)   
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Problembehandlung beim SQL Server-Hilfsprogramm](../../2014/database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
