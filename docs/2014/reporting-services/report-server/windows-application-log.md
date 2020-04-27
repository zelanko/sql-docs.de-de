---
title: Windows-Anwendungsprotokoll | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Windows application logs [Reporting Services]
- logs [Reporting Services], Windows application logs
- application logs [Reporting Services]
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 747a811d1d355bd182b18f4c29f2d1bf9354fa55
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66103024"
---
# <a name="windows-application-log"></a>Windows-Anwendungsprotokoll
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] schreibt Ereignismeldungen in das Windows-Anwendungsprotokoll. Sie können die in das Anwendungsprotokoll geschriebenen Meldungsinformationen verwenden, um sich über Ereignisse zu informieren, die von den auf dem lokalen System ausgeführten Berichtsserveranwendungen generiert werden.  
  
## <a name="viewing-report-server-events"></a>Anzeigen von Berichtsserverereignissen  
 Mit der Ereignisanzeige können Sie die Protokolldatei anzeigen und die darin enthaltenen Meldungen filtern. Weitere Informationen zu Ereignisnachrichten finden Sie unter [Fehler- und Ereignisreferenz &#40;Reporting Services&#41;](../troubleshooting/errors-and-events-reference-reporting-services.md). Weitere Informationen zum Windows-Anwendungsprotokoll oder zur Ereignisanzeige finden Sie in der Produktdokumentation zu Windows.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt drei Ereignisquellen bereit:  
  
-   Berichtsserver (Berichtsserver-Dienst von Windows)  
  
-   Berichts-Manager  
  
-   Prozessor für Zeitplanung und Übermittlung  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist es nicht möglich, die Anwendungsereignisprotokollierung für einen Berichtsserver zu deaktivieren oder zu steuern, welche Ereignisse protokolliert werden. Das Schema zur Beschreibung der Ereignisprotokollierung für den Berichtsserver kann nicht bearbeitet werden. Deshalb kann das Schema nicht um die Unterstützung benutzerdefinierter Ereignisse erweitert werden.  
  
 In der folgenden Tabelle werden die Ereignistypen beschrieben, die der Berichtsserver in das Anwendungsereignisprotokoll schreibt.  
  
|Ereignistyp|BESCHREIBUNG|  
|----------------|-----------------|  
|Information|Ein Ereignis, das einen erfolgreichen Vorgang beschreibt (z. B. das Starten des Berichtsserverdienstes).|  
|Warnung|Ein Ereignis, das auf ein potenzielles Problem hinweist (z. B. unzureichenden Speicherplatz).|  
|Fehler|Ein Ereignis, das ein erhebliches Problem beschreibt (z. B., dass der Dienst nicht gestartet wurde).|  
|Erfolgsüberwachung|Ein Sicherheitsereignis, das eine erfolgreiche Anmeldung beschreibt.|  
|Fehlerüberwachung|Ein Ereignis, das beim Fehlschlagen eines Anmeldeversuchs protokolliert wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Protokolldateien und Quellen](../report-server/reporting-services-log-files-and-sources.md)   
 [Fehler- und Ereignisreferenz &#40;Reporting Services&#41;](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
