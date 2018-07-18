---
title: Hinzufügen von Berichtsserver-Inhaltstypen zu einer Bibliothek (Reporting Services im integrierten SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ac9136c8-9ef4-484c-8e9d-05008a186db5
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: da7ee6e652442bdd2773a8c669b0d134f1fadc37
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177547"
---
# <a name="add-report-server-content-types-to-a-library-reporting-services-in-sharepoint-integrated-mode"></a>Hinzufügen von Berichtsserver-Inhaltstypen zu einer Bibliothek (Reporting Services im integrierten SharePoint-Modus)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthält vordefinierte SharePoint-Inhaltstypen, die zum Verwalten freigegebener Datenquellendateien (rsds), Berichtsmodelldateien (SMDL) und Berichts-Generator-Berichtsdefinitionsdateien (RDL) verwendet werden. Wenn einer Bibliothek ein Inhaltstyp ( **Berichts-Generator-Bericht**, **Berichtsmodell**und **Berichtsdatenquelle** ) hinzugefügt wird, wird der Befehl **Neu** aktiviert, sodass Sie neue Dokumente des betreffenden Typs erstellen können.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus  
  
 Wenn Sie einer Bibliothek Inhaltstypen hinzufügen möchten, müssen Sie Websiteadministrator sein oder über die Berechtigungsstufe "Vollzugriff" verfügen.  
  
 Die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Inhalt sowie die Verwaltung dieser Inhaltstyp werden automatisch in allen Dokumentbibliotheken für vorhandene Websitesammlungen, die aus den folgenden erstellt aktiviert **Business Intelligence Center** Websitevorlage.  
  
 Für Websites, die nach der Integration von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] erstellt wurden, sind die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Inhaltstypen nicht aktiviert.  
  
> [!TIP]  
>  Wenn man **nicht** zuvor konfigurierten Inhaltstypen für eine Bibliothek, aktivieren Sie zunächst die Verwaltung von Inhaltstypen, dann die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Inhaltstypen. Siehe die Verfahren zum Aktivieren der Inhaltstypverwaltung in einer einzelnen Dokumentbibliothek.  
  
 **Kurzvideo:** [(SSRS) Enabling Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w) ((SSRS) Aktivieren von Inhaltstypen in SharePoint2010.wmv).  
  
 **In diesem Thema:**  
  
