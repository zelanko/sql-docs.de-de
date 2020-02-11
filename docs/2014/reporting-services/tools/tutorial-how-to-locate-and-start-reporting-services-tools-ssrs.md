---
title: 'Tutorial: So suchen und starten Sie Reporting Services-Tools (SSRS) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder 1.0, locating and starting tool
- Reporting Services, tutorials
- Reporting Services, tools
- Reporting Services Configuration tool
- Business Intelligence Development Studio, locating and starting tool
- Model Designer [Reporting Services], locating and starting tool
- Report Designer [Reporting Services], tutorials
- tools [Reporting Services]
- tutorials [Reporting Services]
- Report Manager [Reporting Services]
ms.assetid: 51ad69d8-fe92-4662-a7cd-d235692f0c03
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4edd0b6e3928a2bc3a280403a87eda5bb797e620
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099482"
---
# <a name="tutorial-how-to-locate-and-start-reporting-services-tools-ssrs"></a>Lernprogramm: So suchen und starten Sie Reporting Services-Tools (SSRS)
  In diesem Lernprogramm werden die Tools vorgestellt, mit denen Berichtsserver konfiguriert, Berichtsserverinhalte und -vorgänge verwaltet und Berichte erstellt und veröffentlicht werden. Der Zweck dieses Lernprogramms besteht darin, dass neue Benutzer verstehen, wie sie die einzelnen Tools finden und öffnen können. Wenn Sie die Tools bereits kennen, können Sie zu anderen Lernprogrammen wechseln, in denen Sie wichtige Funktionen für die Verwendung von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]kennen lernen. Weitere Informationen zu anderen Tutorials finden Sie unter [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).  
  
 Inhalte dieses Themas:  
  
