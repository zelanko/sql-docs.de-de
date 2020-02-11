---
title: Berichte im lokalen Modus im Vergleich zu Berichten im verbundenen Modus im Berichts-Viewer (Reporting Services im SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a230a9bb-6046-401f-b5e5-53ff6edf2264
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86cff99688dda7a953a7da1d4104865beed5a98b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75253171"
---
# <a name="local-mode-vs-connected-mode-reports-in-the-report-viewer-reporting-services-in-sharepoint-mode"></a>Berichte im lokalen Modus im Vergleich mit Berichten im verbundenen Modus im Berichts-Viewer (Reporting Services im SharePoint-Modus)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Berichte können so konfiguriert werden, dass Sie entweder im *lokalen Modus* oder im *verbundenen Modus*ausgeführt werden [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , der einen Berichts Server nutzt. Sie können stattdessen mithilfe des Berichts-Viewers Berichte aus SharePoint direkt rendern, sofern die Datenerweiterung die Berichterstellung im lokalen Modus unterstützt. Dieser Ansatz wird als *lokaler Modus*bezeichnet. In früheren Versionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]musste die SharePoint-Farm mit einem im SharePoint-Modus konfigurierten [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver verbunden sein, damit Berichte vom Steuerelement des Berichts-Viewers gerendert werden konnten. Dieser Ansatz wird als *Remotemodus* oder *verbundener Modus*bezeichnet.  
  
 Im *lokalen Modus* gibt es keinen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver. Sie müssen das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte installieren, während jedoch kein [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver erforderlich ist. Im lokalen Modus können Benutzer Berichte anzeigen, haben aber keinen Zugriff auf serverseitige Funktionen wie Abonnements und Datenwarnungen.  
  
||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint-Modus|  
  
 **In diesem Thema:**  
  
-   [Lokaler Modus im Vergleich zum verbundenen Modus und unterstützte Erweiterungen](#bkmk_local_vs_connected)  
  
-   [Konfigurieren des lokalen Modus und Zugreifen auf Dienste mit SharePoint 2013](#bkmk_local_mode_sharepoint2013)  
  
-   [Konfigurieren der Berichterstellung im lokalen Modus mit SharePoint 2010](#bkmk_local_mode_sharepoint2010)  
  
##  <a name="bkmk_local_vs_connected"></a>Lokaler Modus im Vergleich zum verbundenen Modus und unterstützte Erweiterungen  
 **Lokaler Modus:** Wenn Sie über eine Daten Erweiterung verfügen, die den lokalen Modus unterstützt, rendert der Berichts-Viewer direktberichte aus SharePoint. Im *lokalen Modus* gibt es keinen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver. Sie müssen das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte installieren, während jedoch kein [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver erforderlich ist. Im lokalen Modus können Benutzer Berichte anzeigen, haben aber **keinen** Zugriff auf serverseitige Funktionen wie Abonnements und Datenwarnungen.  
  
 Für den **verbundenen Modus**, auch *Remote Modus* genannt [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , ist ein Berichts Server im SharePoint-Modus erforderlich, der mit der SharePoint-Farm verbunden ist, damit Berichte von dem Berichts-Viewer-Steuerelement geren  
  
 Die folgende Liste enthält die Datenverarbeitungserweiterungen, die lokale Modusberichterstellung unterstützen:  
  
-   
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Access 2010-Berichtserweiterung. Weitere Informationen zu Access Services finden Sie unter [Verwenden von Access Services mit SQL Reporting Services: Installieren des SQL Server 2008 R2 Reporting Services-Add-Ins (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686).  
  
-   Die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -SharePoint-Listendatenerweiterung. Weitere Informationen zur SharePoint-Listendatenerweiterung finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
 Benutzerdefinierte Datenverarbeitungserweiterungen können auch für den lokalen Modus entwickelt werden. Weitere Informationen finden Sie unter [Implementing a Data Processing Extension](extensions/data-processing/implementing-a-data-processing-extension.md).  
  
 Der lokale Modus unterstützt das Rendern von Berichten mit einer eingebetteten oder freigegebenen Datenquelle von einer RSDS-Datei. Sie können den Bericht oder dessen zugeordnete Datenquelle jedoch nicht verwalten. In diesem Fall wird ein Fehler mit dem Hinweis ausgegeben, dass der Vorgang im lokalen Modus nicht unterstützt wird. Das Verwalten von Datenquellen auf der SharePoint-Website wird nur im verbundenen Modus unterstützt.  
  
> [!NOTE]  
>  Wie in früheren Versionen ist es nicht möglich, Benutzernamen und Kennwörter in die RSDS-Datei einzubetten.  
  
##  <a name="bkmk_local_mode_sharepoint2013"></a>Konfigurieren des lokalen Modus und Zugreifen auf Dienste mit SharePoint 2013  
 Sie können die SharePoint 2013-Farm so konfigurieren, dass vorhandene Access 2010-Webdatenbanken und der lokale [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Modus unterstützt werden. Weitere Informationen finden Sie unter [Einrichten und Konfigurieren von Access Services 2010 für Webdatenbanken in SharePoint Server 2013](https://technet.microsoft.com/library/ee748653\(office.15\).aspx).  
  
 Es ist nicht möglich, neue Access-Webdatenbanken für SharePoint 2013 zu erstellen. Access 2013 verwendet den neuen Datenbanktyp *Access Web App* , den Sie in Access erstellen und dann als SharePoint-App in einem Webbrowser verwenden und mit anderen gemeinsam nutzen.  
  
 Weitere Informationen finden Sie unter folgenden Themen.  
  
-   [Neues in Access 2013](https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) (https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx).  
  
-   [Grundlegende Aufgaben für eine Access](https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) -https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500)app (.  
  
##  <a name="bkmk_local_mode_sharepoint2010"></a>Konfigurieren der Berichterstellung im lokalen Modus mit SharePoint 2010  
 Der lokale Modus erfordert den ASP.NET-Sitzungsstatus. Durch die Installation von Access-Diensten wird der ASP.NET-Sitzungstatus aktiviert. Sie können die Aktivierung auch mit PowerShell durchführen.  
  
1.  Öffnen Sie die SharePoint 2010-Verwaltungsshell.  
  
2.  Geben Sie den folgenden Befehl ein:   
  
    ```  
    - Enable-SPSessionStateService  
    ```  
  
3.  Geben bei Aufforderung den Namen der Datenbank ein.  
  
4.  Führen Sie eine IIS-Rücksetzung aus.  
  
 Weitere Informationen finden Sie unter [Verwenden von Access Services mit SQL Reporting Services: Installieren des SQL Server 2008 R2 Reporting Services-Add-Ins (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686) und [Enable-SPSessionStateService](https://technet.microsoft.com/library/ff607857\(v=office.15\).aspx).  
  
## <a name="connected-mode"></a>Modus „Verbunden“  
 Die neuesten Informationen zur Verwendung der ADS-Erweiterung mit verbundenem Modus in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] finden Sie unter [Access Services-Bericht in SharePoint-Website zeigt einen Fehler in der ADS-Datenerweiterung](https://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellen, die von Reporting Services &#40;SSRS unterstützt werden&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