-   [Aktivieren von Inhaltstypen in allen Dokumentbibliotheken eines vorhandenen Business Intelligence Centers](#bkmk_enable_all)  
  
-   [So aktivieren Sie die Inhaltstypverwaltung für eine einzelne Dokumentbibliothek (SharePoint 2013)](#bkmk_enable_content_management)  
  
-   [So fügen Sie Reporting Services-Inhaltstypen hinzu (SharePoint 2013)](#bkmk_add_single)  
  
-   [So aktivieren Sie die Inhaltstypverwaltung für eine einzelne Dokumentbibliothek (SharePoint 2010)](#bkmk_enable_content_management_2010)  
  
-   [So fügen Sie Berichtsserver-Inhaltstypen hinzu (SharePoint 2010)](#bkmk_add_single_2010)  
  
-   [So aktivieren Sie Inhaltstypen und die Inhaltsverwaltung für mehrere BI-Websites](#bkmk_enable_multiple_sites)  
  
##  <a name="bkmk_enable_all"></a> Aktivieren von Inhaltstypen in allen Dokumentbibliotheken eines vorhandenen Business Intelligence Centers  
  
1.  Um Inhaltstypen sowie die Inhaltsverwaltung in allen Dokumentbibliotheken einer vorhandenen **Business Intelligence Center** -Website zu aktivieren, können Sie die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Integrationsfunktion aktivieren/deaktivieren.  
  
2.  Wechseln Sie zu **Siteeinstellungen**.  
  
    -   Klicken Sie in SharePoint 2013 auf das **Einstellungssymbol**. ![SharePoint-Einstellungen](../analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings")  
  
    -   Klicken Sie in SharePoint 2010 auf **Websiteaktionen**und auf **Siteeinstellungen**.  
  
3.  Klicken Sie auf **Websitesammlungsfeatures**.  
  
4.  Suchen Sie die **Berichtsserver-Integrationsfunktion** , und klicken Sie auf **Deaktivieren**.  
  
     ![rs_berichtsserver_integration_aktiviert](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")  
  
5.  Aktualisieren Sie den Browser, und klicken Sie unter **Berichtsserver-Integrationsfunktion** auf **Aktivieren**.  
  
     ![rs_berichtsserver_integration_deaktiviert](media/rs-reportserver-integration-deactive.gif "rs_reportserver_integration_deactive")  
  
##  <a name="bkmk_enable_content_management"></a> So aktivieren Sie die Inhaltstypverwaltung für eine einzelne Dokumentbibliothek (SharePoint 2013)  
  
1.  Öffnen Sie die Bibliothek, für die Sie mehrere Inhaltstypen aktivieren möchten.  
  
2.  Klicken Sie im Menüband auf **Bibliothek** .  
  
     ![rs_SharePoint2013_BibliothekMenüband](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")  
  
3.  Klicken Sie im Menüband **Bibliothek** auf **Bibliothekeinstellungen**. Falls **Bibliothekseinstellungen** nicht angezeigt wird oder die Schaltfläche deaktiviert ist, sind Sie nicht berechtigt, Bibliothekseinstellungen sowie Inhaltstypen zu konfigurieren.  
  
     ![rs_SharePoint2013_BibliothekEinstellungen](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")  
  
4.  Klicken Sie im Abschnitt **Allgemeine Einstellungen** auf **Erweiterte Einstellungen**.  
  
     ![rs_SharePoint2013_BibliothekEinstellungen_ErweiterteEinstellungen](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")  
  
5.  Wählen Sie im Abschnitt **Inhaltstypen** die Option **Ja** aus, um die Verwaltung von Inhaltstypen zuzulassen.  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="bkmk_add_single"></a> So fügen Sie Reporting Services-Inhaltstypen hinzu (SharePoint 2013)  
  
1.  Öffnen Sie die Bibliothek, für die Sie Reporting Services-Inhaltstypen hinzufügen möchten.  
  
2.  Klicken Sie im Menüband auf **Bibliothek**.  
  
3.  Klicken Sie auf **Bibliothekeinstellungen**.  
  
4.  Klicken Sie unter **Inhaltstypen**auf **Aus vorhandenen Websiteinhaltstypen hinzufügen**.  
  
5.  Wählen Sie unter **Websiteinhaltstypen auswählen aus**die Option **SQL Server Reporting Services-Inhaltstypen**aus.  
  
6.  Klicken Sie in der Liste **Verfügbare Websiteinhaltstypen** auf **Berichts-Generator**, und klicken Sie dann auf **Hinzufügen** , um den ausgewählten Inhaltstyp in die Liste **Hinzuzufügende Inhaltstypen** zu verschieben.  
  
7.  Wiederholen Sie den vorherigen Schritt, um die Inhaltstypen **Berichtsmodell** und **Berichtsdatenquelle** hinzuzufügen.  
  
8.  Nachdem Sie alle gewünschten Inhaltstypen hinzugefügt haben, klicken Sie auf **OK**.  
  
9. > [!NOTE]  
    >  Wenn die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Inhaltstypgruppe **SQL Server Reporting Services-Inhaltstypen** ist nicht sichtbar ist, auf die **Inhaltstypen hinzufügen** Seite ist eine der folgenden Bedingungen "true":  
  
    -   Das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Add-In für SharePoint-Produkte wurde nicht installiert. Weitere Informationen finden Sie unter [installieren oder deinstallieren Sie das Reporting Services-Add-in für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Das Thema enthält Informationen zum Installieren des Add-Ins und es wird Schritt für Schritt erläutert, wie Sie eine Nur-Datei-Installation des Add-Ins ausführen können, um Probleme zu umgehen.  
  
    -   Das Add-In wird installiert, aber die **Funktion für die Berichtsserverintegration** für die Websitesammlung ist nicht aktiv. Prüfen Sie die Websitesammlungsfunktion unter **Siteeinstellungen**.  
  
    -   Alle der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Inhaltstypen haben bereits in der Bibliothek hinzugefügt wurde. Wenn alle Inhaltstypen einer Bibliothek angehören, wird die Gruppe von der Seite **Inhaltstypen hinzufügen** entfernt. Nachdem mindestens ein [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Inhaltstyp gelöscht wurde, wird die Gruppe **SQL Server Reporting Services-Inhaltstypen** auf der Seite **Inhaltstypen hinzufügen** angezeigt.  
  
##  <a name="bkmk_enable_content_management_2010"></a> So aktivieren Sie die Inhaltstypverwaltung für eine einzelne Dokumentbibliothek (SharePoint 2010)  
  
1.  Öffnen Sie die Bibliothek, für die Sie mehrere Inhaltstypen aktivieren möchten. Auf der Menüleiste der Bibliothek sollten die folgenden Menüs angezeigt werden: **Neu**, **Upload**, **Aktionen**und **Einstellungen**. Falls **Einstellungen**nicht angezeigt wird, sind Sie nicht berechtigt, Inhaltstypen hinzuzufügen.  
  
2.  Klicken Sie im Menüband **Bibliothekstools** auf **Bibliothek**.  
  
     ![rs_SharePoint2010_BibliothekMenüband](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")  
  
3.  Klicken Sie in der Menübandgruppe **Einstellungen** auf **Bibliothekseinstellungen**.  
  
4.  Klicken Sie unter **Allgemeine Einstellungen**auf **Erweiterte Einstellungen**.  
  
5.  Wählen Sie im Abschnitt **Inhaltstypen** die Option **Ja** aus, um die Verwaltung von Inhaltstypen zuzulassen.  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="bkmk_add_single_2010"></a> So fügen Sie Berichtsserver-Inhaltstypen hinzu (SharePoint 2010)  
  
1.  Öffnen Sie die Bibliothek, für die Sie Reporting Services-Inhaltstypen hinzufügen möchten.  
  
2.  Klicken Sie auf den Registerkarten des Menübands **Bibliothekstools** auf die Registerkarte **Bibliothek**.  
  
3.  Klicken Sie in der Menübandgruppe **Einstellungen** auf **Bibliothekseinstellungen**.  
  
4.  Klicken Sie unter **Inhaltstypen**auf **Aus vorhandenen Websiteinhaltstypen hinzufügen**.  
  
5.  Klicken Sie im Abschnitt **Inhaltstypen auswählen** in der Liste **Websiteinhaltstypen auswählen aus**auf den Pfeil, um **SQL Server Reporting Services-Inhaltstypen**auszuwählen.  
  
6.  Klicken Sie in der Liste **Verfügbare Websiteinhaltstypen** auf **Berichts-Generator**, und klicken Sie dann auf **Hinzufügen** , um den ausgewählten Inhaltstyp in die Liste **Hinzuzufügende Inhaltstypen** zu verschieben.  
  
7.  Wiederholen Sie den vorherigen Schritt, um die Inhaltstypen **Berichtsmodell** und **Berichtsdatenquelle** hinzuzufügen.  
  
8.  Nachdem Sie alle gewünschten Inhaltstypen hinzugefügt haben, klicken Sie auf **OK**.  
  
##  <a name="bkmk_enable_multiple_sites"></a> So aktivieren Sie Inhaltstypen und die Inhaltsverwaltung für mehrere BI-Websites  
  
1.  Bei Berichtsservern unter SQL Server Reporting Services 2008 und 2008 R2 können Inhaltstypen sowie die Inhaltsverwaltung für mehrere Business Intelligence Center-Websites aktiviert werden:  
  
2.  Klicken Sie in der SharePoint-Zentraladministration auf **Allgemeine Anwendungseinstellungen**. Klicken Sie im Abschnitt **SQL Server Reporting Services (2008 und 2008 R2)** auf **Reporting Services-Integration**.  
  
     ![rs_allgemeine_app_einstellungen](media/rs-general-app-settings.gif "rs_general_app_settings")  
  
3.  Klicken Sie auf **Funktion in allen vorhandenen Websitesammlungen aktivieren**.  
  
     ![rs_allgemeine_app_einstellungen_alte_integrationen](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [SharePoint-Website Referenz- und Listenberechtigungen für Berichtsserverelemente](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)   
 [Starten Sie Berichts-Generator &#40;Berichts-Generator&#41;](report-builder/start-report-builder.md)  
  
  
