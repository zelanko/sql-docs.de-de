---
title: 'Leistungsindikatoren für die Leistungsobjekte ReportServer: Service und reportserversharepoint: Service | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Server service, performance counters
ms.assetid: 2bcacab2-3a4f-4aae-b123-19d756b9b9ed
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d13cec7bac124a8fb1289de6086ec0326789501e
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53366702"
---
# <a name="performance-counters-for-the-reportserverservice--and-reportserversharepointservice-performance-objects"></a>Leistungsindikatoren für die Leistungsobjekte 'ReportServer:Service' und 'ReportServerSharePoint:Service'
  In diesem Thema werden Leistungsindikatoren für die folgenden [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Leistungsobjekte:  
  
-   `ReportServer:Service`  
  
-   `ReportServerSharePoint:Service`  
  
> [!NOTE]  
>  Mit den Leistungsobjekten werden Ereignisse auf dem lokalen Berichtsserver überwacht. Wenn Sie einen Berichtsserver in einer Bereitstellung für horizontales Skalieren ausführen, beziehen sich die Zahlen auf den aktuellen Server, nicht auf die Bereitstellung für horizontales Skalieren insgesamt.  
  
 Die Leistungsobjekte sind im Windows-Systemmonitor (**Perfmon.exe**) verfügbar. Weitere Informationen finden Sie in der Windows-Dokumentation. [Laufzeit-Profilerstellung](https://msdn.microsoft.com/library/w4bz2147.aspx) (https://msdn.microsoft.com/library/w4bz2147.aspx).  
  
 In diesem Thema:  
  
-   [ReportServer:Service-Leistungsindikatoren (Berichtsserver im einheitlichen Modus)](#bkmk_ReportServer)  
  
-   [ReportServerSharePoint:Service (Berichtsserver im SharePoint-Modus)](#bkmk_ReportServerSharePoint)  
  
-   [Zurückgeben von Listen mithilfe von PowerShell-Cmdlets](#bkmk_powershell)  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint-Modus | Im einheitlichen Modus.  
  
##  <a name="bkmk_ReportServer"></a> ReportServer:Service-Leistungsindikatoren (Berichtsserver im einheitlichen Modus)  
 Das `ReportServer:Service`-Leistungsobjekt enthält eine Reihe von Leistungsindikatoren zum Nachverfolgen HTTP-bezogener und speicherbezogener Ereignisse für eine Berichtsserverinstanz. Dieses Leistungsobjekt erscheint einmalig pro [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Instanz auf dem Computer, und Sie können für jede Instanz Indikatoren zum Leistungsobjekt hinzufügen oder aus dem Leistungsobjekt löschen. Leistungsindikatoren für die Standardinstanz werden im Format  `ReportServer:Service` angezeigt. Leistungsindikatoren für benannte Instanzen werden, in dem Format angezeigt `ReportServer$<` *Instance_name*`>:Service`.  
  
 Die `ReportServer:Service` -Leistungsobjekt ist neu in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], und bietet eine Teilmenge an Indikatoren, die mit Internet Information Services (IIS) enthalten waren und [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] in früheren Versionen von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Diese neuen Leistungsindikatoren sind spezifisch für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], und sie verfolgen HTTP-bezogene Ereignisse für den Berichtsserver nach, wie Anforderungen, Verbindungen und Anmeldeversuche. Darüber hinaus schließt dieses Leistungsobjekt Leistungsindikatoren für die Nachverfolgung von Speicherverwaltungsereignissen ein.  
  
 In der folgenden Tabelle werden die im `ReportServer:Service`-Leistungsobjekt enthaltenen Leistungsindikatoren aufgelistet.  
  
 ![Betrifft PowerShell](../media/rs-powershellicon.jpg "PowerShell related content") Das folgende Windows PowerShell-Skript gibt die Liste der Leistungsindikatoren für CounterSetName zurück.  
  
```  
(get-counter -listset "ReportServer:Service").paths  
```  
  
|Leistungsindikator|Description|  
|-------------|-----------------|  
|`Active connections`|Die Anzahl der Verbindungen, die aktuell auf dem Server aktiv sind.|  
|`Bytes Received Total`|Die Anzahl der vom Server empfangenen Bytes. Dieser Leistungsindikator zählt die Rohbytes, die insgesamt vom Berichts-Manager und Berichtsserver empfangen wurden.|  
|`Bytes Received/sec`|Die Anzahl der vom Server pro Sekunde empfangenen Bytes. Dieser Leistungsindikator wird nur aktualisiert, wenn eine Übertragung abgeschlossen wird. Dies bedeutet, dass der Leistungsindikator zunächst bei 0 bleibt und sich der Wert nach Abschluss der Übertragung erhöht.|  
|`Bytes Sent Total`|Die Anzahl der vom Server gesendeten Bytes. Dieser Leistungsindikator zählt die Rohbytes, die insgesamt vom Berichts-Manager und Berichtsserver gesendet wurden.|  
|`Bytes Sent/sec`|Die Anzahl der vom Server pro Sekunde gesendeten Bytes. Dieser Leistungsindikator wird nur aktualisiert, wenn eine Übertragung abgeschlossen wird. Dies bedeutet, dass der Leistungsindikator zunächst bei 0 bleibt und sich der Wert nach Abschluss der Übertragung erhöht.|  
|`Errors Total`|Die Gesamtanzahl der Fehler, die bei der Verarbeitung von HTTP-Anforderungen aufgetreten sind. Diese Fehler schließen HTTP-Statuscodes in den 400ern und 500ern ein.|  
|`Errors/sec`|Die Gesamtanzahl der Fehler, die bei der Verarbeitung von HTTP-Anforderungen pro Sekunde aufgetreten sind. Diese Fehler schließen HTTP-Statuscodes in den 400ern und 500ern ein.|  
|`Logon Attempts Total`|Die Anzahl der Anmeldeversuche, die von RSWindows-Authentifizierungstypen vorgenommen werden. Zu den RSWindows-Authentifizierungstypen gehören RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos und RSWindowsBasic. Der Wert 0 (null) stellt die benutzerdefinierte Authentifizierung dar.|  
|`Logon Attempts/sec`|Die Rate der Anmeldeversuche.|  
|`Logon Successes Total`|Die Anzahl erfolgreicher Anmeldungen für RSWindows-Authentifizierungstypen. Zu den RSWindows-Authentifizierungstypen gehören RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos und RSWindowsBasic. Der Wert 0 (null) stellt die benutzerdefinierte Authentifizierung dar.|  
|`Logon Successes/sec`|Die Rate erfolgreicher Anmeldungen.|  
|`Memory Pressure State`|Eine der folgenden Zahlen, von 1 bis 5, die den aktuellen Speicherzustand des Servers angeben:<br /><br /> 1: Keine Speicherauslastung<br /><br /> 2: Niedrige Speicherauslastung<br /><br /> 3: Mittlere Speicherauslastung<br /><br /> 4: Hohe Speicherauslastung<br /><br /> 5: Speicherauslastung überschritten|  
|`Memory Shrink Amount`|Die Anzahl der Bytes, die der Server angefordert hat, um den belegten Speicher zu reduzieren.|  
|`Memory Shrink Notifications/sec`|Die Anzahl der Benachrichtigungen, die der Server in der letzten Sekunde ausgibt, um den belegten Speicher zu reduzieren. Dieser Wert gibt an, wie oft der Server einen Speichermangel erfährt.|  
|`Requests Disconnected`|Die Anzahl der Anforderungen, die aufgrund von Kommunikationsfehlern getrennt sind.|  
|`Requests Executing`|Die Anzahl der Anforderungen, die gerade verarbeitet werden.|  
|`Requests Not Authorized`|Die Anzahl der Anforderungen, die mit einem HTTP-401-Statuscode fehlschlagen.|  
|`Requests Rejected`|Die Gesamtanzahl der Anforderungen, die aufgrund unzureichender Serverressourcen nicht verarbeitet wurden. Dieser Leistungsindikator gibt die Anzahl der Anforderungen wieder, die einen HTTP 503-Statuscode zurückgeben, der darauf hinweist, dass der Server vollständig ausgelastet ist.|  
|`Requests Total`|Die Gesamtanzahl der Anforderungen, die vom Berichtsserverdienst seit dem Start empfangen wurden. Dieser Leistungsindikator zählt Anforderungen, die zum Berichts-Manager gesendet wurden, und Anforderungen, die vom Berichts-Manager zum Berichtsserver gesendet wurden.|  
|`Requests/sec`|Die Anzahl der Anforderungen, die pro Sekunde verarbeitet werden. Dieser Wert stellt den aktuellen Durchsatz der Anwendung dar.|  
|`Tasks Queued`|Die Anzahl der Tasks, die darauf warten, dass ein Thread für die Verarbeitung zur Verfügung steht. Jede Anforderung, die an den Berichtsserver gestellt wird, entspricht einer oder mehreren Tasks. Dieser Leistungsindikator stellt nur die Anzahl an Tasks dar, die für die Verarbeitung bereit sind. Er enthält nicht die Anzahl an Tasks, die derzeit ausgeführt werden.|  
  
##  <a name="bkmk_ReportServerSharePoint"></a> ReportServerSharePoint:Service (Berichtsserver im SharePoint-Modus)  
 Die `ReportServerSharePoint:Service` -Leistungsobjekt wurde hinzugefügt, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 ![Betrifft PowerShell](../media/rs-powershellicon.jpg "PowerShell related content") Das folgende Windows PowerShell-Skript gibt die Liste der Leistungsindikatoren für CounterSetName zurück.  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
|Leistungsindikator|  
|-------------|  
|`Memory Pressure State`|  
|`Memory Shrink Amount`|  
|`Memory Shrink Notifications/Sec`|  
  
##  <a name="bkmk_powershell"></a> Zurückgeben von Listen mithilfe von PowerShell-Cmdlets  
 ![Betrifft PowerShell](../media/rs-powershellicon.jpg "PowerShell related content") Das folgende Windows PowerShell-Skript gibt die Liste der Leistungsindikatoren für den CounterSetName „ReportServerSharePoint:Service“ zurück:  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Leistung des Berichtsservers](monitoring-report-server-performance.md)   
 [Leistungsindikatoren für den MSRS 2014 Webdienst und den MSRS 2014 Windows-Dienst, Leistungsobjekte &#40;im einheitlichen Modus&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)   
 [Leistungsindikatoren für den MSRS 2014 Web Service SharePoint Mode und den MSRS 2014 Windows Service SharePoint-Modus, Leistungsobjekte &#40;SharePoint-Modus&#41;]... / performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)  
  
  
