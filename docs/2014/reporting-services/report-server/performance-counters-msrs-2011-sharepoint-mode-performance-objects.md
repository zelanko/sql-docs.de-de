---
title: Leistungsindikatoren für den MSRS 2014 Web Service SharePoint Mode und den MSRS 2014 Windows Service SharePoint-Modus, Leistungsobjekte (SharePoint-Modus) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance counters [Reporting Services]
- counters [Reporting Services]
- Report Server Windows service, performance counters
- RS Windows Service performance object
- Scheduling and Delivery Processor performance object [Reporting Services]
- performance [Reporting Services]
ms.assetid: 70bf6980-7845-4ab5-8b2a-ebf526d811a6
caps.latest.revision: 54
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 05e07f38382c6cdc8892c3ffd90ed63798b6f797
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050484"
---
# <a name="performance-counters-for-the-msrs-2014-web-service-sharepoint-mode-and-msrs-2014-windows-service-sharepoint-mode-performance-objects-sharepoint-mode"></a>Leistungsindikatoren für den MSRS 2014-Webdienst im SharePoint-Modus und den MSRS 2014-Windows-Dienst im SharePoint-Modus, Leistungsobjekte (SharePoint-Modus)
  In diesem Thema werden Leistungsindikatoren für die Leistungsobjekte `MSRS 2014 Web Service SharePoint Mode` und `MSRS 2014 Windows Service SharePoint Mode` beschrieben, die Teil einer Bereitstellung von [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] im SharePoint-Modus sind.  
  
