---
title: Überwachen von Python und R-Skripts mit erweiterten Ereignissen
description: Erfahren Sie, wie Sie erweiterte Ereignisse verwenden, um Vorgänge im Zusammenhang mit den SQL Server Machine Learning Services, SQL Server-Launchpad und Python oder R-Aufträgen externe Skripts zu überwachen und zu beheben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6faef1bd78b1c1aa42714da75679dc989f0b9da9
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714384"
---
# <a name="monitor-python-and-r-scripts-with-extended-events-in-sql-server-machine-learning-services"></a>Überwachen von Python-und R-Skripts mit erweiterten Ereignissen in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Erfahren Sie, wie Sie erweiterte Ereignisse verwenden, um Vorgänge im Zusammenhang mit den SQL Server Machine Learning Services, SQL Server-Launchpad und Python oder R-Aufträgen externe Skripts zu überwachen und zu beheben.

## <a name="extended-events-for-sql-server-machine-learning-services"></a>Erweiterte Ereignisse für SQL Server Machine Learning Services

Führen Sie die folgende Abfrage aus Azure Data Studio oder SQL Server Management Studio aus, um eine Liste der Ereignisse anzuzeigen, die sich auf SQL Server Machine Learning Services beziehen.

```sql
SELECT o.name AS event_name, o.description
FROM sys.dm_xe_objects o
JOIN sys.dm_xe_packages p
ON o.package_guid = p.guid
WHERE o.object_type = 'event'
AND p.name = 'SQLSatellite';
```

Weitere Informationen zur Verwendung von erweiterten Ereignissen finden Sie unter [Tools für erweiterte Ereignisse](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).

## <a name="additional-events-specific-to-machine-learning-services"></a>Zusätzliche Ereignisse, die für Machine Learning Services spezifisch sind

Zusätzliche erweiterte Ereignisse sind für Komponenten verfügbar, die mit SQL Server Machine Learning Services verknüpft und verwendet werden, wie z. b. die [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] und bxlserver, sowie der Satelliten Prozess, der die python-oder R-Laufzeit startet. Diese zusätzlichen erweiterten Ereignisse werden von den externen Prozessen ausgelöst. Daher müssen Sie mithilfe eines externen Hilfsprogramms aufgezeichnet werden.

