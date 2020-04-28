---
title: Leistungsindikatoren für den MSRS 2014-Webdienst und den MSRS 2014-Windows-Dienst, Leistungs Objekte (einheitlicher Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Reporting Services]
- Report Server Web service, performance counters
- Reporting Services performance object
- RS Web Service performance object
- counters [Reporting Services]
- performance [Reporting Services]
ms.assetid: c642fc4f-8734-4626-a194-42ac9cd8e2ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9792dd40381c9870198ccaf0c4a6457aae19def2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175189"
---
# <a name="performance-counters-for-the-msrs-2014-web-service-and-msrs-2014-windows-service-performance-objects-native-mode"></a>Leistungsindikatoren für den MSRS 2014-Webdienst und den MSRS 2014-Windows-Dienst, Leistungsobjekte (einheitlicher Modus)
  In diesem Thema werden Leistungsindikatoren für die Leistungsobjekte `MSRS 2014 Web Service` und `MSRS 2014 Windows Service` beschrieben.

> [!NOTE]
>  Mit diesen Leistungsobjekten werden Ereignisse auf dem lokalen Berichtsserver überwacht. Wenn Sie einen Berichtsserver in einer Bereitstellung für horizontales Skalieren ausführen, beziehen sich die Zahlen auf den aktuellen Server, nicht auf die Bereitstellung für horizontales Skalieren.

 **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] im einheitlichen Modus

 Die Leistungsobjekte sind im Windows-Systemmonitor (**Perfmon.exe**) verfügbar. Weitere Informationen finden Sie in der Windows-Dokumentation, [Erstellung von Laufzeitprofilen](https://msdn.microsoft.com/library/w4bz2147.aspx) (https://msdn.microsoft.com/library/w4bz2147.aspx).

 Informationen zu den Leistungsindikatoren im SharePoint-Modus finden Sie unter [Leistungsindikatoren für den MSRS 2014-Webdienst im SharePoint-Modus und den MSRS 2014-Windows-Dienst im SharePoint-Modus &#40;im SharePoint-Modus&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md).

 **In diesem Thema:**

-   [Leistungsindikatoren für den MSRS 2014-Webdienst](#bkmk_webservice)

-   [Leistungsindikatoren für den MSRS 2014-Windows-Dienst](#bkmk_windowsservice)

-   [Zurückgeben von Listen mithilfe von PowerShell-Cmdlets](#bkmk_powershell)

##  <a name="msrs-2014-web-service-performance-counters"></a><a name="bkmk_webservice"></a>Leistungsindikatoren für den MSRS 2014-Webdienst
 Mit dem `MSRS 2014 Web Service`-Leistungsobjekt wird die Berichtsserverleistung überwacht. Dieses Leistungsobjekt enthält eine Reihe von Leistungsindikatoren zum Nachverfolgen der Verarbeitung auf einem Berichtsserver, die in der Regel über interaktive Vorgänge zum Anzeigen von Berichten gestartet wird. Bei der Einrichtung dieses Leistungsindikators können Sie diesen auf alle Instanzen von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] anwenden oder spezifische Instanzen auswählen. Diese Leistungsindikatoren werden zurückgesetzt, sobald [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] den Berichtsserver-Webdienst beendet.

 In der folgenden Tabelle werden die im `MSRS 2014 Web Service`-Leistungsobjekt enthaltenen Leistungsindikatoren aufgelistet.

|Leistungsindikator|BESCHREIBUNG|
|-------------|-----------------|
|`Active Sessions`|Die Anzahl der aktiven Sitzungen. Dieser Leistungsindikator stellt eine kumulierte Anzahl aller durch Berichtsausführungen generierten Browsersitzungen bereit, unabhängig davon, ob sie noch aktiv sind.<br /><br /> Der Leistungsindikator wird verringert, wenn Sitzungsdatensätze entfernt werden. Standardmäßig werden Sitzungen nach einer Inaktivität von zehn Minuten entfernt.|
|`Cache Hits/Sec`|Die Anzahl der Anforderungen pro Sekunde nach zwischengespeicherten Berichten. Die Anforderungen gelten für erneut gerenderte Berichte und nicht für Anforderungen für direkt aus dem Cache verarbeitete Berichte. (Weitere Informationen finden Sie unter `Total Cache Hits` weiter unten in diesem Thema.)|
|`Cache Hits/Sec (Semantic Models)`|Die Anzahl der Anforderungen für ein zwischengespeichertes Modell pro Sekunde. Die Anforderungen gelten für erneut gerenderte Berichte und nicht für Anforderungen für direkt aus dem Cache verarbeitete Berichte.|
|`Cache Misses/Sec`|Die Anzahl der Anforderungen pro Sekunde, bei denen kein Bericht aus dem Cache zurückgegeben werden konnte. Stellen Sie mithilfe dieses Leistungsindikators fest, ob die für die Zwischenspeicherung (Datenträger oder Arbeitsspeicherung) verwendeten Ressourcen ausreichend sind.|
|`Cache Misses/Sec (Semantic Models)`|Die Anzahl der Anforderungen pro Sekunde, bei denen kein Modell aus dem Cache zurückgegeben werden konnte. Stellen Sie mithilfe dieses Leistungsindikators fest, ob die für die Zwischenspeicherung (Datenträger oder Arbeitsspeicherung) verwendeten Ressourcen ausreichend sind.|
|`First Session Requests/Sec`|Die Anzahl neuer Benutzersitzungen, die pro Sekunde aus dem Berichtsservercache gestartet werden.|
|`Memory Cache Hits/Sec`|Die Angabe, wie oft pro Sekunde Berichte aus dem In-Memory-Cache abgerufen werden. Der*Arbeitsspeichercache* ist ein Bestandteil des Caches, der Berichte im CPU-Arbeitsspeicher speichert. Wenn der In-Memory-Cache verwendet wird, ruft der Berichtsserver keinen zwischengespeicherten Inhalt von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ab.|
|`Memory Cache Misses/Sec`|Die Anzahl, wie oft Berichte pro Sekunde nicht aus dem Arbeitsspeichercache abgerufen werden konnten.|
|`Next Session Requests/Sec`|Die Anzahl der Anforderungen für Berichte, die in einer vorhandenen Sitzung geöffnet sind, pro Sekunde (z. B. Berichte, die aus der Momentaufnahme einer Sitzung gerendert wurden).|
|`Report Requests`|Die Anzahl der Berichte, die derzeit aktiv sind und vom Berichtsserver verwaltet werden.|
|`Reports Executed/Sec`|Die Anzahl der erfolgreichen Berichtsausführungen pro Sekunde. Dieser Leistungsindikator stellt Statistiken zum Berichtsumfang bereit. Verwenden Sie diesen Leistungsindikator zusammen mit `Request/Sec`, um die Berichtsausführung mit den Berichtsanforderungen zu vergleichen, die aus dem Cache zurückgegeben werden können.|
|`Requests/Sec`|Die Anzahl der Anforderungen pro Sekunde, die an den Berichtsserver gesendet werden. Mit diesem Leistungsindikator werden alle Anforderungstypen nachverfolgt, die vom Berichtsserver verwaltet werden.|
|`Total Cache Hits`|Die Gesamtzahl der Anforderungen nach Berichten aus dem Cache, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird.|
|`Total Cache Hits (Semantic Models)`|Die Gesamtanzahl der Anforderungen für ein Modell aus dem Cache, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von ASP.NET beendet wird.|
|`Total Cache Misses`|Die Anzahl, wie oft ein Bericht insgesamt nicht aus dem Cache zurückgegeben werden konnte, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird. Mit diesem Leistungsindikator bestimmen Sie, ob ausreichend Speicherplatz und Arbeitsspeicher vorhanden sind.|
|`Total Cache Misses (Semantic Models)`|Die Gesamthäufigkeit, mit der ein Modell nicht aus dem Cache zurückgegeben werden konnte, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von ASP.NET beendet wird. Mit diesem Leistungsindikator bestimmen Sie, ob ausreichend Speicherplatz und Arbeitsspeicher vorhanden sind.|
|`Total Memory Cache Hits`|Die Gesamtzahl der zwischengespeicherten Berichte, die aus dem Arbeitsspeichercache zurückgegeben wurden, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird. Der*Arbeitsspeichercache* ist ein Bestandteil des Caches, der Berichte im CPU-Arbeitsspeicher speichert. Wenn der In-Memory-Cache verwendet wird, ruft der Berichtsserver keinen zwischengespeicherten Inhalt von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ab.|
|`Total Memory Cache Misses`|Die Gesamtzahl der Cachefehlversuche für den In-Memory-Cache, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird.|
|`Total Processing Failures`|Die Anzahl der Fehler bei der Anforderungsverarbeitung für den Berichtsserver-Webdienst.|
|`Total Rejected Threads`|Die Gesamtanzahl der für die asynchrone Verarbeitung abgelehnten Threads, die anschließend im selben Thread als synchrone Prozesse verarbeitet wurden. Jede Datenquelle wird in einem Thread verarbeitet. Falls die Anzahl der Threads die Kapazität überschreitet, werden Threads für die asynchrone Verarbeitung abgelehnt und seriell verarbeitet.|
|`Total Reports Executed`|Die Gesamtzahl der erfolgreich ausgeführten Berichte, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird.|
|`Total Requests`|Die Gesamtzahl der Anforderungen an den Berichtsserver, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, sobald der Berichtsserver-Webdienst von [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] beendet wird.|

##  <a name="msrs-2014-windows-service-performance-counters"></a><a name="bkmk_windowsservice"></a>Leistungsindikatoren für den MSRS 2014-Windows-Dienst
 Mit dem `MSRS 2014 Windows Service`-Leistungsobjekt wird der Berichtsserver-Windows-Dienst überwacht. Das Leistungsobjekt enthält eine Reihe von Leistungsindikatoren zum Nachverfolgen der Berichtsverarbeitung, die über geplante Vorgänge gestartet wird. Zu geplanten Vorgängen zählen Abonnierung und Übermittlung, Momentaufnahmen zur Berichtsausführung und der Berichtsverlauf. Bei der Einrichtung dieses Leistungsindikators können Sie diesen auf alle Instanzen von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] anwenden oder spezifische Instanzen auswählen.

 In der folgenden Tabelle werden die im `MSRS 2014 Windows Service`-Leistungsobjekt enthaltenen Leistungsindikatoren aufgelistet.

|Leistungsindikator|BESCHREIBUNG|
|-------------|-----------------|
|`Active Sessions`|Die Anzahl der aktiven Sitzungen, die in der Berichtsserver-Datenbank gespeichert sind. Dieser Leistungsindikator liefert die Gesamtanzahl aller verfügbaren Browsersitzungen, die aus Berichtsabonnements generiert wurden, unabhängig davon, ob sie noch aktiv sind oder nicht.|
|`Cache Flushes/Sec`|Die Anzahl der Cacheleerungen pro Sekunde.|
|`Cache Hits/Sec`|Die Anzahl der Anforderungen pro Sekunde nach zwischengespeicherten Berichten. Die Anforderungen gelten für erneut gerenderte Berichte und nicht für Anforderungen für direkt aus dem Cache verarbeitete Berichte. (Weitere Informationen finden Sie unter `Total Cache Hits` weiter unten in diesem Thema.)|
|`Cache Hits/Sec (Semantic Models)`|Die Anzahl der Anforderungen für zwischengespeicherte Modelle pro Sekunde.|
|`Cache Misses/Sec`|Die Anzahl der Anforderungen pro Sekunde, bei denen kein Bericht aus dem Cache zurückgegeben werden konnte. Stellen Sie mithilfe dieses Leistungsindikators fest, ob die für die Zwischenspeicherung (Datenträger oder Arbeitsspeicherung) verwendeten Ressourcen ausreichend sind.|
|`Cache Misses/Sec (Semantic Models)`|Die Anzahl der Anforderungen pro Sekunde, bei denen kein Modell aus dem Cache zurückgegeben werden konnte. Stellen Sie mithilfe dieses Leistungsindikators fest, ob die für die Zwischenspeicherung (Datenträger oder Arbeitsspeicherung) verwendeten Ressourcen ausreichend sind.|
|`Delivers/Sec`|Die Anzahl der Berichtsübermittlungen pro Sekunde, von jeder Übermittlungserweiterung.|
|`Events/Sec`|Die Anzahl der pro Sekunde verarbeiteten Ereignisse. Zu den überwachten Ereignissen gehören `SnapshotUpdated` und `TimedSubscription`.|
|`First Session Requests/Sec`|Die Anzahl neuer Berichtsausführungssitzungen, die pro Sekunde erstellt wurden.|
|`Memory Cache Hits/Sec`|Die Angabe, wie oft pro Sekunde Berichte aus dem In-Memory-Cache abgerufen werden. Der*Arbeitsspeichercache* ist ein Bestandteil des Caches, der Berichte im CPU-Arbeitsspeicher speichert. Wenn der In-Memory-Cache verwendet wird, ruft der Berichtsserver keinen zwischengespeicherten Inhalt von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ab.|
|`Memory Cache Misses/Sec`|Die Angabe, wie oft Berichte pro Sekunde nicht aus dem In-Memory-Cache abgerufen werden können.|
|`Next Session Requests/Sec`|Die Anzahl der Anforderungen für Berichte, die in einer vorhandenen Sitzung geöffnet sind, pro Sekunde (z. B. Berichte, die aus der Momentaufnahme einer Sitzung gerendert wurden).|
|`Report Requests`|Die Anzahl der Berichte, die derzeit aktiv sind und vom Berichtsserver verwaltet werden. Verwenden Sie diesen Leistungsindikator, um die Zwischenspeicherungsstrategie auszuwerten. Es können u. U.mehr Anforderungen als generierte Berichte vorhanden sein.|
|`Reports Executed/Sec`|Die Anzahl der erfolgreich generierten Berichte pro Sekunde.|
|`Requests/Sec`|Die Gesamtanzahl erfolgreicher Anforderungen, die vom Berichtsserverdienst pro Sekunde verarbeitet wurden.|
|`Snapshot Updates/Sec`|Die Gesamtanzahl der Updates von Berichtsausführungs-Momentaufnahmen pro Sekunde.|
|`Total App Domain Recycles`|Die Gesamtzahl der Anwendungsdomänenzyklen, nachdem der Berichtsserver-Windows-Dienst gestartet wurde.|
|**Cacheleerungen gesamt**|Die Gesamtzahl der Cacheupdates des Berichtsservers, nachdem der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird. Siehe `Cache Flushes/Sec`.|
|`Total Cache Hits`|Die Gesamtzahl der Anforderungen nach direkt aus dem Cache verarbeiteten Berichten, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird. Siehe `Cache Hits/Sec`.|
|`Total Cache Hits (Semantic Models)`|Die Gesamtanzahl der Anforderungen für direkt aus dem Cache verarbeitete Modelle, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird. Siehe `Cache Hits/Sec`.|
|`Total Cache Misses`|Die Gesamtanzahl, wie oft ein Bericht nicht aus dem Cache zurückgegeben werden konnte, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird. Siehe `Cache Misses/Sec`.|
|`Total Cache Misses (Semantic Models)`|Die Gesamthäufigkeit, mit der ein Modell nicht aus dem Cache zurückgegeben werden konnte, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|
|`Total Deliveries`|Die Gesamtanzahl der Berichte, die durch den Prozessor für Zeitplanung und Übermittlung für alle Übermittlungserweiterungen übermittelt wurden. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|
|`Total Events`|Die Gesamtanzahl der Ereignisse, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|
|`Total Memory Cache Hits`|Die Gesamtanzahl der zwischengespeicherten Berichte, die aus dem Arbeitsspeichercache zurückgegeben wurden, nachdem der Berichtsserver-Windows-Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|
|`Total Memory Cache Misses`|Die Gesamtzahl der Cachefehlversuche für den In-Memory-Cache, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|
|`Total Processing Failures`|Die Anzahl der Fehler bei der Anforderungsverarbeitung im Berichtsserver-Windows-Dienst.|
|`Total Rejected Threads`|Die Gesamtanzahl der für die asynchrone Verarbeitung abgelehnten Threads, die anschließend im selben Thread als synchroner Prozess verarbeitet wurden. Bei mittlerer bis starker Auslastung wird dieser Leistungsindikator laufend erhöht.|
|`Total Reports Executed`|Die Gesamtzahl der ausgeführten Berichte.|
|`Total Requests`|Die Gesamtzahl der erfolgreich ausgeführten Berichte, seit der Dienst gestartet wurde. Dieser Leistungsindikator wird zurückgesetzt, wenn die Anwendungsdomäne wiederverwendet wird.|
|`Total Snapshot Updates`|Die Gesamtanzahl der Updates für Berichtsausführungs-Momentaufnahmen.|

##  <a name="use-powershell-cmdlets-to-return-lists"></a><a name="bkmk_powershell"></a>Zurückgeben von Listen mithilfe von PowerShell-Cmdlets
 ![PowerShell-Inhalt](../media/rs-powershellicon.jpg "PowerShell-Inhalt") Das folgende Windows PowerShell-Skript gibt die Indikatorensätze zurück, bei denen CounterSetName mit „msr“ beginnt:

```powershell
Get-Counter -ListSet msr*
```

 Das folgende Windows PowerShell-Skript gibt die Liste der Leistungsindikatoren für CounterSetName zurück.

```powershell
(Get-Counter -ListSet "MSRS 2014 Windows Service").Paths
```

## <a name="see-also"></a>Weitere Informationen
 [Überwachen der Leistungsindikatoren für den Berichts Server für den MSRS 2014-Webdienst im SharePoint-Modus und den MSRS 2014-Windows-Dienst im SharePoint-Modus &#40;im SharePoint-Modus&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md) [Leistungsindikatoren für die Leistungs Objekte Report Server: Service und Report Server SharePoint: Service](performance-counters-reportserver-service-performance-objects.md) [Monitoring Report Server Performance](monitoring-report-server-performance.md)
