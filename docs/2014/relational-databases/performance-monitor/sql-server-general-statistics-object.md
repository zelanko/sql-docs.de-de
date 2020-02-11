---
title: SQL Server, Allgemeine Statistik-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:General Statistics
- General Statistics object
ms.assetid: c738e549-d7e7-4211-9ec3-064ac140af7c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a8b2131e4c3c2070bb03018c48294543b9baef02
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250639"
---
# <a name="sql-server-general-statistics-object"></a>SQL Server, Allgemeine Statistik-Objekt
  Das **SQLServer: Allgemeine Statistik** -Objekt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in stellt Leistungsindikatoren bereit, mit denen die allgemeine Server weite Aktivität überwacht werden kann, z. b. die Anzahl der aktuellen Verbindungen und die Anzahl der Benutzer, die pro [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Sekunde eine Verbindung mit Computern herstellen, die eine Instanz von ausführen. Dies ist vor allem bei großen OLTP-Systemen (Online Transaction Processing, Onlinetransaktionsverarbeitung) sehr nützlich, wenn viele Clients eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellen oder trennen.  
  
 In dieser Tabelle werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-Leistungsindikatoren von** beschrieben.  
  
|Allgemeine Statistik-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|--------------------------------------------|-----------------|  
|**Aktive temporäre Tabellen**|Anzahl der verwendeten temporären Tabellen/Tabellenvariablen|  
|**Verbindungs zurück Stellungen/Sek.**|Gesamtzahl von Anmeldungen vom Verbindungspool aus.|  
|**Verzögerte Drop-Ereignis Benachrichtigungen**|Anzahl der Ereignisbenachrichtigungen, die von einem Systemthread gelöscht werden sollen|  
|**HTTP-authentifizierte Anforderungen**|Anzahl der authentifizierten HTTP-Anforderungen, die pro Sekunde gestartet werden|  
|**Logische Verbindungen**|Anzahl der logischen Verbindungen mit dem System<br /><br /> Der Hauptzweck von logischen Verbindungen besteht darin, MARS-Anforderungen (Multiple Active Result Sets) zu verarbeiten. Bei MARS-Anforderungen können mehrere logische Verbindungen für eine physische Verbindung vorhanden sein, wenn eine Anwendung eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellt.<br /><br /> Wenn MARS nicht verwendet wird, ist das Verhältnis zwischen physischen und logischen Verbindungen 1:1. Daher erhöht sich die Anzahl der logischen Verbindungen um jeweils 1, wenn eine Anwendung eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellt.|  
|**Anmeldungen/Sek.**|Gesamtanzahl der gestarteten Anmeldungen pro Sekunden. Dieser Leistungsindikator schließt keine Verbindungen in einem Pool ein.|  
|**Logouts/Sek.**|Gesamtanzahl der Abmeldevorgänge, die pro Sekunde gestartet wurden|  
|**MARS-Deadlocks**|Anzahl der erkannten MARS-Deadlocks|  
|**Nicht atomarische Yield-Rate**|Anzahl der nicht atomaren Ergebnisse pro Sekunde|  
|**Blockierte Prozesse**|Anzahl der zurzeit blockierten Prozesse|  
|**Leere SOAP-Anforderungen**|Anzahl der leeren SOAP-Anforderungen, die pro Sekunde gestartet werden|  
|**SOAP-Methodenaufrufe**|Anzahl der SOAP-Methodenaufrufe, die pro Sekunde gestartet werden|  
|**Initiierungs Anforderungen für SOAP-Sitzungen**|Anzahl der pro Sekunde gestarteten Initiierungsanforderungen für SOAP-Sitzungen|  
|**Beendigungs Anforderungen für SOAP-Sitzungen**|Anzahl der pro Sekunde gestarteten Beendigungsanforderungen für SOAP-Sitzungen|  
|**SOAP-SQL-Anforderungen**|Anzahl der SOAP-SQL-Anforderungen, die pro Sekunde gestartet werden|  
|**SOAP-WSDL-Anforderungen**|Anzahl der pro Sekunde gestarteten SOAP-WSDL-Anforderungen|  
|**Erstellungs Rate für temporäre Tabellen**|Anzahl der temporären Tabellen/Tabellenvariablen, die pro Sekunde erstellt werden|  
|**Temporäre Tabellen für Zerstörung**|Anzahl der temporären Tabellen/Tabellenvariablen, die durch den Cleanupsystemthread gelöscht werden|  
|**Warteschlange für Ablauf Verfolgungs Ereignisse**|Anzahl der Benachrichtigungsinstanzen von Ablaufverfolgungsereignissen in der internen Warteschlange, die durch Service Broker gesendet werden sollen|  
|**Transaktionen**|Anzahl der Transaktionseintragungen (lokal, über DTC und gebunden)|  
|**Benutzer Verbindungen**|Zählt die Anzahl der Benutzer, die zurzeit mit SQL Server verbunden sind|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