Weitere Informationen hierzu finden Sie im Abschnitt [Sammeln von Ereignissen aus externen Prozessen](#bkmk_externalevents).

<a name="bkmk_xeventtable"></a> 

## <a name="table-of-extended-events"></a>Tabelle erweiterter Ereignisse

|Ereignis|Beschreibung|Hinweise|  
|-----------|-----------------|---------|  
|connection_accept|Tritt auf, wenn eine neue Verbindung akzeptiert wird. Dieses Ereignis dient dazu, alle Verbindungsversuche zu protokollieren.||  
|failed_launching|Fehler beim Starten.|Gibt einen Fehler an.|  
|satellite_abort_connection|Eintrag über einen Verbindungsabbruch||  
|satellite_abort_received|Wird ausgelöst, wenn eine Abbruchnachricht über eine Satellitenverbindung empfangen wird.||  
|satellite_abort_sent|Wird ausgelöst, wenn eine Abbruchnachricht über eine Satellitenverbindung gesendet wird.||  
|satellite_authentication_completion|Wird ausgelöst, wenn die Authentifizierung für eine TCP- oder Namedpipe-Verbindung abgeschlossen wurde.||  
|satellite_authorization_completion|Wird ausgelöst, wenn die Autorisierung für eine TCP- oder Namedpipe-Verbindung abgeschlossen wurde.||  
|satellite_cleanup|Wird ausgelöst, wenn ein Satellit Cleanup aufruft.|Nur aus externem Prozess ausgelöst. Lesen Sie die Anleitung für das Sammeln von Ereignissen aus externen Prozessen.|  
|satellite_data_chunk_sent|Wird ausgelöst, wenn die Satellitenverbindung das Senden eines einzelnen Datensegments abschließt.|Das Ereignis meldet die Anzahl der gesendeten Zeilen, die Anzahl der Spalten, die Anzahl der verwendeten SNI-Pakete und die verstrichene Zeit in Millisekunden beim Senden des Blocks. Anhand dieser Informationen können Sie nachvollziehen, wie viel Zeit für das Übergeben von verschiedene Datentypen benötigt wird und wie viele Pakete verwendet werden.|  
|satellite_data_receive_completion|Wird ausgelöst, wenn alle erforderlichen Abfragedaten über die Satellitenverbindung empfangen wurden.|Nur aus externem Prozess ausgelöst. Lesen Sie die Anleitung für das Sammeln von Ereignissen aus externen Prozessen.|  
|satellite_data_send_completion|Wird ausgelöst, wenn alle erforderlichen Abfragedaten über die Satellitenverbindung gesendet wurden.||  
|satellite_data_send_start|Wird ausgelöst, wenn die Datenübertragung gestartet wird.| Die Datenübertragung beginnt unmittelbar bevor das erste Daten Segment gesendet wird.|  
|satellite_error|Wird verwendet, um einen SQL-Satellitenfehler nachzuverfolgen||  
|satellite_invalid_sized_message|Länge dieser Nachricht ist ungültig.||  
|satellite_message_coalesced|Wird verwendet, um das Zusammenfügen von Nachrichten auf Netzwerkebene nachzuverfolgen||  
|satellite_message_ring_buffer_record|Eintrag über Nachrichtenringpuffer||  
|satellite_message_summary|zusammenfassende Informationen zur Nachrichtenübermittlung||  
|satellite_message_version_mismatch|Versionsfeld der Nachricht stimmt nicht überein||  
|satellite_messaging|Wird verwendet, um das Nachrichtenereignis (Binden, Bindung aufheben usw.) nachzuverfolgen.||  
|satellite_partial_message|Wird verwendet, um eine Teilnachricht auf Netzwerkebene nachzuverfolgen.||  
|satellite_schema_received|Wird ausgelöst, wenn die Schemanachricht empfangen und von SQL gelesen wird.||  
|satellite_schema_sent|Wird ausgelöst, wenn der Satellit eine Schemanachricht sendet.|Nur aus externem Prozess ausgelöst. Lesen Sie die Anleitung für das Sammeln von Ereignissen aus externen Prozessen.|  
|satellite_service_start_posted|Wird ausgelöst, wenn die Startnachricht des Diensts an Launchpad gesendet wird.|Dies erteilt Launchpad den Auftrag, den externen Prozess zu starten. Außerdem enthält das Ereignis eine ID für die neue Sitzung.|  
|satellite_unexpected_message_received|Wird ausgelöst, wenn eine unerwartete Nachricht empfangen wird.|Gibt einen Fehler an.|  
|stack_trace|Tritt auf, wenn ein Speicherabbild des Prozesses angefordert wird.|Gibt einen Fehler an.|  
|trace_event|Wird zu Protokollierungszwecken verwendet|Diese Ereignisse können Ablaufverfolgungsmeldungen von SQL Server, Launchpad und externen Prozessen enthalten. Dies schließt die Ausgabe an „stdout“ und „stderr“ aus R ein.|  
|launchpad_launch_start|Wird ausgelöst, wenn Launchpad einen Satelliten startet.|Wird nur aus Launchpad ausgelöst. Lesen Sie die Anleitung für das Sammeln von Ereignissen aus launchpad.exe.|  
|launchpad_resume_sent|Wird ausgelöst, wenn Launchpad den Satelliten gestartet und eine Fortsetzungsmeldung an SQL Server gesendet hat.|Wird nur aus Launchpad ausgelöst. Lesen Sie die Anleitung für das Sammeln von Ereignissen aus launchpad.exe.|  
|satellite_data_chunk_sent|Wird ausgelöst, wenn die Satellitenverbindung das Senden eines einzelnen Datensegments abschließt.|Enthält Informationen über die Anzahl der Spalten, Zeilen und Pakete sowie über die zum Versenden des Segments benötigten Zeit.|  
|satellite_sessionId_mismatch|Die Sitzungs-ID der Nachricht wird nicht erwartet.||  

<a name="bkmk_externalevents"></a>

### <a name="collecting-events-from-external-processes"></a>Sammeln von Ereignissen aus externen Prozessen

SQL Server Machine Learning Services startet einige Dienste, die außerhalb des SQL Server Prozesses ausgeführt werden. Zum Erfassen von Ereignissen im Zusammenhang mit diesen externen Prozessen müssen Sie eine Konfigurationsdatei für die Ereignis Ablauf Verfolgung erstellen und die Datei in demselben Verzeichnis wie die ausführbare Datei für den Prozess platzieren.  
  
+ **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
    Legen Sie die *.config*-Datei im Binn-Verzeichnis für die SQL Server-Instanz ab, um Ereignisse zu erfassen, die im Zusammenhang mit Launchpad auftreten. In einer Standardinstallation ist dies Folgendes:

    `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`. installiert haben.  
  
+ **Bxlserver** ist der Satelliten Prozess, der die SQL-Erweiterbarkeit mit externen Skriptsprachen (z. b. R oder python) unterstützt. Für jede externe sprach Instanz wird eine separate Instanz von bxlserver gestartet.
  
    Wenn Sie Ereignisse im Zusammenhang mit bxlserver erfassen möchten, platzieren Sie die *config* -Datei im Installationsverzeichnis von R oder python. In einer Standardinstallation ist dies Folgendes:
     
    **R:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`.  

    **Python:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\PYTHON_SERVICES\library\RevoScaleR\rxLibs\x64`.

Die Konfigurationsdatei muss mit dem Format "[Name]. xevents. xml" identisch mit der ausführbaren Datei benannt werden. Mit anderen Worten: Die Dateien müssen folgendermaßen benannt werden:

+ `Launchpad.xevents.xml`
+ `bxlserver.xevents.xml`

Die Konfigurationsdatei weist das folgende Format auf:

```xml
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="[session name]" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="you">Xevent for launchpad or bxl server.</description>  
    <event package="SQLSatellite" name="[XEvent Name 1]" />  
    <event package="SQLSatellite" name="[XEvent Name 2]" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="[SessionName].xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
```

+ Um die Ablauf Verfolgung zu konfigurieren, bearbeiten Sie den Platzhalter für den *Sitzungs Namen* , den Platz`[SessionName].xel`Halter für den Dateinamen () und die Namen der Ereignisse, die Sie erfassen `[XEvent Name 1]`möchten `[XEvent Name 1]`, z. b.,).  
+ Möglicherweise wird eine beliebige Anzahl von Ereignis Paket Tags angezeigt, die gesammelt werden, solange das Name-Attribut korrekt ist.

