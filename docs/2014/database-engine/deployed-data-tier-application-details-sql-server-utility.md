---
title: Details zu bereitgestellten Datenebenenanwendungen (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.dac.details.F1
helpviewer_keywords:
- utility, management
- Utility
- SQL Server Utility [SQL Server]
- data-tier application [SQL Server], utility details
- Multi-server management [SQL Server]
ms.assetid: 79c41dd9-abcb-434e-9326-00a341d5c867
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ca9186b93e96c60e1c5128e385b5b77d5f2b94e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62754093"
---
# <a name="deployed-data-tier-application-details-sql-server-utility"></a>Details zu bereitgestellten Datenebenenanwendungen (SQL Server-Hilfsprogramm)
  Die Informationen in der Listenansicht Bereitgestellte Datenebenenanwendungen des Hilfsprogramm-Explorers enthalten Auslastungsdaten für einzelne Datenebenenanwendungen, Verlaufsdaten zur CPU-Auslastung und Details zur Speicherplatzauslastung auf Dateiebene sowie die Möglichkeit, Richtlinienschwellenwerte anzuzeigen und zu aktualisieren. Richtlinienschwellenwerte können auf der Ebene der Datenebenenanwendung für die CPU-Auslastung sowie Datenbankdateien und Protokolldateien gesteuert werden. Sie können auch Eigenschaftendetails für einzelne Datenebenenanwendungen anzeigen.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 Listenansicht  
 In der Listenansicht im oberen Bereich werden Daten zu einzelnen Datenebenenanwendungen angezeigt. Zustandssymbole zeigen den Zusammenfassungsstatus für die einzelnen Datenebenenanwendungen nach Auslastungskategorie an:  
  
-   Grünes Häkchen – ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") : Anzahl der Datenebenenanwendungen, die nicht gegen Richtlinien zur Ressourcennutzung verstoßen. Die Ressourcen sind normal ausgelastet.  
  
-   Grüner Pfeil nach unten – ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") : Die Ressourcen sind unterausgelastet.  
  
-   Roter Pfeil nach oben – ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") : Die Ressourcen sind überausgelastet.  
  
 Die Abfolge der Spalten in der Listenansicht kann geändert werden, indem Sie sie nach links oder nach rechts ziehen. Sie können Spalten in der Listenansicht hinzufügen oder löschen, indem Sie mit der rechten Maustaste auf die Spaltenüberschriften klicken und die Spalten auswählen bzw. deren Auswahl aufheben. Darüber hinaus enthält das Kontextmenü Sortieroptionen. Die Sortierung kann auch aktiviert werden, indem Sie oben auf den Spaltennamen klicken.  
  
 Um auf Filteroptionen für die Listenansicht des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramms zuzugreifen, klicken Sie mit der rechten Maustaste auf den Knoten **Bereitgestellte Datenebenenanwendungen** im Navigationsbereich des Hilfsprogramm-Explorers, und wählen Sie **Filtern**aus. Nachdem die Filtereinstellungen implementiert wurden, hat der Knoten **Bereitgestellte Datenebenenanwendungen** im Hilfsprogramm-Explorer die Beschriftung **Bereitgestellte Datenebenenanwendungen (gefiltert)**. Weitere Informationen finden Sie unter [Filtereinstellungen &#40;Objekt-Explorer und Hilfsprogramm-Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).  
  
 In den folgenden Spalten werden standardmäßig Zustandsinformationen zu den einzelnen Datenebenenanwendungen angezeigt.  
  
-   Name – Der Name der Datenebenenanwendung.  
  
-   Anwendungs-CPU – Zeigt den Zustand der Prozessorauslastung für diese Datenebenenanwendung an. Der Zustand dieses Parameters wird anhand der Richtlinie zur CPU-Auslastung bestimmt, die für die Datenebenenanwendung festgelegt wurde, und anhand der Konfigurationseinstellung der Auswertungsrichtlinie für veränderliche Ressourcen. Weitere Informationen finden Sie unter [ Reduzieren von Informationsrauschen bei Richtlinien zur CPU-Auslastung &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
     Um den Verlauf der Prozessorauslastung für diese Datenebenenanwendung anzuzeigen bzw. die Richtliniengrenzwerte einzusehen oder zu ändern, klicken Sie auf die Registerkarte **CPU-Auslastung**.  
  
-   Computer-CPU: Zeigt den Zustand der Prozessorauslastung für den Computer an. Der Zustand dieses Parameters wird anhand der Richtlinie zur CPU-Auslastung bestimmt, die für den Computer festgelegt wurde, und anhand der Konfigurationseinstellung der Auswertungsrichtlinie für veränderliche Ressourcen. Weitere Informationen finden Sie unter [ Reduzieren von Informationsrauschen bei Richtlinien zur CPU-Auslastung &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
     Um den Verlauf der Prozessorauslastung für diese Datenebenenanwendung anzuzeigen bzw. die Richtliniengrenzwerte einzusehen oder zu ändern, klicken Sie auf die Registerkarte **CPU-Auslastung**.  
  
-   Dateispeicherplatz – Zeigt eine Zusammenfassung der Zustände der Dateispeicherplatzauslastung für die einzelnen Datenebenenanwendungen an.  
  
    -   Grünes Häkchen – Die Zustände für alle Dateigruppen und die Protokolldateigruppe sind weder überausgelastet noch unterausgelastet.  
  
    -   Grüner Pfeil nach unten – Der Zustand für mindestens eine Dateigruppe oder Protokolldateigruppe ist unterausgelastet, und keine Dateigruppe oder Protokolldateigruppe ist überausgelastet.  
  
    -   Roter Pfeil nach oben – Der Integritätsstatus für mindestens eine Dateigruppe oder die Protokolldateigruppe ist überausgelastet. Wenn eine Datenbank den Status „emergency“ (Notfall) aufweist, wird für den Integritätsstatus der überausgelastete Protokolldateispeicherplatz angezeigt.  
  
     Um die Richtliniengrenzwerte für den Dateispeicherplatz anzuzeigen oder zu ändern, klicken Sie auf die Registerkarte **Speicherauslastung** .  
  
-   Volumespeicherplatz – Zeigt eine Zusammenfassung der Zustände der Volumespeicherplatzauslastung für alle Volumes mit Datenbanken an, die der ausgewählten Datenebenenanwendung angehören. Wenn der Zustand eines beliebigen Volumes überausgelastet ist, dann wird der Zustand des Volumespeicherplatzes in der Listenansicht als überausgelastet angezeigt. Wenn der Zustand eines beliebigen Volumes unterausgelastet und kein Volume überausgelastet ist, wird der Zustand des Volumespeicherplatzes in der Listenansicht als unterausgelastet angezeigt. Andernfalls wird der Zustand des Volumespeicherplatzes in der Listenansicht als normal angezeigt. Um die Richtliniengrenzwerte anzuzeigen oder zu ändern, klicken Sie auf die Registerkarte **Speicherauslastung** .  
  
-   Richtlinientyp – Gibt an, ob Standardrichtlinien (vom Typ "Global") oder benutzerdefinierte Richtlinien (vom Typ "Überschreibung") für die Datenebenenanwendung wirksam sind.  
  
-   Instanzname – Gibt den Namen der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] an, die die Datenebenenanwendung hostet.  
  
 Weitere Spalten können über das Kontextmenü im Spaltenüberschriftenbereich der Listenansicht angezeigt werden:  
  
-   Datenbankname  
  
-   Bereitstellungsdatum  
  
-   Vertrauenswürdig: (True oder False)  
  
-   Sortierreihenfolge  
  
-   Kompatibilitätsgrad: (z. B. Version100)  
  
-   Verschlüsselung aktiviert: (True oder False)  
  
-   Wiederherstellungsmodell: (SIMPLE, FULL oder BULK_LOGGED)  
  
-   Letzter Berichtszeitpunkt: Diese Spalte zeigt das lokale Datum und die lokale Uhrzeit des UCPs unter Verwendung des datetime-Datentyps an. Weitere Informationen finden Sie unter dem Thema [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) in der SQL Server-Onlinedokumentation. Beachten Sie bei Verwendung des Hilfsprogramm-Objektmodells, dass SSMS den datetimeoffset-Datentyp verwendet. Weitere Informationen finden Sie unter dem Thema [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) in der SQL Server-Onlinedokumentation.  
  
 Registerkarte CPU-Auslastung  
 Die Registerkarte CPU-Auslastung enthält Vergleichsdiagramme mit Verlaufsdaten für die Datenebenenanwendung und die CPU-Auslastung des Computers.  
  
 Das Diagramm enthält Verlaufsdaten zur Prozessorauslastung. Diese beziehen sich auf den Zeitraum, der mithilfe der Optionsfelder auf der rechten Seite des Anzeigebereichs festgelegt wurde. Um das Anzeigeintervall zu ändern und das Dataset zu aktualisieren, aktivieren Sie ein Optionsfeld aus der Liste.  
  
 Folgende Intervalloptionen stehen zur Verfügung:  
  
-   1 Tag, in Intervallen von 15 Minuten  
  
-   1 Woche, in Intervallen von 1 Tag  
  
-   1 Monat, in Intervallen von 1 Woche  
  
-   1 Jahr, in Intervallen von 1 Monat  
  
 Registerkarte Speicherauslastung  
 Die Registerkarte Speicherauslastung verfügt über eine Strukturansicht, in der Details zur Speicherauslastung für Datenbankdateien und Protokolldateien angezeigt werden, die zu der in der Listenansicht ausgewählten Datenebenenanwendung gehören. Die Zeitangaben zeigen das lokale Datum und die lokale Uhrzeit des UCPs unter Verwendung des datetime-Datentyps an. Weitere Informationen finden Sie unter dem Thema [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) in der SQL Server-Onlinedokumentation. Beachten Sie bei Verwendung des Hilfsprogramm-Objektmodells, dass SSMS den datetimeoffset-Datentyp verwendet. Weitere Informationen finden Sie unter dem Thema [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) in der SQL Server-Onlinedokumentation.  
  
 Die Anzeige kann nach Dateigruppe oder nach Volume gruppiert werden. Um die Strukturansicht für Dateigruppen zu verwenden, aktivieren Sie im Bereich **Dateien gruppieren nach** das Optionsfeld **Dateigruppe** .  
  
 Welche Daten im Diagramm mit Verlaufsdaten zur Speicherauslastung angezeigt werden, hängt von dem Knoten ab, der in der Strukturansicht ausgewählt ist:  
  
-   Wählen Sie den Dateigruppenknoten aus, um den Dateispeicherplatz, der von allen Datendateien der ausgewählten Dateigruppe belegt wird, in einem Diagramm darzustellen.  
  
-   Wählen Sie den Protokolldateiknoten aus, um den Dateispeicherplatz, der von allen Protokolldateien der ausgewählten Datenbank belegt wird, in einem Diagramm darzustellen.  
  
-   Wählen Sie den Datenbankknoten aus, um ein Diagramm anzuzeigen, in dem der Dateispeicherplatz addiert wird, der von allen Datendateien und Protokolldateien belegt wird, die der ausgewählten Datenbank angehören.  
  
 Um den Status der Speicherauslastung für einzelne Dateien anzuzeigen, klicken Sie neben einem Dateinamen in der Strukturansicht auf das Pluszeichen.  
  
 Zustandssymbole liefern auf einen Blick Statusinformationen zu den einzelnen Dateigruppen in Relation zu Richtlinienschwellenwerten:  
  
-   Grünes Häkchen – Die Auslastung des Dateispeicherplatzes für mindestens eine Datendatei in der Dateigruppe ist weder überausgelastet noch unterausgelastet.  
  
-   Grüner Pfeil nach unten – Die Auslastung des Dateispeicherplatzes für mindestens eine Datendatei in der Dateigruppe ist unterausgelastet, und keine Dateien in der Dateigruppe sind überausgelastet.  
  
-   Roter Pfeil nach oben – Die Auslastung des Dateispeicherplatzes für alle Datendateien in der Dateigruppe ist überausgelastet. Wenn eine Datenbank den Status „emergency“ (Notfall) aufweist, wird für den Integritätsstatus der überausgelastete Protokolldateispeicherplatz angezeigt.  
  
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
 Die für Datenebenenanwendungen aufgeführten Eigenschaftendetails umfassen die folgenden Kategorien:  
  
-   Datenbankname  
  
-   Bereitstellungsdatum  
  
-   Vertrauenswürdig: (True oder False)  
  
-   Sortierreihenfolge  
  
-   Kompatibilitätsgrad: (z. B. Version100)  
  
-   Verschlüsselung aktiviert: (True oder False)  
  
-   Wiederherstellungsmodell: (SIMPLE, FULL oder BULK_LOGGED)  
  
-   Letzter Berichtszeitpunkt: Diese Spalte zeigt das lokale Datum und die lokale Uhrzeit des UCPs unter Verwendung des datetime-Datentyps an. Weitere Informationen finden Sie unter dem Thema [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) in der SQL Server-Onlinedokumentation. Beachten Sie bei Verwendung des Hilfsprogramm-Objektmodells, dass SSMS den datetimeoffset-Datentyp verwendet. Weitere Informationen finden Sie unter dem Thema [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltete Instanz Details &#40;SQL Server-Hilfsprogramm&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md)   
 [SQL Server-Hilfsprogramm des Utility-Dashboards &#40;&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md)   
 [Überwachen von Instanzen von SQL Server im SQL Server-Hilfsprogramm](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)   
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
