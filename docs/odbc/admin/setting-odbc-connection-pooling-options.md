---
title: Festlegen von ODBC-Verbindungspoolingoptionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1d8e66c506518b77320347ce9120254aa1cae287
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307195"
---
# <a name="setting-odbc-connection-pooling-options"></a>Festlegen von Optionen für ODBC-Verbindungspooling
Das Verbindungspooling ermöglicht es einer Anwendung, eine Verbindung von einem Pool von Verbindungen zu verwenden, die nicht für jede Verwendung wiederhergestellt werden müssen. Sie können die Registerkarte **Verbindungspooling** im Dialogfeld **ODBC-Datenquellenadministrator** verwenden, um die Leistungsüberwachung zu aktivieren und zu deaktivieren. Doppelklicken Sie auf einen Treibernamen, um den Verbindungstimeoutpunkt festzulegen.  
  
 Auf Treiberebene wird das Verbindungspooling durch den Registrierungswert CPTimeout aktiviert. Diese selektive Aktivierung pro Treiber ermöglicht es einem Systemadministrator, das Verbindungspooling nur für die Treiber zu aktivieren, die es unterstützen können. Dies wird erreicht, indem der Standardwert von CPTimeout während des Setupprogramms des Treibers festgelegt wird. Doppelklicken Sie auf einen Treibernamen, um den Verbindungstimeoutpunkt festzulegen.  
  
 Weitere Informationen zum Verbindungspooling finden Sie unter [ODBC Connection Pooling](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="performance-monitoring"></a>Leistungsüberwachung  
 Die Leistungsüberwachung verfolgt die Verbindungsleistung, indem eine Vielzahl von Statistiken aufgezeichnet werden. Diese Statistiken können vom Entwickler so angepasst werden, dass sie Elemente wie die folgenden enthalten:  
  
|Leistungsindikator|Definition|  
|-------------|----------------|  
|ODBC Hard Connection Counter pro Sekunde|Die Anzahl der tatsächlichen Verbindungen pro Sekunde, die mit dem Server hergestellt werden. Wenn Ihre Umgebung zum ersten Mal eine schwere Last trägt, wird dieser Zähler sehr schnell steigen. Nach einigen Sekunden wird es auf Null fallen. Dies ist die normale Situation, wenn das Verbindungspooling funktioniert. Wenn die Verbindungen zum Server hergestellt wurden, werden sie zur Wiederverwendung verwendet und im Pool platziert.|  
|ODBC Hard Disconnect Counter pro Sekunde|Die Anzahl der harten Trennungen pro Sekunde, die an den Server ausgegeben werden. Dies sind tatsächliche Verbindungen mit dem Server, die durch Verbindungspooling freigegeben werden. Dieser Wert wird von Null erhöht, wenn Sie alle Clients auf dem System anhalten und die Verbindungen mit dem Timeout beginnen.|  
|ODBC Soft Connection Counter pro Sekunde|Die Anzahl der Verbindungen, die vom Pool pro Sekunde erfüllt werden, d. h. Verbindungen aus diesem Pool, die an Benutzer übergeben wurden. Dieser Leistungsindikator gibt an, ob das Pooling funktioniert. Je nach Auslastung des Servers ist es nicht ungewöhnlich, dass 40-60 weiche Verbindungen pro Sekunde angezeigt werden.|  
|ODBC Soft Disconnection Counter pro Sekunde|Die Anzahl der von den Anwendungen ausgegebenen Trenngetrennten pro Sekunde. Wenn die Anwendung die Verbindung löst oder trennt, wird die Verbindung wieder im Pool platziert.|  
|ODBC Current Active Connection Counter|Die Anzahl der Verbindungen im Pool, die derzeit verwendet werden.|  
|ODBC Current Free Connection Counter|Die aktuelle Anzahl der im Pool verfügbaren freien Verbindungen. Dies sind Live-Verbindungen, die zur Verwendung zur Verfügung stehen.|  
|Pools derzeit aktiv|Die Anzahl der derzeit aktiven Pools. Dieser Leistungsindikator wurde in Windows 8 für Treiber hinzugefügt, die Verbindungen im Verbindungspool verwalten. Weitere Informationen finden Sie unter [Treiber-Aware Connection Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|Pools erstellt|Die Anzahl der aktiven Pools, einschließlich aktiver und entfernter Pools. Dieser Leistungsindikator wurde in Windows 8 für Treiber hinzugefügt, die Verbindungen im Verbindungspool verwalten. Weitere Informationen finden Sie unter [Treiber-Aware Connection Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
  
 Sie müssen eigene Überwachungsparameter angeben. Beispiele für die Leistungsüberwachung wurden in dieser Version von ODBC enthalten.
