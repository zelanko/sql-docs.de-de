---
title: Berichts-Manager-URL (SSRS-Modus) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 1469d877b992638119ad60bafadc1023a4ed5fc7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050034"
---
# <a name="report-manager-url-ssrs-native-mode"></a>Berichts-Manager-URL (einheitlicher SSRS-Modus)
  Auf der Seite der Berichts-Manager-URL können Sie die URL, mit der auf den Berichts-Manager zugegriffen wird, konfigurieren bzw. ändern. Standardmäßig übernimmt die URL des Berichts-Manager das Präfix, die IP-Adresse und den Port der URL des Report Server-Webdiensts. Dies ist darauf zurückzuführen, dass der Berichts-Manager Front-End-Zugriff auf den Webdienst bietet, der innerhalb desselben Berichtsserver-Diensts ausgeführt wird. Wenn Sie die Dienstanwendungen isolieren und den Berichts-Manager für den Zugriff auf einen Report Server-Webdienst auf einem anderen Computer verwenden, müssen Sie die Datei RSReportServer.config ändern, damit der Berichts-Manager auf eine andere Instanz verweist. Weitere Informationen zum Konfigurieren einer Berichts-Manager-Verbindung mit einem Remoteberichtsserver finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Wenn Sie den Berichtsserver so konfigurieren, dass er im integrierten SharePoint-Modus ausgeführt wird, erstellen Sie keine URL für den Berichts-Manager. Der Berichts-Manager wird auf einem Berichtsserver, der im integrierten SharePoint-Modus ausgeführt wird, nicht unterstützt. Wenn für den Berichts-Manager bereits eine URL vorhanden ist, ist diese nicht mehr verfügbar, sobald Sie den Berichtsserver für den integrierten SharePoint-Modus konfiguriert haben.  
  
 Um diese Seite zu öffnen, starten die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager, und klicken Sie auf **Report Manager URL** im Navigationsbereich. Weitere Informationen zum Starten des Konfigurations-Managers finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
> [!NOTE]  
>  Wenn der Berichts-Manager nicht aktiviert ist, können Sie auf dieser Seite keine Optionen festlegen. Weitere Informationen zum Aktivieren der Berichts-Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Tastatur  
 **Virtuelles Verzeichnis**  
 Gibt den Namen des virtuellen Verzeichnisses für den Berichts-Manager an. Auf einem Computer kann nur jeweils ein Name eines virtuellen Verzeichnisses für jede Instanz des Berichts-Managers vorhanden sein.  
  
 **URLs**  
 Zeigt die für die aktuelle Berichts-Manager-Instanz definierte URL an.  
  
 **Erweitert:**  
 Zeigt eine zusätzliche URL für die aktuelle Berichts-Manager-Instanz an.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [URLs in Konfigurationsdateien &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  