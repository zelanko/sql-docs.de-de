---
title: Ereignisprotokollierung durch den Integration Services-Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], events
- events [Integration Services], service
- Integration Services service, events
ms.assetid: d4122dcf-f16f-47a0-93a2-ffa3d0d4f9cf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dedffe0f30c62399e4d694f7ee1bf5247222e87d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62889272"
---
# <a name="events-logged-by-the-integration-services-service"></a>Ereignisprotokollierung durch den Integration Services-Dienst
  Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst protokolliert verschiedene Meldungen in das Windows-Anwendungsereignisprotokoll. Der Dienst Paket protokolliert diese Meldungen, wenn er startet, wenn er anhält und wenn bestimmte Probleme auftreten.  
  
 Dieses Thema enthält Informationen über die allgemeinen Ereignismeldungen, die von einem Dienst im Anwendungsereignisprotokoll protokolliert werden. Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst protokolliert alle in diesem Thema beschriebenen Meldungen mit der Ereignisquelle SQLISService.  
  
 Allgemeine Informationen zum [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Dienst finden Sie unter [Integration Services-Dienst &#40;SSIS-Dienst&#41;](integration-services-service-ssis-service.md).  
  
## <a name="messages-about-the-status-of-the-service"></a>Meldungen zum Dienststatus  
 Wenn Sie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] zur Installation auswählen, wird der Dienst [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installiert und gestartet, und der Starttyp wird auf Automatisch gesetzt.  
  
|Ereignis-ID|Symbolischer Name|Text|Notizen|  
|--------------|-------------------|----------|-----------|  
|256|DTS_MSG_SERVER_STARTING|Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Dienst wird gestartet.|Der Dienst wird gerade gestartet.|  
|257|DTS_MSG_SERVER_STARTED|Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Dienst wurde gestartet.|Der Dienst wurde gestartet.|  
|260|DTS_MSG_SERVER_START_FAILED|Fehler beim Starten des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Diensts.%nFehler: %1|Der Dienst konnte nicht gestartet werden. Dass der Dienst nicht starten konnte, könnte die Folge einer beschädigten Installation oder eines unpassenden Dienstkontos sein.|  
|258|DTS_MSG_SERVER_STOPPING|Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Dienst wird beendet.%n%n Alle ausgeführten Pakete werden beim beenden angehalten. %1|Der Dienst wird angehalten, und wenn der Dienst so konfiguriert ist, hält er alle ausgeführten Pakete an. In der Konfigurationsdatei können Sie den Wert True oder False festlegen. Dieser Wert bestimmt, ob der Dienst die Ausführung von Paketen beendet, wenn der Dienst selbst beendet wird. Die Meldung für dieses Ereignis enthält den Wert dieser Einstellung.|  
|259|DTS_MSG_SERVER_STOPPED|Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Dienst wurde beendet.%nServerversion %1|Der Dienst wurde beendet.|  
  
## <a name="messages-about-the-configuration-file"></a>Meldungen über die Konfigurationsdatei  
 Einstellungen für den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst werden in einer XML-Datei gespeichert, die Sie ändern können. Weitere Informationen finden Sie unter [Konfigurieren des Integration Services-Diensts &#40;SSIS-Dienst&#41;](../configuring-the-integration-services-service-ssis-service.md).  
  
|Ereignis-ID|Symbolischer Name|Text|Notizen|  
|--------------|-------------------|----------|-----------|  
|274|DTS_MSG_SERVER_MISSING_CONFIG_REG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Dienst: %nRegistrierungseinstellung mit Angabe der Konfigurationsdatei ist nicht vorhanden. %nEs wird versucht, die Standardkonfigurationsdatei zu laden.|Der Registrierungseintrag, der den Pfad der Konfigurationsdatei enthält, ist nicht vorhanden oder leer.|  
|272|DTS_MSG_SERVER_MISSING_CONFIG|Die Konfigurationsdatei für den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Dienst ist nicht vorhanden.%nWird mit Standardeinstellungen geladen.|Die Konfigurationsdatei ist am angegebenen Speicherort nicht vorhanden.|  
|273|DTS_MSG_SERVER_BAD_CONFIG|Falsche Konfigurationsdatei für den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Dienst.%nFehler beim Lesen der Konfigurationsdatei: %1%n%nServer wird mit Standardeinstellungen geladen.|Die Konfigurationsdatei konnte nicht gelesen werden oder ist nicht gültig. Dieser Fehler könnte die Folge eines XML-Syntaxfehlers in der Datei sein.|  
  
## <a name="other-messages"></a>Andere Meldungen  
  
|Ereignis-ID|Symbolischer Name|Text|Notizen|  
|--------------|-------------------|----------|-----------|  
|336|DTS_MSG_SERVER_STOPPING_PACKAGE|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Dienst; Ausgeführtes Paket wird beendet.%nPaketinstanz-ID: %1%nPaket-ID: %2%nPaketname: %3%nPaketbeschreibung: %4%nPaket|Der Dienst versucht, ein ausgeführtes Paket zu beenden. Sie können ausgeführte Pakete in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]überwachen und anhalten. Weitere Informationen zum Verwalten von Paketen in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] finden Sie unter [Paketverwaltung &#40;SSIS-Dienst&#41;](package-management-ssis-service.md).|  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Anzeigen von Protokolleinträgen finden Sie unter [Anzeigen der Protokolleinträge im Fenster „Protokollereignisse“](../view-log-entries-in-the-log-events-window.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durch ein Integration Services-Paket protokollierte Ereignisse](../performance/events-logged-by-an-integration-services-package.md)  
  
  