-   [Reporting Services-Konfigurations-Manager (einheitlicher Modus)](#bkmk_configuration_manager)  
  
-   [Berichts-Manager (einheitlicher Modus)](#bkmk_report_manager)  
  
-   [Management Studio](#bkmk_managements_studio)  
  
-   [SQL Server Data Tools mit Berichts-Designer und dem Berichts-Assistenten](#bkmk_ssdt)  
  
-   [Report Builder (Berichts-Generator)](#bkmk_report_builder)  
  
##  <a name="bkmk_configuration_manager"></a>Konfigurations-Manager für Reporting Services (einheitlicher Modus)  
 Verwenden Sie den Konfigurations-Manager im einheitlichen Modus, um folgende Aufgaben auszuführen:  
  
-   Angeben des Dienstkontos.  
  
-   Erstellen oder Aktualisieren der Berichtsserver-Datenbank.  
  
-   Ändern der Verbindungseigenschaften.  
  
-   Angeben von URLs.  
  
-   Verwalten von Verschlüsselungsschlüsseln.  
  
-   Konfigurieren der unbeaufsichtigten Berichtsverarbeitung und E-Mail-Übermittlung von Berichten.  
  
 **Installation:** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Configuration Manager wird installiert, wenn Sie [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] den einheitlichen Modus installieren. Weitere Informationen finden Sie unter [Installieren Reporting Services Berichts Servers](../install-windows/install-reporting-services-native-mode-report-server.md) im einheitlichen Modus.  
  
#### <a name="to-start-the-reporting-services-configuration-manager"></a>So starten Sie den Reporting Services-Konfigurations-Manager  
  
1.  Geben `reporting` Sie auf dem Windows-Startbildschirm ein, und klicken Sie in den Suchergebnissen der **apps** auf **Konfigurations-Manager für Reporting Services**.  
  
     ![Reporting Services-Konfigurations-Manager beim Start](../media/bi-ssrs-configmanager-win8-startscreen.gif "Reporting Services-Konfigurations-Manager beim Start")  
  
     **Noch**  
  
     Klicken Sie auf **Starten**, auf **Programme**, auf [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], auf **Konfigurationstools**und dann auf **Konfigurations-Manager für Reporting Services**.  
  
     Das Dialogfeld **Auswahl der Berichtsserver-Installationsinstanz** wird angezeigt, mit dem Sie die Berichtsserverinstanz auswählen können, die Sie konfigurieren möchten.  
  
2.  Geben Sie in **Servername**den Namen des Computers an, auf dem die Berichtsserverinstanz installiert ist. Standardmäßig ist der Name des lokalen Computers angegeben, Sie können jedoch auch den Namen einer Remoteinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eingeben.  
  
     Falls Sie einen Remotecomputer angeben, klicken Sie auf **Suchen** , um eine Verbindung herzustellen. Der Berichtsserver muss zuvor für die Remoteverwaltung konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers für die Remoteverwaltung](../report-server/configure-a-report-server-for-remote-administration.md).  
  
3.  Wählen Sie unter **Wählen Sie unterstance Name**die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Instanz aus, die Sie konfigurieren möchten. In der Liste werden ausschließlich [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]- und [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Berichtsserverinstanzen angezeigt. Frühere Versionen von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]können nicht konfiguriert werden.  
  
4.  Klicken Sie auf **Verbinden**.  
  
5.  Wenn Sie sicherstellen möchten, dass das Tool gestartet wurde, vergleichen Sie Ihre Ergebnisse mit dem folgenden Bild:  
  
     ![Reporting Services-Konfigurationstool](../media/rs-ui-reportserverconfigkatmai.gif "Reporting Services-Konfigurationstool")  
  
 **Nächste Schritte:** [Konfigurieren und Verwalten eines Berichts Servers &#40;SSRS im einheitlichen Modus&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) und [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
##  <a name="bkmk_report_manager"></a>Berichts-Manager (einheitlicher Modus)  
 Verwenden Sie [Berichts-Manager &#40;SSRS im einheitlichen Modus&#41;](../report-manager-ssrs-native-mode.md) , um Berechtigungen festzulegen, Abonnements und Zeitpläne zu verwalten und mit Berichten zu arbeiten. Sie können den Berichts-Manager auch zum Anzeigen von Berichten verwenden.  
  
 **Installation:** Berichts-Manager wird bei der Installation [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] des einheitlichen Modus installiert: [Installieren Reporting Services Berichts Servers](../install-windows/install-reporting-services-native-mode-report-server.md) im einheitlichen Modus  
  
 Damit Sie den Berichts-Manager öffnen können, müssen Sie über ausreichende Berechtigungen verfügen (anfangs besitzen nur Mitglieder der lokalen Gruppe Administratoren Berechtigungen, mit denen der Zugriff auf Berichts-Manager-Funktionen möglich ist). Der Berichts-Manager enthält verschiedene Seiten und Optionen, die sich je nach den Rollenzuweisungen des aktuellen Benutzers unterscheiden. Für Benutzer ohne Berechtigungen wird eine leere Seite angezeigt. Für Benutzer mit Berechtigungen zum Anzeigen von Berichten werden Links angezeigt, auf die sie klicken können, um die Berichte zu öffnen. Weitere Informationen zu Berechtigungen finden Sie unter [Rollen und Berechtigungen (Reporting Services)](../security/roles-and-permissions-reporting-services.md).  
  
#### <a name="to-start-report-manager"></a>So starten Sie den Berichts-Manager  
  
1.  Öffnen Sie Ihren Browser. Informationen zu unterstützten Browsern und Browserversionen finden Sie [unter Planning for Reporting Services und Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).  
  
2.  Geben Sie die URL des Berichts-Managers in die Adressleiste des Webbrowsers ein. Standardmäßig lautet die URL **http://\<Servername>/Reports**. Zur Bestätigung des Servernamens und der URL können Sie das Reporting Services-Konfigurationstool verwenden. Weitere Informationen zu URLs in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] finden Sie unter [Konfigurieren von Berichtsserver-URLs (SSRS-Konfigurations-Manager)](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md).  
  
3.  Der Berichts-Manager wird im Browserfenster geöffnet. Die Startseite entspricht dem Basisordner. In Abhängigkeit von den Berechtigungen werden möglicherweise zusätzliche Ordner, Links zu Berichten sowie Ressourcendateien auf der Startseite angezeigt. Möglicherweise werden auf der Symbolleiste auch zusätzliche Schaltflächen und Befehle angezeigt.  
  
4.  Wenn Sie Berichts-Manager auf dem lokalen Berichts Server ausführen, finden Sie weitere Informationen unter [Konfigurieren eines Berichts Servers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
 **Nächste Schritte:** [Konfigurieren Sie Berichts-Manager &#40;einheitlichen Modus&#41;](../report-server/configure-web-portal.md).  
  
##  <a name="bkmk_managements_studio"></a>Management Studio  
 Mit [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] können Berichtsserveradministratoren einen Berichtsserver neben weiteren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Komponentenservern verwalten. Weitere Informationen finden Sie unter [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md).  
  
#### <a name="to-start-sql-server-management-studio"></a>So starten Sie SQL Server Management Studio  
  
1.  Geben `sql server` Sie auf dem Windows-Start Bildschirm ein, und klicken Sie in den Suchergebnissen der **apps** auf **SQL Server Management Studio**.  
  
     ![Management Studio vom Windows-Startbildschirm](../media/bi-ssms-win8-startscreen.gif "Management Studio vom Windows-Startbildschirm")  
  
     **Noch**  
  
     Klicken Sie auf **Start**, auf **Alle Programme**, auf [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]und klicken Sie dann auf **SQL Server Management Studio**. Das Dialogfeld **Mit Server verbinden** wird angezeigt.  
  
2.  Wenn das Dialogfeld **Verbindung mit Server herstellen** nicht angezeigt wird, klicken Sie im **Objekt-Explorer**auf **Verbinden** , und wählen Sie dann **Reporting Services**aus.  
  
3.  Wählen Sie in der Liste **Servertyp** die Option **Reporting Services**aus. Wenn [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] nicht in der Liste aufgeführt wird, ist es nicht installiert.  
  
4.  Wählen Sie in der Liste **Servername** eine Berichtsserverinstanz aus. In der Liste werden lokale Instanzen angezeigt. Sie können auch den Namen einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Remoteinstanz eingeben.  
  
5.  Klicken Sie auf **Verbinden**. Sie können den Stammknoten erweitern, um Servereigenschaften festzulegen, Rollendefinitionen zu ändern oder Berichtsserverfunktionen zu deaktivieren.  
  
##  <a name="bkmk_ssdt"></a>SQL Server Data Tools mit Berichts-Designer und dem Berichts-Assistenten  
 Der Berichts-Designer ist in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] – Business Intelligence für Visual Studio 2012 verfügbar. Die Entwurfsoberfläche im Tool umfasst Fenster im Registerformat, Assistenten und Menüs, mit denen der Zugriff auf Berichts- und Modellerstellungsfunktionen möglich ist. Das Berichts-Designer-Tool steht zur Verfügung, wenn Sie eine Vorlage für ein Berichtsserverprojekt oder für einen Berichtsserverprojekt-Assistenten auswählen. Weitere Informationen finden Sie unter [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).  
  
#### <a name="to-start-report-designer"></a>So starten Sie Berichts-Designer  
  
1.  Geben Sie im Windows-Startbildschirm **data** ein, und klicken Sie in den Suchergebnissen in **Apps** auf **SQL Server Data Tools für Visual Studio 2012**.  
  
     **Noch**  
  
     Zeigen Sie im Menü **Start**auf **Alle Programme**und anschließend auf [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], und klicken Sie auf **SQL Server Data Tools (SSDT)**.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Klicken Sie in der Liste **Projekttypen** auf **Business Intelligence-Projekte**.  
  
4.  Klicken Sie in der Liste **Vorlagen** auf **Berichtsserverprojekt**. Mit der folgenden Grafik wird veranschaulicht, wie die Projektvorlagen im Dialogfeld angezeigt werden:  
  
     ![Neues Projekt (Vorlagendialogfeld)](../media/rs-ui-newrsproject.gif "Neues Projekt (Vorlagendialogfeld)")  
  
5.  Geben Sie einen Namen und einen Speicherort für das Projekt ein, oder klicken Sie auf **Durchsuchen** , und wählen Sie einen Speicherort aus.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)][!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] wird mit der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Startseite geöffnet. Der Projektmappen-Explorer umfasst Kategorien zum Erstellen von Berichten und Datenquellen. Mit diesen Kategorien können Sie neue Berichte und Datenquellen erstellen. Wenn Sie eine Berichtsdefinition erstellen, werden Fenster im Registerformat angezeigt. Die Fenster im Registerformat lauten Daten, Layout und Vorschau.  
  
 Informationen zum Erstellen Ihrer ersten Berichte finden Sie unter [Erstellen eines einfachen Tabellenberichts (SSRS-Tutorial)](../create-a-basic-table-report-ssrs-tutorial.md). Weitere Informationen zu Abfrage-Designern, die Sie in Berichts-Designer verwenden können, finden Sie unter [Abfrage Entwurfs Tools in Berichts-Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md).  
  
##  <a name="bkmk_report_builder"></a>Berichts-Generator  
 Verwenden Sie [Berichts-Generator &#40;SSRS-&#41;](report-builder-authoring-environment-ssrs.md) , um Berichte [!INCLUDE[msCoName](../../includes/msconame-md.md)] in einer Office-ähnlichen Erstellungs Umgebung zu erstellen. Sie haben die Möglichkeit, alle vorhandenen Berichte anzupassen und zu aktualisieren. Dabei spielt es keine Rolle, ob sie im Berichts-Designer oder in früheren Versionen des Berichts-Generators erstellt wurden. Informationen über den Speicherort der Datei ReportBuilder3.msi zur Installation des Berichts-Generators auf dem lokalen Computer erhalten Sie von Ihrem Administrator.  
  
 **Installation:** Die Click-Once-Version des Berichts-Generators wird entweder [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] im einheitlichen Modus oder im SharePoint-Modus installiert. Die eigenständige Version des Berichts-Generators muss separat heruntergeladen werden.  Weitere Informationen finden Sie [unter Installieren der eigenständigen Version von Berichts-Generator &#40;Berichts-Generator&#41;](../install-windows/install-report-builder.md)  
  
#### <a name="to-start-report-builder-clickonce-from-report-manager-native-mode"></a>So starten Sie die ClickOnce-Version des Berichts-Generators aus dem Berichts-Manager (einheitlicher Modus)  
  
1.  Geben Sie im Webbrowser die Berichts-Manager-URL für den Berichtsserver ein. Standardmäßig lautet die URL http://\<*Servername*>/Berichte. Der Berichts-Manager wird geöffnet.  
  
2.  Klicken Sie auf **Berichts-Generator**.  
  
     Der Berichts-Generator wird geöffnet, und Sie können einen Bericht erstellen oder auf dem Berichtsserver öffnen.  
  
#### <a name="to-start-report-builder-clickonce-using-a-url"></a>So starten Sie den Berichts-Generator ClickOnce über eine URL  
  
1.  Geben Sie die folgende URL in die Adressleiste des Webbrowsers ein:  
  
     **http://\<Servername>/ReportServer/ReportBuilder/ReportBuilder_3_0_0_0. Application**  
  
2.  Drücken Sie die EINGABETASTE.  
  
     Der Berichts-Generator wird geöffnet, und Sie können einen Bericht erstellen oder auf dem Berichtsserver öffnen.  
  
#### <a name="to-start-report-builder-clickonce-in-reporting-services-sharepoint-mode"></a>So starten Sie die ClickOnce-Version des Berichts-Generators im SharePoint-Modus von Reporting Services  
  
1.  Navigieren Sie zu der Website mit der Bibliothek, in der Sie einen neuen Bericht erstellen möchten.  
  
2.  Öffnen Sie die Bibliothek.  
  
3.  Klicken Sie im Menü **Neu** auf **Berichts-Generator-Bericht**.  
  
     Der Berichts-Generator wird geöffnet, und Sie können einen Bericht erstellen oder auf dem Berichtsserver öffnen.  
  
#### <a name="to-start-report-builder-stand-alone"></a>So starten Sie die eigenständige Version des Berichts-Generators  
  
1.  Geben Sie im Windows-Startbildschirm **report builder** ein, und klicken Sie auf **Berichts-Generator 3.0**.  
  
     **Noch**  
  
     Klicken Sie im Menü "Start" auf **Alle Programme**und anschließend auf **Microsoft SQL Server 2014 Berichts-Generator**.  
  
2.  Klicken Sie auf **Berichts-Generator**.  
  
     Der Berichts-Generator wird geöffnet, und Sie können einen Bericht erstellen oder öffnen.  
  
3.  Klicken Sie auf **Hilfe zum Berichts-Generator** , um die Dokumentation für den Berichts-Generator zu öffnen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützung für Installation, Deinstallation und Berichts-Generator](../install-uninstall-and-report-builder-support.md)   
 [Reporting Services Installation im SharePoint-Modus &#40;SharePoint 2010 und SharePoint 2013&#41;](../install-windows/install-reporting-services-sharepoint-mode.md)   
 [Reporting Services Berichts Server](../reporting-services-report-server.md)   
 [Abfrage Entwurfs Tools in Berichts-Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md)   
 [Reporting Services-Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)  
  
  
