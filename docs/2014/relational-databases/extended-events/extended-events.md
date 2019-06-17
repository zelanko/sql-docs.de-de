---
title: Erweiterte Ereignisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server]
- xe
ms.assetid: bf3b98a6-51ed-4f2d-9c26-92f07f1fa947
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 485c748aad8b07a5e8b92a02c03d51a82e5f362a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62990701"
---
# <a name="extended-events"></a>Erweiterte Ereignisse
  Die Funktion Erweiterte Ereignisse von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] besitzt eine sehr stark skalierbare und konfigurierbare Architektur, mit der Benutzer je nach Bedarf eine entsprechende Menge an Informationen sammeln können, die zum Beheben oder Identifizieren eines Leistungsproblems notwendig ist.  
  
 Weitere Informationen über die Funktion Erweiterte Ereignisse finden Sie online unter [Erweiterte Ereignisse von SQL Server](https://blogs.msdn.com/b/extended_events/).  
  
## <a name="benefits-of-includessnoversionincludesssnoversion-mdmd-extended-events"></a>Vorteile von erweiterten Ereignissen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Erweiterte Ereignisse ist ein Lightweight-Leistungsüberwachungssystem, das sehr wenige Leistungsressourcen verwendet. Die Funktion „Erweiterte Ereignisse“ stellt zwei grafische Benutzeroberflächen (**Assistent für neue Sitzungen** und **Neue Sitzung**) zum Erstellen, Ändern, Anzeigen und Analysieren der Sitzungsdaten bereit.  
  
## <a name="extended-events-concepts"></a>Konzepte für erweiterte Ereignisse  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Die Funktion „Erweiterte Ereignisse“ basiert auf vorhandenen Konzepten, z.B. einem Ereignis oder einem Ereignisconsumer, verwendet Konzepte aus der Ereignisablaufverfolgung für Windows und führt neue Konzepte ein.  
  
 In der folgenden Tabelle werden die Konzepte von "Erweiterte Ereignisse" beschrieben.  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Pakete für erweiterte Ereignisse von SQL Server](sql-server-extended-events-packages.md)|Beschreibt die Pakete für erweiterte Ereignisse, in denen Objekte enthalten sind, mit denen Daten beim Ausführen einer Sitzung für erweiterte Ereignisse abgerufen und verarbeitet werden.|  
|[Ziele für erweiterte Ereignisse von SQL Server](../../database-engine/sql-server-extended-events-targets.md)|Beschreibt die Ereignisconsumer, die während einer Ereignissitzung Daten empfangen können.|  
|[Engine für erweiterte Ereignisse von SQL Server](sql-server-extended-events-engine.md)|Beschreibt die Engine, die eine Sitzung für erweiterte Ereignisse implementiert und verwaltet.|  
|[Sitzungen für erweiterte Ereignisse von SQL Server](sql-server-extended-events-sessions.md)|Beschreibt die Sitzung für erweiterte Ereignisse.|  
  
## <a name="extended-events-architecture"></a>Architektur von erweiterten Ereignissen  
 Erweiterte Ereignisse entsprechen einem allgemeinen Ereignisbehandlungssystem für Serversysteme. Die Infrastruktur für erweiterte Ereignisse unterstützt die Korrelation von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sowie unter bestimmten Umständen die Korrelation von Daten aus dem Betriebssystem und aus Datenbankanwendungen. Im zweiten Fall muss die Ausgabe von erweiterten Ereignissen an die Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW) weitergeleitet werden, damit die Ereignisdaten mit Ereignisdaten aus dem Betriebssystem oder einer Anwendung korreliert werden können.  
  
 Alle Anwendungen weisen Ausführungspunkte auf, die sowohl innerhalb der Anwendung als auch außerhalb nützlich sind. In der Anwendung kann die asynchrone Verarbeitung in die Warteschlange eingereiht werden, wobei Informationen zugrunde gelegt werden, die bei der ersten Ausführung eines Tasks gesammelt wurden. Außerhalb der Anwendung stellen Ausführungspunkte Überwachungshilfsprogrammen Informationen zum Verhalten und zu den Leistungsmerkmalen der überwachten Anwendung zur Verfügung.  
  
 Erweiterte Ereignisse unterstützen die Verwendung von Ereignisdaten außerhalb eines Prozesses. Diese Daten werden i. d. R. folgendermaßen verwendet:  
  
