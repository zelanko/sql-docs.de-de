---
title: Reporting Services Berichts Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services], extensions
- report servers [Reporting Services], about report server
- rendering extensions [Reporting Services], about extensions
- extensions [Reporting Services], about extensions
- storing data [Reporting Services]
- report servers [Reporting Services]
- data processing extensions [Reporting Services], about extensions
- delivery extensions [Reporting Services], about extensions
- data storage [Reporting Services]
- components [Reporting Services], report server
- report processing [Reporting Services], extensions
- Web service [Reporting Services], report server
- storage [Reporting Services]
ms.assetid: 88ed5b97-1d28-4980-80e4-b36761f3c03a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42ede73866c45662cf653d538f59be48684c5a45
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70176184"
---
# <a name="reporting-services-report-server"></a>Reporting Services-Berichtsserver
  Dieses Thema ist eine Übersicht über den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Berichts Server, die zentrale Komponente einer [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Installation. Er besteht aus einem Paar Verarbeitungs-Engines plus einer Auflistung von besonderen Erweiterungen, mit denen die Authentifizierung, Datenverarbeitung, das Rendering und die Übermittlungsvorgänge bearbeitet werden. Ein [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver wird in einem von zwei Bereitstellungsmodi ausgeführt: dem einheitlichen Modus oder dem SharePoint-Modus. Einen Vergleich der Features finden Sie im Abschnitt [Funktionsvergleich zwischen SharePoint und einheitlichem Modus](#bkmk_featuresupport) .  
  
 **Installation:** Weitere Informationen zur [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Installation finden Sie in den folgenden Bereichen:  
  
-   [Installieren des Reporting Services-Berichtsservers im einheitlichen Modus](install-windows/install-reporting-services-native-mode-report-server.md)  
  
-   [Installieren Sie SQL Server BI-Funktionen mit SharePoint &#40;Power Pivot und Reporting Services&#41;](../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
  
 **Azure**: Informationen zur Verwendung von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] mit Azure Virtual Machines finden Sie in den folgenden Bereichen:  
  
-   [SQL Server Sie Business Intelligence in Azure Virtual Machines](https://msdn.microsoft.com//library/windowsazure/jj992719.aspx).  
  
-   [Verwenden Sie PowerShell, um eine Azure-VM mit einem Berichts Server im einheitlichen Modus zu erstellen](https://msdn.microsoft.com/library/windowsazure/dn449661.aspx).  
  
##  <a name="bkmk_top"></a>In diesem Thema  
  
-   [Übersicht über Berichts Server Modi](#bkmk_overview)  
  
-   [Funktions Vergleich zwischen SharePoint und einheitlichem Modus](#bkmk_featuresupport)  
  
-   [Einheitlicher Modus](#bkmk_nativemode)  
  
-   [Einheitlicher Modus mit SharePoint-Webparts](#bkmk_nativewithwebparts)  
  
-   [SharePoint-Modus](#bkmk_sharepointmode)  
  
-   [Berichtsprozess und Zeitplan und Übermittlungs Prozess](#bkmk_reportprocessor)  
  
-   [Berichts Server-Datenbank](#bkmk_reportdatabase)  
  
-   [Authentifizierungs-, Rendering-, Daten-und Übermittlungs Erweiterungen](#bkmk_authentication)  
  
-   [Verwandte Aufgaben](#bkmk_relatedtasks)  
  
##  <a name="bkmk_overview"></a>Übersicht über Berichts Server Modi  
 Verarbeitungs-Engines (Prozessoren) sind das Kernstück des Berichtsservers. Die Prozessoren unterstützen die Integrität des Berichtssystems und können weder geändert noch erweitert werden. Erweiterungen sind auch Prozessoren, aber sie führen spezifische Funktionen aus. 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] umfasst mindestens eine Standarderweiterung für jeden unterstützten Erweiterungstyp. Sie können einem Berichtsserver benutzerdefinierte Erweiterungen hinzufügen. Dadurch können Sie einen Berichtsserver für die Unterstützung von Funktionen erweitern, die nicht ohne Anpassungen unterstützt werden. Beispiele für benutzerdefinierte Funktionen sind u.&nbsp;a. die Unterstützung von Technologien für einmaliges Anmelden (SSO, Single Sign-On), der Berichtsausgabe in Anwendungsformaten, die nicht bereits von den Standardrenderingerweiterungen verarbeitet werden, und der Berichtsübermittlung an einen Drucker oder eine Anwendung.  
  
 Eine einzelne Berichtsserverinstanz wird von der vollständigen Auflistung von Prozessoren und Erweiterungen definiert, die eine End-to-End-Verarbeitung bieten, von der Bearbeitung der ursprünglichen Anforderung bis hin zur Präsentation eines fertigen Berichts. Mithilfe seiner Unterkomponenten verarbeitet der Berichtsserver Berichtsanforderungen und macht Berichte für einen Zugriff bei Bedarf oder eine geplante Verteilung verfügbar.  
  
 Ein Berichtsserver stellt Funktionen zum Erstellen, Rendern und Übermitteln von Berichten für eine Vielzahl von Datenquellen sowie erweiterbare Authentifizierungs- und Autorisierungsschemas bereit. Darüber hinaus enthält ein Berichtsserver Berichtsserver-Datenbanken, in denen veröffentlichte Berichte, freigegebene Datenquellen, freigegebene Datasets, Berichtsteile, freigegebene Zeitpläne und Abonnements, Berichtsdefinitionsquelldateien, Modelldefinitionen, kompilierte Berichte, Momentaufnahmen, Parameter und andere Ressourcen gespeichert sind. Außerdem bietet der Berichtsserver dem Systemadministrator die Möglichkeit, die Verarbeitung von Berichtsanforderungen sowie die Verwaltung von Momentaufnahmeverläufen und Berechtigungen für Berichte, Datenquellen, Datasets und Abonnements zu konfigurieren.  
  
 Ein [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver unterstützt zwei Bereitstellungsmodi für Berichtsserverinstanzen:  
  
-   Einheitlicher **Modus**: einschließlich des einheitlichen Modus mit SharePoint-Webparts, bei dem ein Berichts Server als Anwendungsserver ausgeführt wird, der alle Verarbeitungs-und [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Verwaltungsfunktionen ausschließlich über-Komponenten bereitstellt. Sie konfigurieren einen Berichtsserver im einheitlichen Modus mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Konfigurations-Manager und SQL Server Management Studio.  
  
-   **SharePoint-Modus**: in diesem Modus wird ein Berichts Server als Teil einer SharePoint-Serverfarm installiert.  Verwenden Sie PowerShell-Befehle oder SharePoint-Inhaltsverwaltungsseiten, um den SharePoint-Modus bereitzustellen und zu konfigurieren.  
  
 In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] kann ein Berichtserver nicht von einem Modus in den anderen wechseln. Wenn Sie den in Ihrer Umgebung verwendeten Berichtsservertyp ändern möchten, müssen Sie den gewünschten Berichtsservermodus installieren und dann die Berichtselemente oder Berichtsserver-Datenbank vom Berichtsserver der älteren Version auf den neuen Berichtsserver kopieren oder verschieben. Dieser Prozess wird in der Regel als „Migration“ bezeichnet. Die für das Migrieren erforderlichen Schritte hängen vom Modus ab, zu dem Sie migrieren, und von der Version, von der Sie migrieren. Weitere Informationen finden Sie unter [Upgrade and Migrate Reporting Services](install-windows/upgrade-and-migrate-reporting-services.md).  
  
##  <a name="bkmk_featuresupport"></a>Funktions Vergleich zwischen SharePoint und einheitlichem Modus  
  
|Funktion oder Komponente|-Modus|-SharePoint-Modus|  
|--------------------------|-----------------|---------------------|  
|**URL-Adressierung**|Ja|Im integrierten SharePoint-Modus wird eine andere URL-Adressierung verwendet. SharePoint-URLs werden verwendet, um auf Berichte, Berichtsmodelle, freigegebene Datenquellen und Ressourcen zu verweisen. Die Ordnerhierarchie des Berichtsservers wird nicht verwendet. Falls Sie über benutzerdefinierte Anwendungen verfügen, die vom URL-Zugriff abhängig sind, wie auf einem Berichtsserver im einheitlichen Modus unterstützt, funktionieren diese Funktionen nicht mehr, wenn der Berichtsserver für die SharePoint-Integration konfiguriert ist.<br /><br /> Weitere Informationen zum URL-Zugriff finden Sie unter [URL-Zugriffsparameterverweis](url-access-parameter-reference.md).|  
|**Benutzerdefinierte Sicherheitserweiterungen**|Ja|
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] können auf dem Berichtsserver nicht bereitgestellt oder verwendet werden. Der Berichtsserver schließt eine spezielle Sicherheitserweiterung ein, die verwendet wird, sobald Sie einen Berichtsserver für die Ausführung im integrierten SharePoint-Modus konfigurieren. Diese Sicherheitserweiterung ist eine interne Komponente, die für integrierte Vorgänge erforderlich ist.|  
|**Konfigurations-Manager**|Ja|** \* Wichtig \* \* ** Configuration Manager können nicht zum Verwalten eines Berichts Servers im SharePoint-Modus verwendet werden. Verwenden Sie stattdessen die SharePoint-Zentraladministration.|  
|**Berichts-Manager**|Ja|Der Berichts-Manager kann nicht zum Verwalten des SharePoint-Modus verwendet werden. Verwenden Sie die SharePoint-Anwendungsseiten. Weitere Informationen finden Sie unter [Reporting Services-SharePoint-Dienst und -Dienstanwendungen](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).|  
|**Verknüpfte Berichte**|Ja|Nein.|  
|**Meine Berichte**|Ja|Nein|  
|**Meine Abonnements** und Batch Verarbeitungsmethoden.|Ja|Nein|  
|**Datenwarnungen**|Nein|Ja|  
|**Power View**|Nein|Ja<br /><br /> Erfordert Silverlight im Clientbrowser. Weitere Informationen zu den Browser Anforderungen finden Sie [unter Planning for Reporting Services und Power View Browser Support &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)|  
|**. RDL-Berichte**|Ja|Ja<br /><br /> .RDL-Berichte können für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver im einheitlichen Modus oder SharePoint-Modus ausgeführt werden.|  
|**. Rdlx-Berichte**|Nein|Ja<br /><br /> Power View-.RDLX-Berichte können nur für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver im SharePoint-Modus ausgeführt werden.|  
|**Anmelde Informationen für das SharePoint-Benutzer Token für die SharePoint-Listen Erweiterung**|Nein|Ja|  
|**AAM-Zonen für bereit Stellungen mit Internet Zugriff**|Nein|Ja|  
|**SharePoint-Sicherung und-Wiederherstellung**|Nein|Ja|  
|**ULS-Protokoll Unterstützung**|Nein|Ja|  
  
##  <a name="bkmk_nativemode"></a>Einheitlicher Modus  
 Im einheitlichen Modus ist ein Berichtsserver ein eigenständiger Anwendungsserver, der das Anzeigen, Verwalten, Verarbeiten und Übermitteln von Berichten und Berichtsmodellen ermöglicht. Dies ist der Standardmodus für Berichtsserverinstanzen. Sie können einen Berichtsserver im einheitlichen Modus installieren, der während des Setups konfiguriert wird, oder Sie können ihn für Vorgänge im einheitlichen Modus konfigurieren, nachdem das Setup abgeschlossen ist.  
  
 Im nachfolgenden Diagramm ist die Drei-Ebenen-Architektur einer [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Bereitstellung im einheitlichen Modus zu sehen. Hieraus gehen die Berichtsserverdatenbank und die Datenquellen auf der Datenebene, die Berichtsserverkomponenten auf der mittleren Ebene sowie die Clientanwendungen und integrierten bzw. benutzerdefinierten Tools auf der Präsentationsebene hervor. Daneben zeigt es den Fluss von Anforderungen und Daten zwischen den Serverkomponenten sowie welche Komponenten Inhalte an einen Datenspeicher senden bzw. aus einem Datenspeicher abrufen.  
  
 ![Reporting Services-Architektur](media/reporting-serv-arch.gif "Reporting Services-Architektur")  
  
 Der Berichtsserver wird als [!INCLUDE[msCoName](../includes/msconame-md.md)] -Windows-Dienst implementiert, der so genannte "Berichtsserverdienst", der einen Webdienst, die Hintergrundverarbeitung und andere Vorgänge hostet. In der Dienste-Konsolenanwendung wird der Dienst als SQL Server Reporting Services (MSSQLSERVER) aufgelistet.  
  
 Entwickler von Drittanbietern können zusätzliche Erweiterungen erstellen, um die Verarbeitungsfunktionen des Berichtsservers zu ersetzen oder zu erweitern. Weitere Informationen zu befehlsorientierten Benutzerschnittstellen, die Anwendungsentwicklern zur Verfügung stehen, finden Sie in der [Technischen Referenz](../../2014/reporting-services/technical-reference-ssrs.md).  
  
###  <a name="bkmk_nativewithwebparts"></a>Einheitlicher Modus mit SharePoint-Webparts  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]bietet zwei Webparts, die Sie auf einer Instanz von [!INCLUDE[winSPServ](../includes/winspserv-md.md)] 2,0 oder höher oder SharePoint Portal Server 2003 oder höher installieren und registrieren können. Sie können die Webparts von einer SharePoint-Website aus verwenden, um Berichte zu suchen und anzuzeigen, die auf einem Berichtsserver im einheitlichen Modus gespeichert und verarbeitet werden. Diese Webparts wurden in früheren Versionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]eingeführt.  
  
##  <a name="bkmk_sharepointmode"></a>SharePoint-Modus  
 Im SharePoint-Modus muss ein Berichtsserver als Teil einer SharePoint-Serverfarm ausgeführt werden. Die Verarbeitungs-, Rendering- und Verwaltungsfunktionen des Berichtsservers werden durch einen SharePoint-Anwendungsserver dargestellt, der den gemeinsamen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Dienst und eine oder mehrere [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendungen ausführt. Eine SharePoint-Website stellt den Front-End-Zugriff auf Berichtsserverinhalt und -vorgänge bereit.  
  
 Der SharePoint-Modus erfordert:  
  
-   [!INCLUDE[SPF2010](../includes/spf2010-md.md)]oder [!INCLUDE[SPS2010](../includes/sps2010-md.md)].  
  
-   Eine entsprechende Version des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-Ins für SharePoint 2010-Produkte.  
  
-   Ein SharePoint-Anwendungsserver, auf dem der gemeinsame [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienst installiert ist, und mindestens eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendung.  
  
 Die folgende Abbildung zeigt eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Umgebung im SharePoint-Modus:  
  
 ![Funktionale SSRS SharePoint-Architektur](media/rs-sharepoint-architecture.gif "Funktionale SSRS SharePoint-Architektur")  
  
||BESCHREIBUNG|  
|-|-----------------|  
|**1**|Webserver oder Web-Front-Ends (WFE). Das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In muss auf jedem Webserver installiert sein, von dem aus Sie die Webanwendungsfunktionen nutzen möchten, beispielsweise Berichte oder [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Verwaltungsseiten für Tasks (z. B. das Verwalten von Datenquellen oder Abonnements) anzeigen.|  
|**2,2**|Das Add-In installiert URL- und SOAP-Endpunkte für das Kommunizieren der Clients mit den Anwendungsservern über den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstproxy.|  
|**€**|Anwendungsserver, auf denen der gemeinsame [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienst ausgeführt wird. Das horizontale Skalieren der Berichtsverarbeitung wird im Rahmen der SharePoint-Farm verwaltet und durch das Hinzufügen des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Diensts zu zusätzlichen Anwendungsservern.|  
|**0:**|Sie können mehrere [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendungen erstellen mit unterschiedlichen Konfigurationen, einschließlich Berechtigungen, E-Mail, Proxys und Abonnements.|  
|**5**|Berichte, Datenquellen und andere Elemente werden in den SharePoint-Inhaltsdatenbanken gespeichert.|  
|**6**|
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendungen erstellen drei Datenbanken für Berichtsserver-, temp- und Datenwarnungsfunktionen. Konfigurationseinstellungen, die für alle SSRS-Dienstanwendungen gelten, werden in der Datei **RSReportserver.config** gespeichert.|  
  
##  <a name="bkmk_reportprocessor"></a>Berichtsprozess und Zeitplan und Übermittlungs Prozess  
 Der Berichtsserver enthält zwei Verarbeitungs-Engines, die die vorbereitende Berichtsverarbeitung und die Zwischenberichtsverarbeitung sowie Zeitplanungs- und Übermittlungsvorgänge ausführen. Der Berichtsprozessor ruft die Berichtsdefinition oder das Berichtsmodell ab, kombiniert die Layoutinformation mit Daten der Datenverarbeitungserweiterung und rendert sie im gewünschten Format. Der Zeitplanungs- und Übermittlungsprozess verarbeitet Berichte, die durch einen Zeitplan ausgelöst werden, und übermittelt Berichte an Ziele.  
  
##  <a name="bkmk_reportdatabase"></a>Berichts Server-Datenbank  
 Der Berichtsserver ist ein statusloser Server, der alle Eigenschaften, Objekte und Metadaten in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank speichert. Zu den gespeicherten Daten gehören veröffentlichte Berichte, kompilierte Berichte, Berichtsmodelle und die Ordnerhierarchie, die die Adressierung für alle vom Berichtsserver verwalteten Elemente bereitstellt. Eine Berichtsserver-Datenbank kann internen Speicher für eine einzelne [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Installation oder für mehrere Berichtsserver bereitstellen, die Teil einer Bereitstellung für horizontales Skalieren sind. Wenn Sie einen Berichtsserver für die Ausführung in einer großen Bereitstellung eines SharePoint-Produkts oder einer SharePoint-Technologie konfigurieren, verwendet der Berichtsserver die SharePoint-Datenbanken zusätzlich zur Berichtsserver-Datenbank. Weitere Informationen zu Datenspeichern in einer Reporting Services-Installation finden Sie unter [Report Server Database &#40;SSRS Native Mode&#41;](report-server/report-server-database-ssrs-native-mode.md).  
  
##  <a name="bkmk_authentication"></a>Authentifizierungs-, Rendering-, Daten-und Übermittlungs Erweiterungen  
 Der Berichtsserver unterstützt die folgenden Erweiterungsarten: Authentifizierungserweiterungen, Datenverarbeitungserweiterungen, Berichtsverarbeitungserweiterungen, Renderingerweiterungen und Übermittlungserweiterungen. Ein Berichtsserver erfordert mindestens eine Authentifizierungserweiterung, Datenverarbeitungserweiterung und Renderingerweiterung. Übermittlungserweiterungen und benutzerdefinierte Berichtsverarbeitungserweiterungen sind zwar optional, jedoch erforderlich, wenn Sie die Berichtsverteilung oder benutzerdefinierte Steuerelemente unterstützen möchten.  
  
 Reporting Services bietet Standarderweiterungen, damit Sie alle Serverfunktionen verwenden können, ohne benutzerdefinierte Komponenten entwickeln zu müssen. In der folgenden Tabelle werden die Standarderweiterungen beschrieben, die zu einer vollständigen Berichtsserverinstanz beitragen, die einsatzbereite Funktionen bietet:  
  
|type|Standard|  
|----------|-------------|  
|Authentication|Eine Standard-Berichtsserverinstanz unterstützt die Windows-Authentifizierung, einschließlich Identitätswechsel- und Delegationsfunktionen, falls diese in Ihrer Domäne aktiviert sind.|  
|Datenverarbeitung|Eine Standard-Berichtsserverinstanz bietet Datenverarbeitungserweiterungen für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-, Oracle-, Hyperion Essbase-, SAPBW-, OLE DB-, Parallel Data Warehouse- und ODBC-Datenquellen.|  
|Darstellung|Eine Standard-Berichtsserverinstanz bietet Renderingerweiterungen für die Dateiformate HTML, Excel, CSV, XML, Word und PDF sowie für SharePoint-Listen und Bilddateien.|  
|Lieferung|Eine Standard-Berichtsserverinstanz schließt eine E-Mail-Übermittlungserweiterung und eine Dateifreigabe-Übermittlungserweiterung ein. Falls der Berichtsserver für die SharePoint-Integration konfiguriert ist, können Sie eine Übermittlungserweiterung verwenden, die Berichte in eine SharePoint-Bibliothek speichert.|  
  
> [!NOTE]  
>  Reporting Services umfassen einen vollständigen Satz von Tools und Anwendungen, die Sie zum Verwalten des Servers, Erstellen von Inhalt und Verfügbarmachen dieses Inhalts für die Benutzer in Ihrem Unternehmen verwenden können.  
  
##  <a name="bkmk_relatedtasks"></a> Verwandte Aufgaben  
 Die folgenden Themen enthalten zusätzliche Informationen zum Installieren, Verwenden und Verwalten eines Berichtsservers:  
  
|Aufgabe|Link|  
|----------|----------|  
|Prüfen Sie die Hardware- und Softwareanforderungen.|[Hardware-und Software Anforderungen für Reporting Services im SharePoint-Modus](../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md).|  
|Installieren Sie [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus.|[Installieren Reporting Services SharePoint-Modus für SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|Wenn Sie ein Webentwickler sind oder Erfahrung im Erstellen von Cascading Stylesheets haben, können Sie auf eigenes Risiko die Standardstile ändern, um Farben, Schriftarten und Layout der Symbolleiste oder des Berichts-Managers zu ändern. In dieser Version sind weder die Standardstylesheets noch Anweisungen zum Ändern der Stylesheets dokumentiert.|[Anpassen von Stylesheets für den HTML-Viewer und Berichts-Manager](../../2014/reporting-services/customize-style-sheets-for-html-viewer-and-report-manager.md)|  
|Entwickler von Websites, die sich mit HTML-Formaten und Cascading Style Sheets (CSS) auskennen, können anhand der Informationen in diesem Thema ermitteln, welche Dateien geändert werden können, um die Darstellung des Berichts-Managers anzupassen.|[Konfigurieren des Berichts-Managers für die Übergabe von benutzerdefinierten Authentifizierungscookies](security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)|  
|Erläutert, wie die Speichereinstellungen für den Report Server-Webdienst und den Windows-Dienst angepasst werden können.|[Configure Available Memory for Report Server Applications (Konfigurieren von verfügbarem Speicher für Berichtsserveranwendungen)](report-server/configure-available-memory-for-report-server-applications.md)|  
|Erläutert empfohlene Schritte zur Konfiguration des Berichtsservers für die Remoteverwaltung.|[Configure a Report Server for Remote Administration (Konfigurieren eines Berichtsservers für die Remoteverwaltung)](report-server/configure-a-report-server-for-remote-administration.md)|  
|Stellt Anweisungen zum Konfigurieren der Verfügbarkeit von **Meine Berichte** auf einer einheitlichen Berichtsserverinstanz bereit.|[Aktivieren und Deaktivieren von "Meine Berichte"](report-server/enable-and-disable-my-reports.md)|  
|Stellt Anweisungen zum Einrichten des RSClientPrint-Steuerelements bereit, das Druckfunktionen innerhalb unterstützter Browser bereitstellt. Weitere Informationen zu den Browser Anforderungen finden Sie [unter Planning for Reporting Services und Power View Browser Support &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md).|[Enable and Disable Client-Side Printing for Reporting Services (Aktivieren und Deaktivieren des clientseitige Drucks für Reporting Services)](report-server/enable-and-disable-client-side-printing-for-reporting-services.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen für Reporting Services](extensions/reporting-services-extensions.md)   
 [Reporting Services-Tools](tools/reporting-services-tools.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41;](report-server/report-server-database-ssrs-native-mode.md)   
 [Implementieren einer Sicherheits Erweiterung](extensions/security-extension/implementing-a-security-extension.md)   
 [Implementieren von Datenverarbeitungserweiterungen](extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Datenquellen, die von Reporting Services &#40;SSRS unterstützt werden&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Verwalten von SSRS mithilfe von PowerShell](https://sqlbelle.wordpress.com/2015/08/17/automate-ssrs-report-generation-using-powershell/)  
  
  
