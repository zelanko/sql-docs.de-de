---
description: MSSQLSERVER_833
title: MSSQLSERVER_833 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 132e33d7bf2b03df21a1d6a3475ca625675b3328
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91988762"
---
# <a name="mssqlserver_833"></a>MSSQLSERVER_833
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sql-asdbmi.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|833|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|BUF_LONG_IO|  
|Meldungstext|Bei %d E/A-Anforderungen von SQL Server wurden mehr als %d Sekunden zum Abschließen des Vorgangs für die Datei [%ls] in der Datenbank `[%ls] (%d)` benötigt .  Das Dateihandle des Betriebssystems lautet 0x%p.  Der Offset des letzten langen E/A-Vorgangs lautet: %#016I64x.|  
  
## <a name="explanation"></a>Erklärung  
Mit dieser Meldung wird angegeben, dass von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Lese- oder Schreibanforderung vom Datenträger ausgegeben wurde und dass die Rückgabe der Anforderung länger als 15 Sekunden gedauert hat. Dieser Fehler wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gemeldet und deutet auf ein Problem mit dem E/A-Subsystem hin. Möglicherweise bemerken Sie auch weitere Symptome im Zusammenhang mit dieser Meldung: lange Wartezeiten für PAGEIOLATCH-Wartevorgänge, Warnungen oder Fehler im Systemereignisprotokoll, Hinweise auf Probleme mit der Datenträgerlatenz bei Leistungsindikatoren der Systemüberwachung. Überwachen Sie [sys.dm_io_virtual_file_stats](../system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md), und wählen Sie eine geeignete Speicherebene und einen geeigneten IOPS-Wert für Ihren Speicherdurchsatz aus. 
  
### <a name="possible-causes"></a>Mögliche Ursachen  
Dieses Problem kann durch Leistungsprobleme im Betriebssystem, Hardware- oder Firmwarefehler, Gerätetreiberprobleme oder das Eingreifen von Filtertreibern in den E/A-Vorgang oder Speicherpfad von Datenbankdateien verursacht werden. SQL Server zeichnet die Uhrzeit der Initiierung einer E/A-Anforderung sowie die Uhrzeit des Abschlusses des E/A-Vorgangs auf. Wenn der Unterschied zwischen diesen beiden Zeitpunkten 15 Sekunden oder mehr beträgt, wird diese Bedingung erkannt. Das bedeutet auch, dass SQL Server nicht die Ursache einer verzögerten E/A-Bedingung ist, die in dieser Meldung berichtet und beschrieben wird. Diese Bedingung wird als „verzögerte E/A“ bezeichnet. Die meisten Datenträgeranforderungen erfolgen mit der typischen Geschwindigkeit des Datenträgers. Diese typische Datenträgergeschwindigkeit wird häufig als „Datenträgersuchzeit“ bezeichnet. Die Datenträgersuchzeit bei den meisten Standarddatenträgern beträgt 10 Millisekunden oder weniger. Daher sind 15 Sekunden eine sehr lange Zeit für die Rückkehr des E/A-Pfads des Systems zu SQL Server. 
  
## <a name="user-action"></a>Benutzeraktion  
Sie können diesen Fehler durch Überprüfung des Systemereignisprotokolls auf hardwarebedingte Fehlermeldungen beheben. Sie können zudem hardwarespezifische Protokolle überprüfen, sofern diese verfügbar sind. Sie sollten die erforderlichen Methoden und Techniken verwenden, um die Ursache der Verzögerung im Betriebssystem, bei den Treibern oder bei der E/A-Hardware zu ermitteln. Die Lösung dieses Problems umfasst möglicherweise eine Aktualisierung aller Gerätetreiber und Firmware oder die Ausführung weiterer Diagnosemaßnahmen im Zusammenhang mit Ihrem Datenträgersystem. 
  
Prüfen Sie mit dem Systemmonitor die folgenden Leistungsindikatoren:  
  
-   **Average Disk Sec/Transfer**  
  
-   **Average Disk Queue Length**  
  
-   **Current Disk Queue Length**  
  
Beispielsweise beträgt die Zeit von **Average Disk Sec/Transfer** für einen Computer mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] normalerweise unter 15 Millisekunden. Wenn sich der Wert **Average Disk Sec/Transfer** erhöht, ist dies ein Hinweis darauf, dass das E/A-Subsystem den E/A-Bedarf nicht optimal erfüllt.

Sie können auch Features wie die [Storport-ETW-Protokollierung](/archive/blogs/ntdebugging/storport-etw-logging-to-measure-requests-made-to-a-disk-unit) verwenden, um die Latenz von Anforderungen zu messen, die an eine Datenträgereinheit gesendet werden. Ein weiteres ähnliches Kit für die Problembehandlung bei E/A-Vorgängen ist als integriertes Profil [Windows Performance Recorder](/windows-hardware/test/wpt/introduction-to-wpr) verfügbar.
  
> [!NOTE]  
> Der Datenträgerzugriff wird möglicherweise durch ein Antivirenprogramm verzögert. Schließen Sie die in der Fehlermeldung angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datendateien von aktiven Virenüberprüfungen aus, um die Zugriffsgeschwindigkeit zu erhöhen. Sie können das [Befehlszeilen-Hilfsprogramm „fltmc.exe“](/windows-hardware/drivers/ifs/development-and-testing-tools#fltmcexe-control-program) verwenden, um alle im System installierten Filtertreiber abzufragen und sich über die Funktionen zu informieren, die das Programm im Speicherpfad zu den Datenbankdateien ausführt. 
  
Weitere Informationen zu E/A-Fehlern finden Sie unter [Microsoft SQL Server I/O Basics, Chapter 2 (E/A-Grundlagen von Microsoft SQL Server, Kapitel 2)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) und im Knowledge Base-Artikel unter [https://support.microsoft.com/kb/897284/en-us](https://support.microsoft.com/kb/897284/en-us).  
