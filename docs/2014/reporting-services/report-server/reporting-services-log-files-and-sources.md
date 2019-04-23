---
title: Reporting Services-Protokolldateien und Quellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [Reporting Services], log files
- logs [Reporting Services]
- logs [Reporting Services], about log files
- report servers [Reporting Services], log files
- report server log files
- files [Reporting Services], logs
ms.assetid: 80ef0acc-cbef-49d0-87e7-844e3ce19604
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 417c0aa5a444c6d73c76b11aa21756400ac891c1
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59963506"
---
# <a name="reporting-services-log-files-and-sources"></a>Reporting Services-Protokolldateien und -Quellen
  Ein[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Berichtsserver und eine Berichtsserverumgebung unterstützen eine Vielzahl von Protokollzielen, um Informationen zu Servervorgängen und zum Status aufzuzeichnen. Es gibt zwei grundlegende Kategorien von Protokollierung: Protokollierung der Ausführung und Ablaufprotokollierung. Die Protokollierung der Ausführung schließt Informationen zu Berichtsausführungsstatistiken, Überwachung, Leistungsdiagnose und Optimierung ein. Die Ablaufprotokollierung enthält Informationen zu Fehlermeldungen und allgemeiner Diagnose.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] im SharePoint-Modus | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] im einheitlichen Modus  
  
 Die folgende Tabelle enthält Links zu zusätzlichen Informationen zu den Protokollen, einschließlich ihrer Speicherorte und der Vorgehensweise zum Anzeigen ihrer Inhalte.  
  
|Log|Description|  
|---------|-----------------|  
|[Berichtsserverausführungsprotokoll und die ExecutionLog3-Ansicht](report-server-executionlog-and-the-executionlog3-view.md)|Das Ausführungsprotokoll ist in der Berichtsserverdatenbank gespeicherte SQL Server-Sicht.<br /><br /> Das Berichtsserver-Ausführungsprotokoll enthält Daten zu bestimmten Berichten, beispielsweise, wann ein Bericht ausgeführt wurde, wer ihn ausgeführt hat, wohin er übermittelt wurde und welches Renderingformat verwendet wurde.|  
|SharePoint-Ablaufverfolgungsprotokoll|Für Berichtsserver, die in SharePoint ausgeführt werden, enthält das SharePoint-Ablaufverfolgungsprotokoll [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Informationen. Sie können auch für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] spezifische Informationen für den vereinheitlichten SharePoint-Protokollierungsdienst (SharePoint Unified Logging Service) konfigurieren. Weitere Informationen finden Sie unter [Aktivieren von Reporting Services-Ereignissen für das SharePoint-Ablaufverfolgungsprotokoll &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)|  
|[Report Server Service Trace Log (Berichtsserverdienst-Ablaufverfolgungsprotokoll)](report-server-service-trace-log.md)|Das Ablaufverfolgungsprotokoll des Diensts enthält sehr detaillierte Informationen, die beim Debuggen einer Anwendung oder beim Analysieren eines Problems oder Ereignisses hilfreich sind.<br /><br /> `C:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles`|  
|[Berichtsserver-HTTP-Protokoll](report-server-http-log.md)|Die HTTP-Protokolldatei zeichnet alle HTTP-Anforderungen und -Antworten auf, die vom Report Server-Webdienst und Berichts-Manager verarbeitet werden.|  
|[Windows-Anwendungsprotokoll](windows-application-log.md)|Das Microsoft Windows-Anwendungsprotokoll enthält Informationen zu Berichtsserverereignissen.|  
|Windows-Leistungsprotokolle|Windows-Leistungsprotokolle enthalten Daten zur Berichtsserverleistung. Sie können Leistungsprotokolle erstellen und anschließend Leistungsindikatoren auswählen, die bestimmen, welche Daten gesammelt werden. Weitere Informationen finden Sie unter [Überwachen der Leistung des Berichtsservers](monitoring-report-server-performance.md).|  
|Setupprotokolldateien|Auch während der Installation werden Protokolldateien erstellt. Falls die Installation fehlschlägt oder mit Warn- oder anderen Meldungen erfolgreich beendet wird, können Sie zur Problembehandlung die Protokolldateien untersuchen. Weitere Informationen finden Sie unter [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).|  
|IIS-Protokolle|Von Microsoft-Internetinformationsdiensten (IIS) erstellte Protokolldateien. Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren der Protokollierung in IIS (Internetinformationsdienste)](https://support.microsoft.com/kb/313437).|  
|Video|Sehen Sie sich ein kurzes Video an, das die Verwendung von Microsoft Power Query zum Anzeigen von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Protokolldateien veranschaulicht.<br /><br /> ![Video über Power Query und SSRS-Protokolle](../media/generic-video-thumbnail.png "Video über Power Query und SSRS-Protokolle")|  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](reporting-services-report-server-native-mode.md)   
 [Fehler- und Ereignisreferenz &#40;Reporting Services&#41;](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
