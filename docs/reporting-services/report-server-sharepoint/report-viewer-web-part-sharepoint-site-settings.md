---
title: Einstellungen der SharePoint-Website für den Berichts-Viewer-Webpart (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/31/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server-sharepoint
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: jt000
ms.author: jasontre
ms.openlocfilehash: 57e0e7ca8aa76570f70ae2279964d47f50da31aa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33024597"
---
# <a name="sharepoint-site-settings-for-the-report-viewer-web-part---reporting-services"></a>Einstellungen der SharePoint-Website für den Berichts-Viewer-Webpart – Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Der Berichts-Viewer-Webpart weist einige Einstellungen auf, die konfiguriert werden können. Diese Einstellungen können auf der SharePoint-Websiteeinstellungenseite durch einen Websiteadministrator aktiviert und deaktiviert werden. Beachten Sie, dass jede Website eigene Einstellungen aufweist. Darüber hinaus werden diese Einstellungen nach der Neuinstallation des Berichts-Viewer-Webparts nicht zurückgesetzt.

## <a name="accessing-the-site-settings-page"></a>Zugreifen auf die Websiteeinstellungenseite

So können Sie auf die Websiteeinstellungen zugreifen:

1. Wählen Sie auf Ihrer SharePoint-Website das **Zahnradsymbol** in der oberen linken Ecke und anschließend **Websiteeinstellungen** aus.

    ![Websiteeinstellungen über das Zahnradsymbol.](media/sharepoint-site-settings.png)

2. Klicken auf **Einstellungen für Berichts-Viewer-Webpart** in der Websiteeinstellungengruppe **Reporting Services**.

    > [!NOTE]
    > Die Websiteeinstellungen können Sie auch durch direktes Navigieren zu `<site>/_layouts/15/ReportViewerWebPart/ReportViewerWebPartSettings.aspx` erreichen.

## <a name="report-viewer-web-part-settings"></a>Berichts-Viewer-Webparteinstellungen

|Einstellung|Kommentare|  
|-------------|--------------|  
|Nutzungsdaten sammeln|Ermöglicht das Senden von Fehler- und Nutzungsinformationen an Microsoft, um eine Verbesserung der Produkte zu ermöglichen. Die Microsoft-Richtlinie für die Fehlerbericht-Datensammlung finden Sie in den [Microsoft SQL Server-Datenschutzbestimmungen](https://go.microsoft.com/fwlink/?linkid=860782&clcid=0x409).|  
|Barrierefreiheit-Metadaten für Berichte aktivieren|Legt die [`AccessibleTablix`-Geräteinfo](../html-device-information-settings.md) für gerenderte Berichte fest.| 
