---
title: SQL Server, Datenbanken-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Databases object
- SQLServer:Databases
- Availability Groups [SQL Server], performance counters
ms.assetid: a7f9e7d4-fff4-4c72-8b3e-3f18dffc8919
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b4c0c7a5626f3eb48509d7a4cfbf239f7cb931da
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52776422"
---
# <a name="sql-server-databases-object"></a>SQL Server, Datenbanken-Objekt
  Das **SQLServer:Datenbanken** -Objekt in SQL Server stellt Leistungsindikatoren bereit, mit denen Sie Massenkopiervorgänge, den Durchsatz von Sicherungs- und Wiederherstellungsvorgängen sowie Transaktionsprotokollaktivitäten überwachen können. Überwachen Sie Transaktionen und das Transaktionsprotokoll, um ermitteln zu können, wie viel Benutzeraktivität in der Datenbank auftritt und in welchem Umfang das Transaktionsprotokoll aufgefüllt wird. Durch den Umfang der Benutzeraktivität kann die Leistung der Datenbank bestimmt werden. Protokollgröße, Sperren und die Replikation können davon betroffen sein. Das Überwachen der Protokollaktivität auf niedriger Ebene zur Messung der Benutzeraktivität und der Ressourcennutzung kann Ihnen dabei helfen, Leistungsengpässe zu erkennen.  
  
 Es können mehrere Instanzen des **Datenbanken** -Objekts überwacht werden, von denen jede eine einzelne Datenbank darstellt.  
  
 In dieser Tabelle werden die **Datenbanken** -Leistungsindikatoren von SQL Server beschrieben.  
  
