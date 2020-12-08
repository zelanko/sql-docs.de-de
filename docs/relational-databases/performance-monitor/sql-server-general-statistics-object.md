---
title: SQL Server, Allgemeine Statistik-Objekt | Microsoft-Dokumentation
description: Hier lernen Sie das „SQLServer:Allgemeine Statistiken“-Objekt kennen, das Leistungsindikatoren bereitstellt, mit denen Sie die allgemeine serverweite Aktivität überwachen können, wie etwa die Anzahl von aktuellen Verbindungen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:General Statistics
- General Statistics object
ms.assetid: c738e549-d7e7-4211-9ec3-064ac140af7c
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 124352d2c252f927d0b07a34f1077fe0c9dde210
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505685"
---
# <a name="sql-server-general-statistics-object"></a>SQL Server, Allgemeine Statistik-Objekt
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Das **SQLServer:Allgemeine Statistiken**-Objekt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Leistungsindikatoren bereit, mit denen Sie die allgemeine serverweite Aktivität überwachen können, wie etwa die Anzahl von aktuellen Verbindungen und die Anzahl von Benutzern, die pro Sekunde eine Verbindung mit Computern, die eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführen, herstellen oder trennen. Dies ist vor allem bei großen OLTP-Systemen (Online Transaction Processing, Onlinetransaktionsverarbeitung) sehr nützlich, wenn viele Clients eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellen oder trennen.  
  
 In dieser Tabelle werden die Leistungsindikatoren des Objekts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:**General Statistics** beschrieben.  
  
|Allgemeine Statistik-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|--------------------------------------------|-----------------|  
|**Aktive temporäre Tabellen**|Anzahl der verwendeten temporären Tabellen/Tabellenvariablen|  
|**Connection Resets/Sek**|Gesamtzahl von Anmeldungen vom Verbindungspool aus.|  
|**Verzögertes Löschen von Ereignisbenachrichtigungen**|Anzahl der Ereignisbenachrichtigungen, die von einem Systemthread gelöscht werden sollen|  
|**Authentifizierte HTTP-Anforderungen**|Anzahl der authentifizierten HTTP-Anforderungen, die pro Sekunde gestartet werden|  
|**Logische Verbindungen**|Anzahl der logischen Verbindungen mit dem System<br /><br /> Der Hauptzweck von logischen Verbindungen besteht darin, MARS-Anforderungen (Multiple Active Result Sets) zu verarbeiten. Bei MARS-Anforderungen können mehrere logische Verbindungen für eine physische Verbindung vorhanden sein, wenn eine Anwendung eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellt.<br /><br /> Wenn MARS nicht verwendet wird, ist das Verhältnis zwischen physischen und logischen Verbindungen 1:1. Daher erhöht sich die Anzahl der logischen Verbindungen um jeweils 1, wenn eine Anwendung eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellt.|  
|**Anmeldungen/Sekunde**|Gesamtanzahl der gestarteten Anmeldungen pro Sekunden. Dieser Leistungsindikator schließt keine Verbindungen in einem Pool ein.|  
|**Abmeldungen/Sekunde**|Gesamtanzahl der Abmeldevorgänge, die pro Sekunde gestartet wurden|  
|**MARS-Deadlocks**|Anzahl der erkannten MARS-Deadlocks|  
|**Nicht atomare Ergebnisrate**|Anzahl der nicht atomaren Ergebnisse pro Sekunde|  
|**Blockierte Prozesse**|Anzahl der zurzeit blockierten Prozesse|  
|**Leere SOAP-Anforderungen**|Anzahl der leeren SOAP-Anforderungen, die pro Sekunde gestartet werden|  
|**SOAP-Methodenaufrufe**|Anzahl der SOAP-Methodenaufrufe, die pro Sekunde gestartet werden|  
|**Initiierungsanforderungen für SOAP-Sitzungen**|Anzahl der pro Sekunde gestarteten Initiierungsanforderungen für SOAP-Sitzungen|  
|**Beendigungsanforderungen für SOAP-Sitzungen**|Anzahl der pro Sekunde gestarteten Beendigungsanforderungen für SOAP-Sitzungen|  
|**SOAP-SQL-Anforderungen**|Anzahl der SOAP-SQL-Anforderungen, die pro Sekunde gestartet werden|  
|**SOAP-WSDL-Anforderungen**|Anzahl der pro Sekunde gestarteten SOAP-WSDL-Anforderungen|  
|**Sperrenwartevorgänge für den SQL-Ablaufverfolgungs-E/A-Anbieter**|Anzahl der Sperrenwartevorgänge pro Sekunde für den Datei-EA-Anbieter.| 
|**Erstellungsrate für temporäre Tabellen**|Anzahl der temporären Tabellen/Tabellenvariablen, die pro Sekunde erstellt werden|  
|**Temporäre Tabellen zum Löschen**|Anzahl der temporären Tabellen/Tabellenvariablen, die durch den Cleanupsystemthread gelöscht werden|  
|**ID der tempdb-Wiederherstellungseinheit**|Anzahl der doppelt generierten IDs der tempdb-Wiederherstellungseinheit.|
|**Tempdb-Rowset-ID**|Anzahl der doppelt generierten tempdb-Rowset-IDs.| 
|**Benachrichtigungswarteschlange der Ablaufverfolgungsereignisse**|Anzahl der Benachrichtigungsinstanzen von Ablaufverfolgungsereignissen in der internen Warteschlange, die durch Service Broker gesendet werden sollen|  
|**Transaktionen**|Anzahl der Transaktionseintragungen (lokal, über DTC und gebunden)|  
|**Benutzerverbindungen**|Zählt die Anzahl der Benutzer, die zurzeit mit SQL Server verbunden sind|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
