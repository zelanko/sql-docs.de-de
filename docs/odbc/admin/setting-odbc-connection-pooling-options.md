---
title: Festlegen von Optionen für ODBC-Verbindungspooling | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection pooling [ODBC]
- ODBC data source administrator [ODBC], connection pooling options
- ODBC data source administrator [ODBC], performance monitoring
ms.assetid: 037e2f78-f204-40f4-b4ab-d9cdf562012b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46b6f5d7e6af3726558f5cee72f00ff06e13ab89
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812057"
---
# <a name="setting-odbc-connection-pooling-options"></a>Festlegen von Optionen für ODBC-Verbindungspooling
Verbindungspooling ermöglicht einer Anwendung eine Verbindung aus einem Pool von Verbindungen verwendet werden, die nicht für jede Verwendung erneut hergestellt werden müssen. Können Sie die **Verbindungspooling** Registerkarte die **ODBC-Datenquellenadministrator** Dialogfeld aktivieren und Deaktivieren der Überwachung der Anwendungsleistung. Doppelklicken Sie auf ein Treibername den Timeoutzeitraum festlegen.  
  
 Auf der Ebene des Treibers ist das Verbindungspooling durch den Registrierungswert CPTimeout aktiviert. Dieses selektive pro-Treiber aktivieren, kann ein Systemadministrator zum Aktivieren des Verbindungspoolings nur die Treiber, die dies unterstützen. Es erfolgt durch Festlegen den Standardwert von CPTimeout während der Setup-Programm des Treibers. Doppelklicken Sie auf ein Treibername den Timeoutzeitraum festlegen.  
  
 Weitere Informationen zum Verbindungspooling finden Sie unter [ODBC-Verbindungspooling](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="performance-monitoring"></a>Überwachung der Anwendungsleistung  
 Überwachung der Anwendungsleistung Wertentwicklung Verbindung durch die Aufzeichnung von einer Vielzahl von Statistiken. Diese Statistiken können der Entwickler umfassen Elemente wie den folgenden angepasst werden:  
  
|Leistungsindikator|Definition|  
|-------------|----------------|  
|ODBC-feste Verbindung Indikator pro Sekunde|Die Anzahl der tatsächlichen Verbindungen pro Sekunde, die mit dem Server hergestellt werden. Beim ersten Ihrer Umgebung ausgelastet ist, führt geht dieser Leistungsindikator sehr schnell einrichten. Nach wenigen Sekunden löscht er 0 (null). Dies ist die normale Situation an, wenn Verbindungspooling funktioniert. Wenn die Verbindungen mit dem Server festgelegt wurden, werden sie verwendet und im Pool für die Wiederverwendung platziert werden.|  
|ODBC schwer trennen Indikator pro Sekunde|Die Anzahl der hard trennt die Verbindung pro Sekunde an den Server ausgegeben. Hierbei handelt es sich um tatsächliche Verbindungen mit dem Server, die vom Verbindungspooling veröffentlicht werden. Dieser Wert wird 0 (null) erhöhen, wenn Sie alle Clients auf dem System beenden und starten Sie die Verbindungen zu einem Timeout.|  
|ODBC-vorläufig Verbindung Indikator pro Sekunde|Die Anzahl der Verbindungen, die durch den Pool pro Sekunde erfüllt – das heißt, Verbindungen aus dem Pool, die an Benutzer ausgegeben wurden. Dieser Leistungsindikator gibt an, ob Verbindungspooling ausgeführt wird. Abhängig von der Last auf dem Server ist es nicht ungewöhnlich, dass diese Option, um einen weichen zwischen 40 und 60-Verbindungen pro Sekunde angezeigt.|  
|ODBC-vorläufig Trennung Indikator pro Sekunde|Die Anzahl der pro Sekunde, die von den Anwendungen ausgegeben trennt die Verbindung. Wenn die Anwendung frei, oder trennt die Verbindung, wird die Verbindung wieder in den Pool platziert.|  
|ODBC-Indikator für aktuellen aktive Verbindung|Die Anzahl der Verbindungen im Pool, die derzeit verwendet werden.|  
|ODBC-Indikator für aktuellen freien|Die aktuelle Anzahl der freien verfügbaren Verbindungen im Pool. Hierbei handelt es sich um live-Verbindungen, die für die Verwendung verfügbar sind.|  
|Aktive Pools|Die Anzahl der derzeit aktive Pools. Dieser Leistungsindikator wurde in Windows 8-Treiber hinzugefügt, die Verbindungen im Verbindungspool zu verwalten. Weitere Informationen finden Sie unter [Treiberfähiges Verbindungspooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|Erstellte Pools|Die Anzahl der Pools aktiv ist, einschließlich aktiv und entfernte Pools. Dieser Leistungsindikator wurde in Windows 8-Treiber hinzugefügt, die Verbindungen im Verbindungspool zu verwalten. Weitere Informationen finden Sie unter [Treiberfähiges Verbindungspooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
  
 Sie müssen Ihre eigenen Überwachungsparameter angeben. Beispiele für die Überwachung der Anwendungsleistung wurden mit dieser Version von ODBC.