-   Von Ablaufverfolgungstools wie der SQL-Ablaufverfolgung und dem Systemmonitor  
  
-   Von Tools für die Protokollierung wie dem Windows-Ereignisprotokoll oder dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll  
  
-   Von Benutzern, die ein Produkt verwalten oder Anwendungen für ein Produkt entwickeln  
  
 Das Design von erweiterten Ereignissen zeichnet sich durch die folgenden zentralen Aspekte aus:  
  
-   Die Engine für erweiterte Ereignisse ist ereignisagnostisch. Daher kann die Engine jedes beliebige Ereignis an jedes beliebige Ziel binden, da es nicht durch den Ereignisinhalt eingeschränkt wird. Weitere Informationen zum Modul für erweiterte Ereignisse finden Sie unter [SQL Server Extended Events Engine](sql-server-extended-events-engine.md).  
  
-   Ereignisse werden von Ereignisconsumern getrennt, die in erweiterten Ereignissen als *Ziele* bezeichnet werden. Das bedeutet, dass jedes Ziel jedes Ereignis empfangen kann. Zusätzlich kann jedes ausgelöste Ereignis automatisch vom Ziel verarbeitet werden, das dann wiederum die Protokollierung ausführen oder zusätzlichen Ereigniskontext bereitstellen kann. Weitere Informationen finden Sie unter [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md).  
  
-   Ereignisse unterscheiden sich von der Aktion, die ausgeführt werden soll, wenn ein Ereignis auftritt. Dies führt dazu, dass jede beliebige Aktion jedem beliebigen Ereignis zugeordnet werden kann.  
  
-   Mithilfe von Prädikaten kann dynamisch gefiltert werden, wenn Ereignisdaten aufgezeichnet werden sollen. Dadurch wird die Infrastruktur für erweiterte Ereignisse noch flexibler. Weitere Informationen finden Sie unter [SQL Server Extended Events Packages](sql-server-extended-events-packages.md).  
  
 Erweiterte Ereignisse können Ereignisdaten synchron generieren (und asynchron verarbeiten), wodurch eine flexible Lösung für die Ereignisbehandlung bereitgestellt wird. Außerdem bieten erweiterte Ereignisse die folgenden Funktionen:  
  
-   Eine im gesamten Serversystem einheitliche Methode für die Ereignisbehandlung, wobei die Benutzer dennoch die Möglichkeit haben, einzelne Ereignisse für die Problembehandlung zu isolieren.  
  
-   Integration mit und Unterstützung von vorhandenen ETW-Tools  
  
-   Einen vollständig konfigurierbaren Ereignisbehandlungsmechanismus auf Grundlage von [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Die Möglichkeit zur dynamischen Überwachung aktiver Prozesse mit minimaler Beeinträchtigung dieser Prozesse.  
  
-   Eine standardmäßige Systemintegritätssitzung, die ohne merkliche Auswirkungen auf die Leistung ausgeführt wird. In der Sitzung werden Systemdaten erfasst, mit deren Hilfe Sie Leistungsprobleme beheben können. Weitere Informationen finden Sie unter [Verwenden der system_health-Sitzung](use-the-ssms-xe-profiler.md).  
  
## <a name="extended-events-tasks"></a>Tasks für erweiterte Ereignisse  
 Durch Verwenden von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)] zum Ausführen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -DDL-Anweisungen (Data Definition Language), dynamischen Verwaltungssichten und -funktionen oder Katalogsichten können Sie einfache oder komplexe Problembehandlungslösungen für erweiterte Ereignisse von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für Ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Umgebung erstellen.  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Verwenden Sie den **Objekt-Explorer** , um Ereignissitzungen zu verwalten.|[Verwalten von Ereignissitzungen im Objektexplorer](../../ssms/object/object-explorer.md)|  
