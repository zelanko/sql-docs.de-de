---
title: Analysis Services-Ablaufverfolgungsereignisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- events [Analysis Services]
- event classes [Analysis Services], about event classes
- Profiler [SQL Server Profiler], Analysis Services
- event classes [Analysis Services]
ms.assetid: 6fb219cc-f37e-437a-a544-01cec0953571
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f9d20abf0f811b06ec380b1d4ba984c2f6d7eb87
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153490"
---
# <a name="analysis-services-trace-events"></a>Analysis Services-Ablaufverfolgungsereignisse
  Sie können der Aktivität einer Microsoft SQL Server Analysis Services (SSAS)-Instanz verfolgen, indem Sie die von der Instanz generierten Ablaufverfolgungsereignisse erfassen und anschließend analysieren.  Ablaufverfolgungsereignisse werden so gruppiert, dass verwandte Ablaufverfolgungsereignisse einfacher gefunden werden können.  Jedes Ablaufverfolgungsereignis enthält einen Satz von Daten, der für das Ereignis relevant ist. Nicht alle Datenelemente sind für sämtliche Ereignisse von Bedeutung.  
  
 Ablaufverfolgungsereignisse können gestartet und aufgezeichnet werden mithilfe von **[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]**, finden Sie unter [verwenden SQL Server Profiler zum Überwachen von Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md), oder gestartet werden kann, ein XMLA-Befehl als **SQL Server Erweiterte Ereignisse** und später analysiert, finden Sie [verwenden SQL Server Extended Events &#40;XEvents&#41; zum Überwachen von Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md).  
    
 In den folgenden Tabellen werden jede Ereigniskategorie und die Ereignisse in dieser Kategorie beschrieben.  
  
 Jede Tabelle enthält die folgenden Spalten:  
  
 Ereignis-ID  
 Ein ganzzahliger Wert, durch den der Ereignistyp identifiziert wird. Dieser Wert ist hilfreich, wenn Sie in Tabellen oder XML-Dateien konvertierte Ablaufverfolgungen lesen, um den Ereignistyp zu filtern.  
  
 Ereignisname  
 Der dem Ereignis in Analysis Services-Clientanwendungen zugewiesene Name.  
  
 Ereignisbeschreibung  
 Eine kurze Beschreibung des Ereignisses.  
  
 **[Befehlsereignisse (Ereigniskategorie)](command-events-event-category.md)**  
  
 Sammeln von Ereignissen für Befehle.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|15|Command Begin|Beginn des Befehls.|  
|16|Command End|Ende des Befehls.|  
  
 **[Ermittlungsereignisse (Ereigniskategorie)](discover-events-event-category.md)**  
  
 Sammeln von Ereignissen für Ermittlungsanforderungen.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|36|Discover Begin|Start der Ermittlungsanforderung.|  
|38|Discover End|Ende der Ermittlungsanforderung.|  
  
 **[Ermitteln von (Ereigniskategorie)](discover-server-state-event-category.md)**  
  
 Sammeln von Ereignissen für Serverstatus-Ermittlungen.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|33|Server State Discover Begin|Start der Serverstatusermittlung.|  
|34|Server State Discover Data|Inhalt der Antwort der Serverstatusermittlung.|  
|35|Server State Discover End|Ende der Serverstatusermittlung.|  
  
 **[Fehler und Warnungen-Ereigniskategorie](errors-and-warnings-event-category.md)**  
  
 Sammeln von Ereignissen für Serverfehler.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|17|Fehler|Serverfehler.|  
  
 **[File Load- und Save-Ereigniskategorie](file-load-and-save-event-category.md)**  
  
 Sammlung von Ereignissen für die Berichterstellung zu Dateilade- und Speichervorgängen.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|90|File Load Begin|Beginnt das Laden der Datei.|  
|91|File Load End|Beendet das Laden der Datei.|  
|92|File Save Begin|Beginnt das Speichern der Datei.|  
|93|File Save End|File Save End|  
|94|PageOut Begin|Beginnt den PageOut-Vorgang.|  
|95|PageOut End|PageOut End|  
|96|PageIn Begin|Beginnt den PageIn-Vorgang.|  
|97|PageIn End|PageIn End|  
  
 **[Sperren-Ereigniskategorie](lock-events-category.md)**  
  
 Sammlung von sperrenbezogenen Ereignissen.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|50|Deadlock|Deadlock für Metadatensperren.|  
|51|Lock Timeout|Timeout für Metadatensperre.|  
|52|Lock Acquired|Lock Acquired|  
|53|Lock Released|Lock Released|  
|54|Lock Waiting|Lock Waiting|  
  
 **[Benachrichtigungsereignisse (Ereigniskategorie)](notification-events-event-category.md)**  
  
 Sammeln von Benachrichtigungsereignissen.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|39|Benachrichtigung|Benachrichtigungsereignis.|  
|40|Benutzerdefiniert|Benutzerdefiniertes Ereignis.|  
  
 **[Fortschrittsbericht (Ereigniskategorie)](progress-reports-event-category.md)**  
  
 Sammeln von Ereignissen für Fortschrittsberichte.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|5|Progress Report Begin|Fortschrittsbericht beginnt.|  
|6|Progress Report End|Der Statusbericht wurde beendet.|  
|7|Progress Report Current|Der Statusbericht wird ausgeführt.|  
|8|Progress Report Error|Es ist ein Statusberichtfehler aufgetreten.|  
  
 **[Abfrageereignisse – Kategorie](queries-events-category.md)**  
  
 Sammeln von Ereignissen für Abfragen.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|9|Query Begin|Beginn der Abfrage.|  
|10|Abfrageende|Ende der Abfrage.|  
  
 **[Abfrageverarbeitungsereignisse – Kategorie](query-processing-events-category.md)**  
  
 Sammeln von wichtigen Ereignissen während einer Abfrageausführung.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|70|Query Cube Begin|Beginn des Abfragecubes.|  
|71|Query Cube End|Ende des Abfragecubes.|  
|72|Calculate Non Empty Begin|Die Berechnung von nicht leeren Elementen wird gestartet.|  
|73|Calculate Non Empty Current|Die Berechnung nicht leerer Elemente wird ausgeführt.|  
|74|Calculate Non Empty End|Die Berechnung nicht leerer Elemente wird beendet.|  
|75|Serialize Results Begin|Die Serialisierung von Ergebnissen wird gestartet.|  
|76|Serialize Results Current|Die Serialisierung von Ergebnissen wird ausgeführt.|  
|77|Serialize Results End|Die Serialisierung von Ergebnissen wird beendet.|  
|78|Execute MDX Script Begin|Die Ausführung des MDX-Skripts wird gestartet.|  
|79|Execute MDX Script Current|Das MDX-Skript wird ausgeführt. Veraltet.|  
|80|Execute MDX Script End|Die Ausführung des MDX-Skripts wird beendet.|  
|81|Query Dimension|Die Abfragedimension.|  
|11|Query Subcube|Query Subcube für verwendungsbasierte Optimierung.|  
|12|Query Subcube Verbose|Query Subcube mit detaillierten Informationen. Dieses Ereignis kann sich bei Aktivierung negativ auf die Leistung auswirken.|  
|60|Get Data From Aggregation|Abfrage durch Abrufen von Daten aus der Aggregation beantworten. Dieses Ereignis kann sich bei Aktivierung negativ auf die Leistung auswirken.|  
|61|Get Data From Cache|Abfrage durch Abrufen von Daten aus einem der Caches beantworten. Dieses Ereignis kann sich bei Aktivierung negativ auf die Leistung auswirken.|  
|82|VertiPaq SE Query Begin|VertiPaq SE-Abfrage|  
|83|VertiPaq SE Query End|VertiPaq SE-Abfrage|  
|84|Resource Usage|Lese- und Schreibvorgänge für Berichte, CPU-Auslastung nach Ende von Befehlen und Abfragen.|  
|85|VertiPaq SE Query Cache Match|Cacheverwendung in VertiPaq SE-Abfrage|  
|98|Direct Query Begin|Beginn der direkten Abfrage.|  
|99|Direct Query End|Ende der direkten Abfrage.|  
  
 **[Sicherheitsüberwachung-Ereigniskategorie](security-audit-event-category.md)**  
  
 Sammeln von Datenbanküberwachungs-Ereignisklassen.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|1|Audit Login|Sammelt alle neuen Verbindungsereignisse seit dem Start der Ablaufverfolgung (z. B., wenn ein Client eine Verbindung mit einem Server anfordert, auf dem eine SQL Server-Instanz ausgeführt wird).|  
|2|Audit Logout|Sammelt alle neuen Ereignisse zum Trennen einer Verbindung, die seit dem Start der Ablaufverfolgung eingetreten sind, z. B. wenn ein Client einen Befehl zum Trennen der Verbindung ausgibt.|  
|4|Audit Server Starts and Stops|Erfasst das Herunterfahren von Diensten, startet Aktivitäten und hält sie an.|  
|18|Audit Object Permission Event|Erfasst Objektberechtigungsänderungen.|  
|19|Audit Admin Operations-Ereignis|Erfasst Serversicherung/-wiederherstellung/-synchronisierung/-anfügung/-trennung/Laden von Bildern (imageload)/Speichern von Bildern (imagesave).|  
  
 **[Sitzungsereignisse (Ereigniskategorie)](session-events-event-category.md)**  
  
 Sammeln von Sitzungsereignissen.  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|41|Existing Connection|Vorhandene Benutzerverbindung.|  
|42|Vorhandene Sitzung|Vorhandene Sitzung.|  
|43|Sitzungsinitialisierung|Sitzungsinitialisierung.|  
  
## <a name="see-also"></a>Siehe auch  
[Verwenden von SQL Server Profiler zum Überwachen von Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md)
