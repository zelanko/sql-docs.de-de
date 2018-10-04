---
title: Berichts-Manager (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], managing
- Report Manager [Reporting Services], about Report Manager
- customizing Report Manager
- Report Manager [Reporting Services], customizing
- report servers [Reporting Services], administering
- browsing reports [Reporting Services]
- administering reports
- Report Manager [Reporting Services]
- components [Reporting Services], Report Manager
ms.assetid: 80949f9d-58f5-48e3-9342-9e9bf4e57896
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c3a102af211ccaa8fad3d7792cf868653ca4797d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48176940"
---
# <a name="report-manager--ssrs-native-mode"></a>Berichts-Manager (einheitlicher SSRS-Modus)
  Der Berichts-Manager ist ein webbasiertes Zugriffs- und Verwaltungstool für Berichte. Dieses Tool kann verwendet werden, um eine einzelne Berichtsserverinstanz von einem Remotestandort aus über eine HTTP-Verbindung zu verwalten. Sie können ebenso die Berichts-Viewer- und Navigationsfunktionen des Berichts-Managers verwenden. In diesem Thema:  
  
-   [Was ist der Berichts-Manager?](#bkmk_whatis_report_manager)  
  
-   [Starten und verwenden Sie Berichts-Manager](#bkmk_start_report_manager)  
  
-   [Symbolbeschreibungen](#bkmk_icon_descriptions)  
  
##  <a name="bkmk_whatis_report_manager"></a> Was ist der Berichts-Manager?  
 Mit dem Berichts-Manager können Sie die folgenden Aufgaben ausführen:  
  
-   Anzeigen, Suchen, Drucken und Abonnieren von Berichten.  
  
-   Erstellen, Sichern und Warten der Ordnerhierarchie zum Organisieren von Elementen auf dem Server.  
  
-   Konfigurieren der rollenbasierten Sicherheit, die den Zugriff auf Elemente und Vorgänge bestimmt.  
  
-   Konfigurieren von Berichtsausführungseigenschaften, dem Berichtsverlauf und Berichtsparameter.  
  
-   Erstellen von Berichtsmodellen, die verbinden und Abrufen von Daten aus einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenquelle oder eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relationale Datenquelle.  
  
-   Festlegen der Modellelementsicherheit für den Zugriff auf bestimmte Entitäten im Modell bzw. Zuordnen von Entitäten zu vordefinierten Berichten mit Durchklicken, die Sie im Voraus erstellen.  
  
-   Erstellen freigegebener Zeitpläne und Datenquellen für eine leichtere Verwaltung von Zeitplänen und Datenquellenverbindungen.  
  
-   Erstellen datengesteuerter Abonnements, die Berichte an eine lange Empfängerliste verteilen.  
  
-   Erstellen verknüpfter Berichte zur Wiederverwendung und Änderung des Zwecks eines vorhandenen Berichts auf verschiedene Weise.  
  
-   Starten des Berichts-Generators zum Erstellen von Berichten, die Sie auf dem Berichtsserver speichern und ausführen können.  
  
 Mit dem Berichts-Manager können die Ordner des Berichtsservers durchsucht oder nach bestimmten Berichten gesucht werden. Sie können einen Bericht, seine allgemeinen Eigenschaften und alte Versionen anzeigen, die in einem Berichtsverlauf erfasst sind. Je nach den Ihnen gewährten Berechtigungen können Sie unter Umständen Berichte abonnieren, die an ein E-Mail-Postfach oder einen freigegeben Ordner im Dateisystem übermittelt werden.  
  
> [!NOTE]  
>  Weitere Informationen zu unterstützten Browsern und Versionen finden Sie unter [Planung für Reporting Services und Power View-Browserunterstützung &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md).  
  
 Der Berichts-Manager wird nur für einen Berichtsserver verwendet, der im einheitlichen Modus ausgeführt wird. Er wird nicht für einen Berichtsserver unterstützt, den Sie für den integrierten Modus von SharePoint konfiguriert haben.  
  
 Einige Berichts-Manager-Features sind nur in bestimmten Editionen von verfügbar [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 In einer neuen Installation verfügen nur lokale Administratoren über ausreichende Berechtigungen zum Verwenden des Inhalts und der Einstellungen. Wenn Sie anderen Benutzern Berechtigungen erteilen möchten, muss ein lokaler Administrator Rollenzuweisungen erstellen, die den Zugriff auf den Berichtsserver ermöglichen. Die Anwendungsseiten und Aufgaben, auf die ein Benutzer anschließend Zugriff erhält, sind von den Rollenzuweisungen für den Benutzer abhängig. Weitere Informationen finden Sie unter [Gewähren von Benutzerzugriff auf einen Berichtsserver &#40;Berichts-Manager&#41;](security/grant-user-access-to-a-report-server.md).  
  
 Wenn Sie [!INCLUDE[wiprlhlong](../includes/wiprlhlong-md.md)] oder Windows Server 2008 verwenden, müssen Sie den Berichts-Manager für die lokale Verwaltung konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
##  <a name="bkmk_start_report_manager"></a> Starten und verwenden Sie Berichts-Manager  
 Der Berichts-Manager ist eine Webanwendung, die Sie durch Eingabe der Berichts-Manager-URL in die Adressleiste eines Browserfensters öffnen. Wenn Sie den Berichts-Manager starten, variieren die angezeigten Seiten, Links und Optionen je nach den Berechtigungen, über die Sie auf dem Berichtsserver verfügen. Um einen Task auszuführen, müssen Sie einer Rolle zugewiesen sein, die den Task einschließt. Ein Benutzer, dem eine Rolle mit vollen Berechtigungen zugewiesen wurde, hat Zugriff auf sämtliche Anwendungsmenüs und Seiten zum Verwalten eines Berichtsservers. Einem Benutzer, dem eine Rolle mit der Berechtigung zum Anzeigen und Ausführen von Berichten zugewiesen wurde, werden dagegen nur die Menüs und Seiten angezeigt, die diese Aktivitäten unterstützen. Jeder Benutzer kann über verschiedene Rollenzuweisungen für verschiedene Berichtsserver oder sogar für die verschiedenen Berichte und Ordner auf einem einzigen Berichtsserver verfügen.  
  
 Weitere Informationen zu den Rollen finden Sie unter [Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus](security/granting-permissions-on-a-native-mode-report-server.md).  
  
> [!NOTE]  
>  Wenn Sie mit Windows Vista oder Windows Server 2008 arbeiten, müssen Sie den Berichtsserver für die lokale Verwaltung konfigurieren, bevor Sie den Berichts-Manager zum Verwalten einer lokalen Berichtsserverinstanz verwenden. Anweisungen dazu, wie Sie den Server zu konfigurieren, finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="start-report-manager"></a>Start des Berichts-Managers  
  
#### <a name="to-start-report-manager-from-a-browser"></a>So starten Sie den Berichts-Manager aus einem Browser  
  
1.  Open [!INCLUDE[msCoName](../includes/msconame-md.md)] InternetExplorer 7.0 oder höher.  
  
2.  Geben Sie die URL des Berichts-Managers in die Adressleiste des Webbrowsers ein.  
  
    -   Die URL lautet standardmäßig `http://[ComputerName]/reports`.  
  
    -   Der Berichtsserver ist möglicherweise für die Verwendung eines bestimmten Ports konfiguriert. Beispiel: `http:// [ComputerName]:80/reports` oder `http:// [ComputerName]:8080/reports`.  
  
## <a name="configuring-report-manager"></a>Konfigurieren des Berichts-Managers  
 Die Berichts-Manager-Konfiguration besteht aus der Definition einer URL für die Anwendung. Eine zusätzliche Konfiguration ist erforderlich, wenn Ihre Bereitstellung den ausgeführten Berichts-Manager auf einem separaten Computer einschließt.  
  
 Sie können den Berichts-Manager nur sehr eingeschränkt anpassen. Sie können z. B. den Anwendungstitel auf der Seite Siteeinstellungen ändern. Wenn Sie ein Entwickler von Websites sind, können Sie die Stylesheets ändern, die die Stilinformationen enthalten, die vom Berichts-Manager verwendet werden. Da der Berichts-Manager nicht speziell für die Unterstützung der Anpassung entworfen wurde, müssen Sie jede Änderung, die Sie vornehmen, sorgfältig prüfen. Wenn Sie feststellen, dass der Berichts-Manager nicht Ihren Anforderungen entspricht, können Sie einen benutzerdefinierten Berichts-Viewer entwickeln oder SharePoint-Webparts konfigurieren, um Berichte auf einer SharePoint-Website zu suchen und anzuzeigen. Weitere Informationen finden Sie unter [Konfigurieren des Berichts-Managers &#40;einheitlicher Modus&#41;](report-server/configure-web-portal.md).  
  
##  <a name="bkmk_icon_descriptions"></a> Symbolbeschreibungen  
 In der folgenden Tabelle werden die Symbole beschrieben, die im Berichts-Manager verwendet werden. Weitere Informationen zu den Symbolen, die in der Symbolleiste des Berichts angezeigt werden, finden Sie unter [HTML-Viewer und die Berichtssymbolleiste](html-viewer-and-the-report-toolbar.md).  
  
|Symbol|Description|Aktion|  
|----------|-----------------|------------|  
|![Berichtsymbol](media/hlp-16doc.gif "Report icon")|Bericht|Klicken Sie auf das Berichtssymbol oder den Berichtsnamen, um den Bericht zu öffnen. Der Bericht wird in einem eigenen Fenster geöffnet.|  
|![Modellsymbol](media/model-icon.gif "Model icon")|Berichtsmodell|Klicken Sie auf das Berichtsmodellsymbol, um Eigenschaftenseiten für Modelle zu öffnen.|  
|![Symbol verknüpfte Berichte](media/hlp-16linked.gif "Linked report icon")|Verknüpfter Bericht|Klicken Sie auf das Berichtssymbol oder den Berichtsnamen, um den verknüpften Bericht zu öffnen. Der Bericht wird in einem eigenen Fenster geöffnet.|  
|![Ordnersymbol](media/hlp-16folder.gif "Folder icon")|Ordner|Klicken Sie auf das Ordnersymbol oder den Ordnernamen, um den Ordner zu öffnen.|  
|![Symbol "Abonnement"](media/hlp-16subscription.gif "Abonnement (Symbol)")|Abonnement|Klicken Sie auf ein Abonnementsymbol, um ein Abonnement zu bearbeiten.|  
|![Symbol für datengesteuertes Abonnement](media/hlp-16subscriptiondd.gif "datengesteuerten Abonnement (Symbol)")|Datengesteuertes Abonnement|Klicken Sie auf ein Symbol oder die Beschreibung für ein datengesteuertes Abonnement, um ein Abonnement zu bearbeiten.|  
|![Symbol allgemeine Ressource](media/hlp-16file.gif "generic resource icon")|Ressource|Klicken Sie auf das Ressourcensymbol oder den Ressourcennamen, um die Ressource zu öffnen. Die Ressource wird in einem eigenen Fenster geöffnet.|  
|![Symbol freigegebene Datenquelle](media/hlp-16datasource.png "Shared data source icon")|Freigegebenes Datenquellenelement|Klicken Sie auf ein Symbol für eine freigegebene Datenquelle, um die Eigenschaftenseiten, die Berichtsliste und die Abonnementliste der Datenquelle zu öffnen.|  
|![Symbol für Eigenschaftenseite](media/hlp-16prop.gif "Symbol für Eigenschaftenseite")|Eigenschaftenseite|Klicken Sie auf das Eigenschaftensymbol, um zusätzliche Seiten zu öffnen sowie Eigenschaften und die Sicherheit festzulegen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [Browserunterstützung für Reporting Services und Power View-Browserunterstützung &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)   
 [Berichts-Generator &#40;SSRS&#41;](tools/report-builder-authoring-environment-ssrs.md)   
 [Reporting Services-Tools](tools/reporting-services-tools.md)   
 [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41;](report-server/report-server-content-management-ssrs-native-mode.md)   
 [Anzeigen und Durchsuchen von Berichten im einheitlichen Modus, die mit SharePoint-Webparts &#40;SSRS&#41;](reports/view-and-explore-native-mode-reports-using-sharepoint-web-parts-ssrs.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