|Beschreibt, wie Sie eine Sitzung für erweiterte Ereignisse erstellen.|[Erstellen einer Sitzung für erweiterte Ereignisse](../../database-engine/create-an-extended-events-session.md)|  
|Beschreibt, wie Sie Zieldaten anzeigen und aktualisieren.|[Anzeigen von Ereignissitzungsdaten](../../database-engine/view-event-session-data.md)|  
|Beschreibt, wie Sie die folgenden Tools von erweiterten Ereignissen zum Erstellen und Verwalten von erweiterten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ereignissitzungen verwenden:|[Tools für erweiterte Ereignisse](extended-events-tools.md)|  
|Beschreibt, wie Sie eine Sitzung für erweiterte Ereignisse ändern.|[Ändern einer Sitzung für erweiterte Ereignisse](alter-an-extended-events-session.md)|  
|Beschreibt, wie Sie Zieldaten kopieren oder exportieren.|[Kopieren oder Exportieren von Zieldaten](../../database-engine/copy-or-export-target-data.md)|  
|Beschreibt, wie Sie die Sicht der Ablaufverfolgungsergebnisse ändern, um die Analyse der Daten anzupassen.|[Ändern der Sicht der Ablaufverfolgungsergebnisse](../../database-engine/modify-the-trace-results-view.md)|  
|Beschreibt, wie Sie Informationen zu den den Ereignissen zugeordneten Feldern abrufen.|[Abrufen der Felder für alle Ereignisse](../../database-engine/get-the-fields-for-all-events.md)|  
|Beschreibt, wie Sie herausfinden, welche Ereignisse in den registrierten Paketen verfügbar sind.|[Anzeigen der Ereignisse für registrierte Pakete](../../database-engine/view-the-events-for-registered-packages.md)|  
|Beschreibt, wie Sie ermitteln, welche Ziele für erweiterte Ereignisse in den registrierten Paketen verfügbar sind.|[Anzeigen der Ziele von erweiterten Ereignissen für registrierte Pakete](../../database-engine/view-the-extended-events-targets-for-registered-packages.md)|  
|Beschreibt, wie Sie die Ereignisse und Aktionen für erweiterte Ereignisse anzeigen, die den einzelnen SQL-Ablaufverfolgungsereignissen und deren zugeordneten Spalten entsprechen.|[Anzeigen der Entsprechungen von erweiterten Ereignissen für SQL-Ablaufverfolgungsklassen](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)|  
|Beschreibt, wie Sie die Parameter suchen, die sich festlegen lassen, wenn Sie das ADD TARGET-Argument in CREATE EVENT SESSION oder ALTER EVENT SESSION verwenden.|[Abrufen der konfigurierbaren Parameter für das ADD TARGET-Argument](../../database-engine/get-the-configurable-parameters-for-the-add-target-argument.md)|  
|Beschreibt, wie Sie ein vorhandenes SQL-Ablaufverfolgungsskript in eine Sitzung für erweiterte Ereignisse konvertieren.|[Konvertieren eines vorhandenen SQL-Ablaufverfolgungsskripts in eine Sitzung für erweiterte Ereignisse](convert-an-existing-sql-trace-script-to-an-extended-events-session.md)|  
|Beschreibt die Ermittlung der gesperrten Abfragen, des Plans der Abfrage und des [!INCLUDE[tsql](../../includes/tsql-md.md)] -Stapels zum Zeitpunkt der Sperrung.|[Feststellen, welche Abfragen Sperren enthalten](determine-which-queries-are-holding-locks.md)|  
|Beschreibt, wie Sie die Quelle von Sperren identifizieren, die die Datenbankleistung beeinträchtigen.|[Suchen der Objekte, die über die meisten Sperren verfügen](find-the-objects-that-have-the-most-locks-taken-on-them.md)|  
|Beschreibt, wie Sie anhand von erweiterten Ereignissen mit der Ereignisablaufverfolgung für Windows die Systemaktivität überwachen.|[Überwachen der Systemaktivität mit erweiterten Ereignissen](monitor-system-activity-using-extended-events.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenebenenanwendungen](../data-tier-applications/data-tier-applications.md)   
 [DAC-Unterstützung für SQL Server-Objekte und -Versionen](../data-tier-applications/dac-support-for-sql-server-objects-and-versions.md)   
 [Bereitstellen einer Datenebenenanwendung](../data-tier-applications/deploy-a-data-tier-application.md)   
 [Überwachen von Datenebenenanwendungen](../data-tier-applications/monitor-data-tier-applications.md)   
 [Dynamische Verwaltungssichten für erweiterte Ereignisse](../views/views.md)   
 [Ereignisse Katalogsichten für erweiterte &#40;Transact-SQL&#41;] (~/relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql  
  
  