> [!NOTE]  
>  Mit diesen Leistungsobjekten werden Ereignisse auf dem lokalen Berichtsserver überwacht. Wenn Sie einen Berichtsserver in einer Bereitstellung für horizontales Skalieren ausführen, beziehen sich die Zahlen auf den aktuellen Server, nicht auf die Bereitstellung für horizontales Skalieren insgesamt.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint-Modus  
  
 Die Leistungsobjekte sind im Windows-Systemmonitor (**Perfmon.exe**) verfügbar. Weitere Informationen finden Sie in der Windows-Dokumentation. [Laufzeit-Profilerstellung](http://msdn.microsoft.com/library/w4bz2147.aspx).  
  
 **In diesem Thema:**  
  
-   [Leistungsindikatoren für den MSRS 2014 Web Service SharePoint-Modus](#bkmk_webservice)  
  
-   [Leistungsindikatoren für den MSRS 2014 Windows Service SharePoint-Modus](#bkmk_windowsservice)  
  
-   [Zurückgeben von Listen mithilfe von PowerShell-Cmdlets](#bkmk_powershell)  
  
##  <a name="bkmk_webservice"></a> Leistungsindikatoren für den MSRS 2014 Web Service SharePoint-Modus  
 Mit dem `MSRS 2014 Web Service SharePoint Mode`-Leistungsobjekt wird die Berichtsserverleistung überwacht. Dieses Leistungsobjekt enthält eine Reihe von Leistungsindikatoren zum Nachverfolgen der Verarbeitung auf einem Berichtsserver, die in der Regel über interaktive Vorgänge zum Anzeigen von Berichten gestartet wird. Wenn Sie diesen Leistungsindikator einrichten, können Sie den Zähler auf alle Instanzen von anwenden [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] oder spezifische Instanzen auswählen. Diese Leistungsindikatoren werden zurückgesetzt, sobald [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] den Berichtsserver-Webdienst beendet.  
  
 Die folgende Tabelle enthält die Indikatoren, die in enthaltenen der `MSRS 2014 Web Service SharePoint Mode` Leistungsobjekt "".  
  
|Leistungsindikator|Description|  
|-------------|-----------------|  
|`Active Sessions`|Die Anzahl der aktiven Sitzungen. Dieser Leistungsindikator stellt eine kumulierte Anzahl aller durch Berichtsausführungen generierten Browsersitzungen bereit, unabhängig davon, ob sie noch aktiv sind.<br /><br /> Der Leistungsindikator wird verringert, wenn Sitzungsdatensätze entfernt werden. Standardmäßig werden Sitzungen nach einer Inaktivität von zehn Minuten entfernt.|  
|`Cache Hits/Sec`|Die Anzahl der Anforderungen pro Sekunde nach zwischengespeicherten Berichten. Es handelt sich um Anforderungen für erneut gerenderte Berichte, nicht um Anforderungen für direkt aus dem Cache verarbeitete Berichte. (Siehe `Total Cache Hits` weiter unten in diesem Thema.)|  
|`Cache Hits/Sec (Semantic Models)`|Die Anzahl der Anforderungen für ein zwischengespeichertes Modell pro Sekunde. Es handelt sich um Anforderungen für erneut gerenderte Berichte, nicht um Anforderungen für direkt aus dem Cache verarbeitete Berichte.|  
|`Cache Misses/Sec`|Die Anzahl der Anforderungen pro Sekunde, bei denen kein Bericht aus dem Cache zurückgegeben werden konnte. Stellen Sie mithilfe dieses Leistungsindikators fest, ob die für die Zwischenspeicherung (Datenträger oder Arbeitsspeicherung) verwendeten Ressourcen ausreichend sind.|  
|`Cache Misses/Sec (Semantic Models)`|Die Anzahl der Anforderungen pro Sekunde, bei denen kein Modell aus dem Cache zurückgegeben werden konnte. Stellen Sie mithilfe dieses Leistungsindikators fest, ob die für die Zwischenspeicherung (Datenträger oder Arbeitsspeicherung) verwendeten Ressourcen ausreichend sind.|  
|`First Session Requests/Sec`|Die Anzahl neuer Benutzersitzungen, die pro Sekunde aus dem Berichtsservercache gestartet werden.|  
|`Memory Cache Hits/Sec`|Die Angabe, wie oft pro Sekunde Berichte aus dem In-Memory-Cache abgerufen werden. Der*Arbeitsspeichercache* ist ein Bestandteil des Caches, der Berichte im CPU-Arbeitsspeicher speichert. Wenn der In-Memory-Cache verwendet wird, ruft der Berichtsserver keinen zwischengespeicherten Inhalt von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ab.|  
|`Memory Cache Misses/Sec`|Die Anzahl, wie oft Berichte pro Sekunde nicht aus dem Arbeitsspeichercache abgerufen werden konnten.|  
|`Next Session Requests/Sec`|Die Anzahl der Anforderungen für Berichte, die in einer vorhandenen Sitzung geöffnet sind, pro Sekunde (z. B. Berichte, die aus der Momentaufnahme einer Sitzung gerendert wurden).|  
|`Report Requests`|Die Anzahl der Berichte, die derzeit aktiv sind und vom Berichtsserver verarbeitet werden.|  
|`Reports Executed/Sec`|Die Anzahl der erfolgreichen Berichtsausführungen pro Sekunde. Dieser Leistungsindikator stellt Statistiken zum Berichtsumfang bereit. Verwenden Sie diesen Leistungsindikator zusammen mit `Request/Sec` berichtsausführung mit den berichtsanforderungen zu vergleichen, die aus dem Cache zurückgegeben werden können.|  
|`Requests/Sec`|Die Anzahl der Anforderungen pro Sekunde, die an den Berichtsserver gesendet werden. Dieser Leistungsindikator verfolgt alle Anforderungstypen, die vom Berichtsserver verarbeitet werden.|  
|`Total Cache Hits`|Die Gesamtzahl der Anforderungen nach Berichten aus dem Cache, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird.|  
|`Total Cache Hits (Semantic Models)`|Die Gesamtanzahl der Anforderungen für ein Modell aus dem Cache, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von ASP.NET beendet wird.|  
|`Total Cache Misses`|Die Anzahl, wie oft ein Bericht insgesamt nicht aus dem Cache zurückgegeben werden konnte, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird. Mit diesem Leistungsindikator bestimmen Sie, ob ausreichend Speicherplatz und Arbeitsspeicher vorhanden sind.|  
|`Total Cache Misses (Semantic Models)`|Die Gesamthäufigkeit, mit der ein Modell nicht aus dem Cache zurückgegeben werden konnte, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von ASP.NET beendet wird. Mit diesem Leistungsindikator bestimmen Sie, ob ausreichend Speicherplatz und Arbeitsspeicher vorhanden sind.|  
|`Total Memory Cache Hits`|Die Gesamtzahl der zwischengespeicherten Berichte, die aus dem Arbeitsspeichercache zurückgegeben wurden, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird. Der*In-Memory-Cache* ist ein Bestandteil des Caches, der Berichte im CPU-Speicher speichert. Wenn der In-Memory-Cache verwendet wird, ruft der Berichtsserver keinen zwischengespeicherten Inhalt von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ab.|  
|`Total Memory Cache Misses`|Die Gesamtzahl der Cachefehlversuche für den In-Memory-Cache, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird.|  
|`Total Processing Failures`|Die Anzahl der Fehler bei der Anforderungsverarbeitung im Berichtsserver-Webdienst.|  
|`Total Rejected Threads`|Die Gesamtanzahl der für die asynchrone Verarbeitung abgelehnten Threads, die anschließend im selben Thread als synchrone Prozesse verarbeitet wurden. Jede Datenquelle wird in einem Thread verarbeitet. Falls die Anzahl der Threads die Kapazität überschreitet, werden Threads für die asynchrone Verarbeitung abgelehnt und seriell verarbeitet.|  
|`Total Reports Executed`|Die Gesamtzahl der erfolgreich ausgeführten Berichte, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird.|  
|`Total Requests`|Die Gesamtzahl der Anforderungen an den Berichtsserver, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird.|  
  
##  <a name="bkmk_windowsservice"></a> Leistungsindikatoren für den MSRS 2014 Windows Service SharePoint-Modus  
 Mit diesem `MSRS 2014 Windows Service SharePoint Mode`-Leistungsobjekt wird der Berichtsserver-Windows-Dienst überwacht. Das Leistungsobjekt enthält eine Reihe von Leistungsindikatoren zum Nachverfolgen der Berichtsverarbeitung, die über geplante Vorgänge gestartet wird. Zu geplanten Vorgängen zählen Abonnierung und Übermittlung, Momentaufnahmen zur Berichtsausführung und der Berichtsverlauf. Wenn Sie diesen Leistungsindikator einrichten, können Sie den Zähler auf alle Instanzen von anwenden [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] oder spezifische Instanzen auswählen.  
  
 Die folgende Tabelle enthält die Leistungsindikatoren, die in enthalten sind die `MSRS 2014 Windows Service SharePoint mode` Leistungsobjekt "".  
  
|Leistungsindikator|Description|  
|-------------|-----------------|  
|`Active Sessions`|Die Anzahl der aktiven Sitzungen, die in der Berichtsserver-Datenbank gespeichert sind. Dieser Leistungsindikator liefert die Gesamtanzahl aller verfügbaren Browsersitzungen, die aus Berichtsabonnements generiert wurden, unabhängig davon, ob sie noch aktiv sind oder nicht.|  
|`Alerting: event queue length`||  
|`Alerting: events processed - CreateSchedule`||  
|`Alerting: events processed – Delete schedule`||  
|`Alerting: events processed – DeliverAlert`||  
|`Alerting: events processed – FireAlert`||  
|`Alerting: events processed – FireSchedule`||  
|`Alerting: events processed – GenerateAlert`||  
|`Alerting: events processed – UpdateSchedule`||  
|`Cache Flushes/Sec`|Die Anzahl der Cacheleerungen pro Sekunde.|  
|`Cache Hits/Sec`|Die Anzahl der Anforderungen pro Sekunde nach zwischengespeicherten Berichten. Es handelt sich um Anforderungen für erneut gerenderte Berichte, nicht um Anforderungen für direkt aus dem Cache verarbeitete Berichte. (Siehe `Total Cache Hits` weiter unten in diesem Thema.)|  
|`Cache Hits/Sec (Semantic Models)`|Die Anzahl der Anforderungen für zwischengespeicherte Modelle pro Sekunde.|  
|`Cache Misses/Sec`|Die Anzahl der Anforderungen pro Sekunde, bei denen kein Bericht aus dem Cache zurückgegeben werden konnte. Stellen Sie mithilfe dieses Leistungsindikators fest, ob die für die Zwischenspeicherung (Datenträger oder Arbeitsspeicherung) verwendeten Ressourcen ausreichend sind.|  
|`Cache Misses/Sec (Semantic Models)`|Die Anzahl der Anforderungen pro Sekunde, bei denen kein Modell aus dem Cache zurückgegeben werden konnte. Stellen Sie mithilfe dieses Leistungsindikators fest, ob die für die Zwischenspeicherung (Datenträger oder Arbeitsspeicherung) verwendeten Ressourcen ausreichend sind.|  
|`Delivers/Sec`|Die Anzahl der Berichtsübermittlungen pro Sekunde, von jeder Übermittlungserweiterung.|  
|`Events/Sec`|Die Anzahl der pro Sekunde verarbeiteten Ereignisse. Den überwachten Ereignissen gehören `SnapshotUpdated` und `TimedSubscription`.|  
|`First Session Requests/Sec`|Die Anzahl neuer Berichtsausführungssitzungen, die pro Sekunde erstellt wurden.|  
|`Memory Cache Hits/Sec`|Die Angabe, wie oft pro Sekunde Berichte aus dem In-Memory-Cache abgerufen werden. Der*Arbeitsspeichercache* ist ein Bestandteil des Caches, der Berichte im CPU-Arbeitsspeicher speichert. Wenn der In-Memory-Cache verwendet wird, ruft der Berichtsserver keinen zwischengespeicherten Inhalt von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ab.|  
|`Memory Cache Misses/Sec`|Die Angabe, wie oft Berichte pro Sekunde nicht aus dem In-Memory-Cache abgerufen werden können.|  
|`Next Session Requests/Sec`|Die Anzahl der Anforderungen für Berichte, die in einer vorhandenen Sitzung geöffnet sind, pro Sekunde (z. B. Berichte, die aus der Momentaufnahme einer Sitzung gerendert wurden).|  
|`Report Requests`|Die Anzahl der Berichte, die derzeit aktiv sind und vom Berichtsserver verarbeitet werden. Verwenden Sie diesen Leistungsindikator, um die Zwischenspeicherungsstrategie auszuwerten. Es können u. U. wesentlich mehr Anforderungen als generierte Berichte vorhanden sein.|  
|`Reports Executed/Sec`|Die Anzahl der erfolgreich generierten Berichte pro Sekunde.|  
|`Requests/Sec`|Die Gesamtanzahl erfolgreicher Anforderungen, die vom Berichtsserverdienst pro Sekunde verarbeitet wurden.|  
|`Snapshot Updates/Sec`|Die Gesamtanzahl der Updates von Berichtsausführungs-Momentaufnahmen pro Sekunde.|  
|`Total App Domain Recycles`|Die Gesamtzahl der Anwendungsdomänenzyklen, nachdem der Berichtsserver-Windows-Dienst gestartet wurde.|  
|**Cacheleerungen gesamt**|Die Gesamtzahl der Cacheupdates des Berichtsservers, nachdem der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird. Finden Sie unter `Cache Flushes/Sec`.|  
|`Total Cache Hits`|Die Gesamtzahl der Anforderungen nach direkt aus dem Cache verarbeiteten Berichten, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird. Finden Sie unter `Cache Hits/Sec`.|  
|`Total Cache Hits (Semantic Models)`|Die Gesamtanzahl der Modellanforderungen, die direkt aus dem Cache verarbeitet wurden, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|  
|`Total Cache Misses`|Die Gesamtanzahl, wie oft ein Bericht nicht aus dem Cache zurückgegeben werden konnte, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird. Finden Sie unter `Cache Misses/Sec`.|  
|`Total Cache Misses (Semantic Models)`|Die Gesamthäufigkeit, mit der ein Modell nicht aus dem Cache zurückgegeben werden konnte, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|  
|`Total Deliveries`|Die Gesamtzahl der Berichte, die vom Prozessor für Zeitplanung und Übermittlung für alle Übermittlungserweiterungen übermittelt wurden. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|  
|`Total Events`|Die Gesamtzahl der Ereignisse, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|  
|`Total Memory Cache Hits`|Die Gesamtzahl der zwischengespeicherten Berichte, die aus dem In-Memory-Cache zurückgegeben wurden, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|  
|`Total Memory Cache Misses`|Die Gesamtzahl der Cachefehlversuche für den In-Memory-Cache, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|  
|`Total Processing Failures`|Die Anzahl der Fehler bei der Anforderungsverarbeitung für den Berichtsserver-Windows-Dienst.|  
|`Total Rejected Threads`|Die Gesamtanzahl der für die asynchrone Verarbeitung abgelehnten Threads, die anschließend im selben Thread als synchroner Prozess verarbeitet wurden. Bei mittlerer bis starker Auslastung wird dieser Leistungsindikator laufend erhöht.|  
|`Total Reports Executed`|Die Gesamtzahl der ausgeführten Berichte.|  
|`Total Requests`|Die Gesamtzahl der erfolgreich ausgeführten Berichte, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|  
|`Total Snapshot Updates`|Die Gesamtanzahl der Updates von Berichtsausführungs-Momentaufnahmen.|  
  
##  <a name="bkmk_powershell"></a> Zurückgeben von Listen mithilfe von PowerShell-Cmdlets  
 ![Betrifft PowerShell](../media/rs-powershellicon.jpg "PowerShell related content") Das folgende Windows PowerShell-Skript gibt die Indikatorensätze zurück, bei denen CounterSetName mit „msr“ beginnt:  
  
```  
get-counter -listset msr*  
Returns a list with the following information  
CounterSetName     : MSRS 2014 Windows Service SharePoint Mode  
CounterSetName     : MSRS 2014 Web Service SharePoint Mode  
```  
  
 Das folgende Windows PowerShell-Skript gibt die Liste der Leistungsindikatoren für CounterSetName "MSRS 2014 Windows Service SharePoint Mode" zurück.  
  
```  
(get-counter -listset "MSRS 2014 Windows Service SharePoint Mode").paths  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Leistung des Berichtsservers](monitoring-report-server-performance.md)   
 [Leistungsindikatoren für den MSRS 2014 Webdienst und den MSRS 2014 Windows-Dienst, Leistungsobjekte &#40;im einheitlichen Modus&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)  
  
  