|Datenbanken-Leistungsindikatoren von SQL Server|Description|  
|-----------------------------------|-----------------|  
|**Aktive Transaktionen**|Anzahl von aktiven Transaktionen für die Datenbank.|  
|**Sicherungs-/Wiederherstellungsdurchsatz/Sekunde**|Durchsatz von Lese-/Schreiboperationen bei Sicherungs- und Wiederherstellungsvorgängen für eine Datenbank pro Sekunde. So können Sie beispielsweise messen, wie sich die Leistung des Datenbank-Sicherungsvorgangs ändert, wenn mehr Sicherungsmedien parallel verwendet werden oder wenn schnellere Medien verwendet werden. Der Durchsatz eines Datenbank-Sicherungs- oder -Wiederherstellungsvorgangs ermöglicht es Ihnen, den Fortschritt und die Leistung der gesamten Sicherungs- und Wiederherstellungsvorgänge zu ermitteln.|  
|**Zeilen für Massenkopieren/Sekunde**|Anzahl von massenkopierten Zeilen pro Sekunde.|  
|**Durchsatz bei Massenkopieren/Sekunde**|Umfang der pro Sekunde massenkopierten Daten (in KB).|  
|**Commit-Tabelleneinträge**|Die Größe des speicherinternen Anteils der Commit-Tabelle für die Datenbanken. Weitere Informationen finden Sie unter [sys.dm_tran_commit_table &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/change-tracking-sys-dm-tran-commit-table).|  
|**Größe der Datendatei(en) (KB)**|Die kumulierte Größe (in KB) aller Datendateien in der Datenbank, wobei auch jegliche automatische Vergrößerung berücksichtigt ist. Die Überwachung dieses Leistungsindikators ist z. B: nützlich, wenn die richtige Größe von **tempdb**ermittelt werden soll.|  
|**DBCC - Rate logischer Scans/Sekunde**|Anzahl an Bytes logischer Lesescans pro Sekunde für DBCC-Anweisungen (Database Console Commands, Datenbankkonsolenbefehle).|  
|**Protokollcache-Trefferquote**|Prozentsatz der Lesevorgänge im Protokollcache, die durch den Protokollcache aufgelöst werden konnten.|  
|**Protokollcache-Lesevorgänge/Sekunde**|Lesevorgänge pro Sekunde, die über den Cache des Protokoll-Managers ausgeführt wurden.|  
|**Protokolldatei(en) Größe (KB)**|Die kumulierte Größe aller Protokolldateien in der Datenbank (in KB).|  
|**Von Protokolldatei(en) verwendete Größe (KB)**|Die kumulierte verwendete Größe aller Protokolldateien in der Datenbank.|  
|**Wartezeit für Protokollleerung**|Gesamte Wartezeit (in Millisekunden) bis zum Entleeren des Protokolls. Bei einer sekundären AlwaysOn-Datenbank gibt dieser Wert die Wartezeit für Protokolldatensätze an, die auf einem Datenträger festzuschreiben sind.|  
|**Ausstehende Protokollleerungen/Sekunde**|Anzahl von Commits pro Sekunde, die auf eine Protokollleerung warten.|  
|**Wartezeit für Protokollleerung (ms)**|Entspricht der Zeit in Millisekunden zum Ausführen von Schreibvorgängen für Protokollleerungen, die in der letzten Sekunde abgeschlossen wurden.|  
|**Protokollleerungen/Sekunde**|Anzahl an Protokollleerungen pro Sekunde.|  
|**Protokollvergrößerungen**|Gesamtanzahl von Vergrößerungen des Transaktionsprotokolls für diese Datenbank.|  
|**Protokollverkleinerungen**|Gesamtanzahl an Verkleinerungen des Transaktionsprotokolls für diese Datenbank.|  
|**Protokollpool-Cachefehlversuche/Sekunde**|Anzahl an Anforderungen, für die der Protokollblock im Protokollpool nicht verfügbar war. Der *Protokollpool* ist ein arbeitsspeicherinterner Cache für das Transaktionsprotokoll. Dieser Cache wird verwendet, um das Lesen des Protokolls zur Wiederherstellung, Transaktionsreplikation, Rollback und [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]zu optimieren.|  
|**Protokollpool-Lesevorgänge auf dem Datenträger/Sekunde**|Anzahl an Lesevorgängen auf dem Datenträger, die vom Protokollpool zum Abrufen von Protokollblöcken ausgegeben wurden.|  
|**Protokollpoolanforderungen/Sekunde**|Die Anzahl an Protokollblockanforderungen, die vom Protokollpool verarbeitet wurden.|  
|**Protokollkürzungen**|Die Anzahl, wie oft das Transaktionsprotokoll verkleinert wurde.|  
|**Protokoll verwendet (Prozent)**|Der prozentuale Anteil des Speicherplatzes im Protokoll, der verwendet wird.|  
|**Replikations Replikationstransaktionen**|Anzahl von Transaktionen im Transaktionsprotokoll der Veröffentlichungsdatenbank, die für die Replikation gekennzeichnet sind, jedoch noch nicht an die Verteilungsdatenbank übermittelt wurden.|  
|**Replikations Trans. Zins**|Anzahl von Transaktionen, die pro Sekunde aus dem Transaktionsprotokoll der Veröffentlichungsdatenbank ausgelesen und an die Verteilungsdatenbank übermittelt wurden.|  
|**Verschiebung bei Datenverkleinerung Bytes/Sekunde**|Umfang an Daten, die bei der automatischen Verkleinerung oder der Ausführung von DBCC SHRINKDATABASE oder DBCC SHRINKFILE pro Sekunde verschoben wurden.|  
|**Nachverfolgte Transaktionen/Sekunde**|Anzahl an Transaktionen, für die ein Commit ausgeführt wurde und die in der Commit-Tabelle für die Datenbank erfasst wurden.|  
|**Transaktionen/Sekunde**|Anzahl an Transaktionen, die für die Datenbank pro Sekunde gestartet wurden.<br /><br /> **Transaktionen/Sekunde** zählt keine XTP-Transaktionen (d.h. Transaktionen, die durch eine nativ kompilierte gespeicherte Prozedur gestartet wurden).|  
|**Geschriebene Transaktionen/Sek**|Anzahl von Transaktionen, die in der letzten Sekunde Daten in die Datenbank geschrieben und einen Commit durchgeführt haben.|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, Datenbankreplikat](sql-server-database-replica.md)  
  
  
