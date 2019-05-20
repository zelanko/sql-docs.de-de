---
title: Einstellungen der SharePoint-Website für den Berichts-Viewer-Webpart (SSRS) | Microsoft-Dokumentation
ms.date: 11/15/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: jt000
ms.author: jasontre
ms.openlocfilehash: 738908549caa157557a16b1ae05575231a15c734
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65580589"
---
# <a name="sharepoint-site-settings-for-the-report-viewer-web-part---reporting-services"></a>Einstellungen der SharePoint-Website für den Berichts-Viewer-Webpart – Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2016-2019](../../includes/ssrs-appliesto-sharepoint-2016-2019.md)] [!INCLUDE[ssrs-appliesto-not-sharepoint-online](../../includes/ssrs-appliesto-not-sharepoint-online.md)]

Der Berichts-Viewer-Webpart weist einige Einstellungen auf, die konfiguriert werden können. Diese Einstellungen können auf der SharePoint-Websiteeinstellungenseite durch einen Websiteadministrator aktiviert und deaktiviert werden. Jede Website weist eigene Einstellungen auf. Darüber hinaus werden diese Einstellungen nach der Neuinstallation des Berichts-Viewer-Webparts nicht zurückgesetzt.

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
|Nutzungsdaten sammeln|Ermöglicht das Senden von Fehler- und Nutzungsinformationen an Microsoft, um eine Verbesserung der Produkte zu ermöglichen. Die Microsoft-Richtlinie für die Fehlerbericht-Datensammlung finden Sie in den [Microsoft SQL Server-Datenschutzbestimmungen](https://go.microsoft.com/fwlink/?LinkID=868444).|  
|Barrierefreiheit-Metadaten für Berichte aktivieren|Legt die [`AccessibleTablix`-Geräteinfo](../html-device-information-settings.md) für gerenderte Berichte fest.| 
