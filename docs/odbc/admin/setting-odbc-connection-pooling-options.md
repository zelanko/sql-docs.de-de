---
title: Festlegen der Optionen für das ODBC-Verbindungs Pooling | Microsoft-Dokumentation
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
ms.openlocfilehash: 43d4fe1ab363326269daf40375e126b930d2548b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67901644"
---
# <a name="setting-odbc-connection-pooling-options"></a>Festlegen von Optionen für ODBC-Verbindungspooling
Das Verbindungspooling ermöglicht einer Anwendung, eine Verbindung aus einem Pool von Verbindungen zu verwenden, die nicht für jede Verwendung wieder hergestellt werden müssen. Mithilfe der Registerkarte **Verbindungs Pooling** des Dialog Felds **ODBC-Datenquellen-Administrator** können Sie die Leistungsüberwachung aktivieren und deaktivieren. Doppelklicken Sie auf einen Treiber Namen, um den Verbindungs Timeout Zeitraum festzulegen.  
  
 Auf der Treiber Ebene wird das Verbindungspooling durch den Registrierungs Wert "CPTimeout" aktiviert. Diese selektive pro-Treiber-Aktivierung ermöglicht einem Systemadministrator, das Verbindungspooling nur für die Treiber zu aktivieren, die dies unterstützen können. Dies wird erreicht, indem der Standardwert von CPTimeout während des Setup Programms des Treibers festgelegt wird. Doppelklicken Sie auf einen Treiber Namen, um den Verbindungs Timeout Zeitraum festzulegen.  
  
 Weitere Informationen zum Verbindungspooling finden Sie unter [ODBC-Verbindungspooling](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="performance-monitoring"></a>Leistungsüberwachung  
 Die Leistungsüberwachung verfolgt die Verbindungs Leistung, indem eine Reihe von Statistiken aufgezeichnet wird. Diese Statistiken können vom Entwickler angepasst werden, um Elemente wie die folgenden einzuschließen:  
  
|Leistungsindikator|Definition|  
|-------------|----------------|  
|ODBC-hardverbindungs-Counter pro Sekunde|Die Anzahl der tatsächlich auf dem Server vorgenommenen Verbindungen pro Sekunde. Wenn Ihre Umgebung zum ersten Mal stark ausgelastet ist, wird dieser Leistungswert sehr schnell fortgeführt. Nach einigen Sekunden wird der Wert auf 0 (null) gesenkt. Dies ist die normale Situation, wenn Verbindungspooling funktioniert. Wenn die Verbindungen mit dem Server hergestellt wurden, werden Sie verwendet und zur Wiederverwendung in den Pool eingefügt.|  
|ODBC-hardtrennungs-Counter pro Sekunde|Die Anzahl der hart getrennten Verbindungen pro Sekunde, die für den Server ausgegeben werden. Dabei handelt es sich um tatsächliche Verbindungen mit dem Server, die vom Verbindungspooling freigegeben werden. Dieser Wert wird von Null erhöht, wenn Sie alle Clients auf dem System beenden und das Timeout für Verbindungen beginnt.|  
|ODBC-weicher Verbindungs Counter pro Sekunde|Die Anzahl von Verbindungen, die vom Pool pro Sekunde erfüllt werden, d. h. Verbindungen von diesem Pool, die an Benutzer übergeben wurden. Dieser Wert gibt an, ob das Pooling funktioniert. Abhängig von der Auslastung Ihres Servers ist es nicht ungewöhnlich, dass in diesem Fall 40-60 weiche Verbindungen pro Sekunde angezeigt werden.|  
|ODBC-Verbindungs-Counter für weiche Verbindungen pro Sekunde|Die Anzahl von Verbindungen, die pro Sekunde von den Anwendungen ausgegeben werden. Wenn die Anwendung die Verbindung freigibt oder trennt, wird die Verbindung wieder im Pool abgelegt.|  
|ODBC-Leistungs Leistungswert|Die Anzahl der Verbindungen im Pool, die zurzeit verwendet werden.|  
|ODBC-Leistungswert für aktuelle freie Verbindung|Die aktuelle Anzahl der verfügbaren freien Verbindungen im Pool. Dabei handelt es sich um Live Verbindungen, die zur Verwendung verfügbar sind.|  
|Derzeit aktive Pools|Die Anzahl der zurzeit aktiven Pools. Dieser Wert wurde in Windows 8 für Treiber hinzugefügt, die Verbindungen im Verbindungspool verwalten. Weitere Informationen finden Sie unter [Treiber fähiges Verbindungs Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|Erstellte Pools|Die Anzahl aktiver Pools, einschließlich aktiver und entfernter Pools. Dieser Wert wurde in Windows 8 für Treiber hinzugefügt, die Verbindungen im Verbindungspool verwalten. Weitere Informationen finden Sie unter [Treiber fähiges Verbindungs Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
  
 Sie müssen ihre eigenen Überwachungsparameter angeben. Beispiele für die Leistungsüberwachung sind in dieser Version von ODBC enthalten.
