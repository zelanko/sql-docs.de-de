---
title: Berichtsserverdienst-Ablaufverfolgungsprotokoll | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- logs [Reporting Services], trace
- traces [Reporting Services]
- system information [Reporting Services]
- versions [Reporting Services]
ms.assetid: 2fde08b2-137d-4f4b-88e5-216030216e0d
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 1c04e3d642b267660b8527502a248a386c8ba93d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56010671"
---
# <a name="report-server-service-trace-log"></a>Berichtsserverdienst-Ablaufverfolgungsprotokoll
  Das [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Berichtsserver-Ablaufverfolgungsprotokoll ist eine ASCII-Textdatei, die detaillierte Informationen für Berichtsserver-Dienstvorgänge enthält, einschließlich vom Report Server-Webdienst, vom Berichts-Manager und von der Hintergrundverarbeitung ausgeführte Vorgänge. In den Ablaufverfolgungsprotokollen sind redundante Informationen gespeichert, die in anderen Protokolldateien aufgezeichnet werden, sowie zusätzliche Informationen, die anderweitig nicht verfügbar sind. Ablaufverfolgungsinformationen können beispielsweise zum Debuggen einer Anwendung, die einen Berichtsserver enthält, oder zum Analysieren eines bestimmten Problems, das ins Ereignis- oder Ausführungsprotokoll geschrieben wurde, nützlich sein.  
  
> [!NOTE]  
>  In vorherigen Versionen waren mehrere Ablaufverfolgungsprotokolldateien vorhanden, eine pro Anwendung. Die folgenden Dateien sind veraltet und werden in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen nicht mehr erstellt: ReportServerWebApp_*\<Zeitstempel >* log, ReportServer_*\<Zeitstempel >*.log und ReportServerService_main_ *\< Timestamp >*. Log.  
  
 **In diesem Thema:**  
  
-   [Wo befinden sich die Berichtsserver-Protokolldateien?](#bkmk_view_log)  
  
-   [Konfigurationseinstellungen für die Ablaufverfolgung](#bkmk_trace_configuration_settings)  
  
-   [Hinzufügen von benutzerdefinierten Konfigurationseinstellung zum Angeben eines Speicherorts der Dump-Datei](#bkmk_add_custom)  
  
-   [Protokolldateifelder](#bkmk_log_file_fields)  
  
##  <a name="bkmk_view_log"></a> Wo befinden sich die Protokolldateien des Berichtsservers?  
 Die Ablaufverfolgungs-Protokolldateien sind `ReportServerService_<timestamp>.log` und befinden sich im folgenden Ordner:  
  
 `C:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles`  
  
 Das Ablaufverfolgungsprotokoll wird täglich erstellt, beginnend mit dem ersten Eintrag nach Mitternacht (lokale Zeit) sowie nach Neustart des Diensts. Der Timestamp basiert auf der koordinierten Weltzeit (UTC). Die Datei liegt im Format EN-US vor. Standardmäßig sind Ablaufverfolgungsprotokolle auf 32 Megabyte begrenzt und werden nach 14 Tagen gelöscht.  
  
 Sehen Sie sich ein kurzes Video an, das die Verwendung von Microsoft Power Query zum Anzeigen von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Protokolldateien veranschaulicht.  
  
 ![Video über Power Query und SSRS-Protokolle](../media/generic-video-thumbnail.png "Video über Power Query und SSRS-Protokolle")  
  
##  <a name="bkmk_trace_configuration_settings"></a> Konfigurationseinstellungen für die Ablaufverfolgung  
 Das Verhalten der Ablaufverfolgungsprotokolle wird in der Konfigurationsdatei **ReportingServicesrService.exe.config**verwaltet. Die Konfigurationsdatei befindet sich unter folgendem Ordnerpfad:  
  
 `\Program Files\Microsoft SQL Server\MSRS12.<instance name>\Reporting Services\ReportServer\bin`. installiert haben.  
  
 Im folgenden Beispiel wird die XML-Struktur der `RStrace`-Einstellungen veranschaulicht. Der Wert für `DefaultTraceSwitch` bestimmt die Art der Informationen, die dem Protokoll hinzugefügt werden. Mit Ausnahme des `Components`-Attributs sind die Werte für `RStrace` in den Konfigurationsdateien identisch.  
  
```  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
```  
  
 Die folgende Tabelle enthält Informationen zu den einzelnen Einstellungen.  
  
|Einstellung|Description|  
|-------------|-----------------|  
|`RStrace`|Gibt Namespaces an, die für Fehler und für die Ablaufverfolgung verwendet werden.|  
|`DefaultTraceSwitch`|Gibt die Ebene der Informationen an, die im Ablaufverfolgungsprotokoll ReportServerService aufgezeichnet werden. Jede Ebene enthält jeweils die Informationen aller niedrigerer Ebenen. Das Deaktivieren der Ablaufverfolgung wird nicht empfohlen. Gültige Werte sind:<br /><br /> 0= Deaktiviert die Ablaufverfolgung. Das ReportServerService-Protokoll ist standardmäßig aktiviert. Um diese Funktion zu deaktivieren, legen Sie die Ablaufverfolgungsebene auf 0 fest.<br /><br /> 1= Ausnahmen und Neustarts<br /><br /> 2= Ausnahmen, Neustarts, Warnungen<br /><br /> 3= Ausnahmen, Neustarts, Warnungen, Statusmeldungen (Standard)<br /><br /> 4= Ausführlicher Modus|  
|**FileName**|Gibt den ersten Teil des Protokolldateinamens an. Der Wert von `Prefix` ergänzt den restlichen Namen.|  
|**FileSizeLimitMb**|Gibt eine Obergrenze für die Größe des Ablaufverfolgungsprotokolls an. Die Datei wird in Megabytes gemessen. Gültige Werte sind 0 bis zu einer maximalen ganzen Zahl. Der Standardwert ist 32. Wenn Sie 0 oder eine negative Zahl angeben, wird dieser Wert vom Berichtsserver wie der Wert 1 behandelt.<br /><br /> Sie können die Dateigröße beeinflussen, indem Sie Ablaufverfolgungsebenen festlegen (0 bis 4), um zu steuern, wie viel Inhalt aufgezeichnet wird. Zudem können Sie angeben, welche Bestandteile verfolgt werden. Wenn das Maximum der Protokolldatei vor dem Ablaufdatum von 14 Tagen erreicht wird, werden ältere Einträge durch neuere Einträge ersetzt.|  
|**KeepFilesForDays**|Gibt die Anzahl von Tagen an, nach der eine Ablaufverfolgungs-Protokolldatei gelöscht wird. Gültige Werte sind 0 bis zu einer maximalen ganzen Zahl. Der Standardwert ist 14. Wenn Sie 0 oder eine negative Zahl angeben, wird dieser Wert vom Berichtsserver wie der Wert 1 behandelt.|  
|`Prefix`|Gibt einen generierten Wert an, der die Protokollinstanzen voneinander unterscheidet. Standardmäßig werden Timestampwerte an die Dateinamen von Ablaufverfolgungsprotokollen angehängt. Dieser Wert wird auf "tid, time " festgelegt. Ändern Sie diese Einstellung nicht.|  
|**TraceListeners**|Gibt die Zieladresse für die Ausgabe des Inhalts von Ablaufverfolgungsprotokollen an. Sie können mehrere durch Trennzeichen getrennte Ziele angeben. Gültige Werte sind:<br /><br /> DebugWindow<br /><br /> File (Standard)<br /><br /> StdOut|  
|**TraceFileMode**|Gibt an, ob Ablaufverfolgungsprotokolle Daten für einen Zeitraum von 24 Stunden enthalten. Für jede Komponente sollte pro Tag ein eindeutiges Ablaufverfolgungsprotokoll erstellt werden. Dieser Wert wird auf "Unique (Standard)" festgelegt. Ändern Sie diesen Wert nicht.|  
|`Components`|Gibt die Komponenten, für die Ablaufverfolgungsprotokoll-Informationen generiert werden, sowie die Ablaufverfolgungsebene in diesem Format an:<br /><br /> \<Komponentenkategorie>:\<Ablaufverfolgungsebene><br /><br /> Für Komponentenkategorien kann Folgendes festgelegt werden:<br />`All` wird zur Ablaufverfolgung der allgemeinen Berichtsserveraktivität für alle Vorgänge verwendet, die nicht in die einzelnen Kategorien unterteilt werden.<br />`RunningJobs` wird für die Ablaufverfolgung eines ausgeführten Berichts oder eines Abonnementvorgangs verwendet.<br />`SemanticQueryEngine` wird für die Ablaufverfolgung einer Semantikabfrage verwendet, die verarbeitet wird, wenn ein Benutzer eine Ad-hoc-Durchsuchung von Daten in einem modellbasierten Bericht ausführt.<br />`SemanticModelGenerator` wird für die Ablaufverfolgung der Modellgenerierung verwendet.<br />`http` wird verwendet, um die Berichtsserver-HTTP-Protokolldatei zu aktivieren. Weitere Informationen finden Sie unter [Report Server HTTP Log](report-server-http-log.md).<br /><br /> <br /><br /> Gültige Werte für die Ablaufverfolgungsebene sind Folgende:<br /><br /> 0= Deaktiviert die Ablaufverfolgung<br /><br /> 1= Ausnahmen und Neustarts<br /><br /> 2= Ausnahmen, Neustarts, Warnungen<br /><br /> 3= Ausnahmen, Neustarts, Warnungen, Statusmeldungen (Standard)<br /><br /> 4= Ausführlicher Modus<br /><br /> Der Standardwert für Berichtsserver ist: "all:3".<br /><br /> Sie können alle oder einige der Komponenten angeben (`all`, `RunningJobs`, `SemanticQueryEngine` und `SemanticModelGenerator`). Wenn Informationen für eine bestimmte Komponente nicht generiert werden sollen, können Sie deren Ablaufverfolgung deaktivieren (z. B. "SemanticModelGenerator:0"). Deaktivieren Sie nicht die Ablaufverfolgung für `all`.<br /><br /> Wenn Sie keine Ablaufverfolgungsebene an die Komponente anfügen, wird der für `DefaultTraceSwitch` angegebene Wert verwendet. Wenn Sie beispielsweise "all,RunningJobs,SemanticQueryEngine,SemanticModelGenerator" angeben, verwenden alle Komponenten die Standard-Ablaufverfolgungsebene.<br /><br /> Sie können "SemanticQueryEngine:4" festlegen, wenn Sie die für jede Semantikabfrage generierten Transact-SQL-Anweisungen anzeigen möchten. Die Transact-SQL-Anweisungen werden im Ablaufverfolgungsprotokoll aufgezeichnet. Im folgenden Beispiel wird die Konfigurationseinstellung veranschaulicht, die dem Protokoll Transact-SQL-Anweisungen hinzufügt:<br /><br /> \<add name="Komponenten" value="all,SemanticQueryEngine:4" />|  
  
##  <a name="bkmk_add_custom"></a> Hinzufügen einer benutzerdefinierten Konfigurationseinstellung zum Angeben eines Speicherortes für eine Sicherungsdatei  
 Sie können dem Speicherort, der vom Windows-Tool Dr. Watson zum Speichern von Sicherungsdateien verwendet wird, eine benutzerdefinierte Einstellung hinzufügen. Die benutzerdefinierte Einstellung ist `Directory`. Im folgenden Beispiel wird veranschaulicht, wie diese Konfigurationseinstellung im Abschnitt `RStrace` angegeben wird:  
  
```  
<add name="Directory" value="U:\logs\" />  
```  
  
 Weitere Informationen finden Sie im [Knowledge Base-Artikel 913046](https://support.microsoft.com/?kbid=913046) auf der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Website.  
  
##  <a name="bkmk_log_file_fields"></a> Protokolldateifelder  
 Ein Ablaufverfolgungsprotokoll enthält folgende Felder:  
  
-   Systeminformationen, einschließlich Betriebssystem, Version, Anzahl der Prozessoren und Arbeitsspeicher.  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Komponente und Versionsinformationen.  
  
-   Im Anwendungsprotokoll protokollierte Ereignisse.  
  
-   Vom Berichtsserver generierte Ausnahmen.  
  
-   Von einem Berichtsserver protokollierte Warnungen wegen unzureichender Ressourcen.  
  
-   Eingehende SOAP-Umschläge und zusammengefasste ausgehende SOAP-Umschläge.  
  
-   Informationen zu HTTP-Header, Stapelüberwachung und Debugablaufverfolgung.  
  
 Sie können anhand der Informationen im Ablaufverfolgungsprotokoll bestimmen, ob ein Bericht übermittelt wurde, wer den Bericht empfangen hat und wie viele Übermittlungsversuche unternommen wurden. Ablaufverfolgungsprotokolle zeichnen auch Berichtsausführungsaktivitäten sowie die Umgebungsvariablen auf, die bei der Berichtsverarbeitung verwendet werden. Fehler und Ausnahmen werden ebenfalls in Ablaufverfolgungsprotokollen aufgezeichnet. Dazu zählen beispielsweise Berichtstimeoutfehler (erkennbar am `ThreadAbortExceptions`-Eintrag).  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Protokolldateien und Quellen](../report-server/reporting-services-log-files-and-sources.md)   
 [Fehler- und Ereignisreferenz &#40;Reporting Services&#41;](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