### <a name="example-capturing-launchpad-events"></a>Beispiel: Aufzeichnen von Launchpad-Ereignissen

Das folgende Beispiel zeigt die Definition einer Ereignis Ablauf Verfolgung für den Launchpad-Dienst:

```xml
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="launchpad_launch_start" />  
    <event package="SQLSatellite" name="launchpad_resume_sent" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="launchpad_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
```

+ Platzieren Sie die *.config*-Datei im Binn-Verzeichnis für die SQL Server-Instanz.
+ Diese Datei muss den Namen `Launchpad.xevents.xml`haben.

### <a name="example-capturing-bxlserver-events"></a>Beispiel: Erfassen von bxlserver-Ereignissen  

Das folgende Beispiel zeigt die Definition einer Ereignisablaufverfolgung für die ausführbare Datei von BXLServer.
  
```xml
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
 <event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="satellite_abort_received" />  
    <event package="SQLSatellite" name="satellite_authentication_completion" />  
    <event package="SQLSatellite" name="satellite_cleanup" />  
    <event package="SQLSatellite" name="satellite_data_receive_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_start" />  
    <event package="SQLSatellite" name="satellite_schema_sent" />   
    <event package="SQLSatellite" name="satellite_unexpected_message_received" />    
    <event package="SQLSatellite" name="satellite_data_chunk_sent" />   
    <target package="package0" name="event_file">  
      <parameter name="filename" value="satellite_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
```

+ Legen Sie die *.config*-Datei im gleichen Verzeichnis ab wie die ausführbare BXLServer-Datei.
+ Diese Datei muss den Namen `bxlserver.xevents.xml`haben.

## <a name="next-steps"></a>Nächste Schritte

- [Überwachen der Python-und R-Skriptausführung mit benutzerdefinierten Berichten in SQL Server Management Studio](../../advanced-analytics/administration/monitor-sql-server-machine-learning-services-using-custom-reports-management-studio.md)
- [Überwachen von SQL Server Machine Learning Services mithilfe dynamischer Verwaltungs Sichten (DMVs)](../../advanced-analytics/administration/monitor-sql-server-machine-learning-services-using-dynamic-management-views.md)
