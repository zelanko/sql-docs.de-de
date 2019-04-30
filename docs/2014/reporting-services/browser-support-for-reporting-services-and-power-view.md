---
title: Planen der Unterstützung für Reporting Services und Power View-Browser (Reporting Services 2014)
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 58ed105619ca5ad5eadb00271e18ddaa10c6bfe3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63266821"
---
# <a name="planning-for-reporting-services-and-power-view-browser-support-reporting-services-2014"></a>Planen der Unterstützung für Reporting Services und Power View-Browser (Reporting Services 2014)
  Verwenden Sie in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] einen Webbrowser zum Anzeigen von Berichten und zum Ausführen des Berichts-Managers. Nicht alle Berichtsfunktionen werden von allen Browsern unterstützt. Dieses Thema behandelt die Unterstützung und die Anforderungen für Verwaltungsfunktionen des Berichts-Managers, die Anzeige von Berichten und die ReportViewer-Steuerelemente in Visual Studio. In diesem Thema werden auch die für die unterstützten Browser verfügbaren Funktionen sowie Authentifizierungs- und Skriptanforderungen zusammengefasst.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus | [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im einheitlichen Modus  
  
 **In diesem Thema:**  
  
- [Power View-Browserszenarien](#bkmk_powerview)  
  
- [Browseranforderungen für Berichts-Manager (einheitlicher Modus)](#bkmk_reportmanager)  
  
- [Browseranforderungen zum Anzeigen von Berichten](#bkmk_reportviewer)  
  
- [Anforderungen für die Authentifizierung](#bkmk_authentication)  
  
- [Browserunterstützung für ReportViewer-Webserversteuerelemente in Visual Studio](#bkmk_controls)  
  
##  <a name="bkmk_powerview"></a> Power View-Browserszenarien

 Welche Browser und Browserversionen [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] unterstützt, hängt vom Typ des geöffneten Dokuments ab. Excel 2013-Arbeitsmappen und "**.rdlx**"-Dateien verwenden unterschiedliche Komponenten.  
  
|Dokumenttyp|Umgebung|Browserunterstützung|  
|-------------------|-----------------|---------------------|  
|Power View-Bericht (.RDLX)|**SharePoint-Server:** [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] im integrierten SharePoint-Modus von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] und die Power View-Webanwendung.|Siehe [Power View auf dem SharePoint-Server und im integrierten SharePoint-Modus von Reporting Services](#bkmk_powerview_on_SSRS).|  
|Excel 2013-Arbeitsmappe mit Power View-Blättern|**SharePoint-Server:** [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] in Excel Services.<br /><br /> **Online SharePoint (Office 365):** [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] für Excel Web App.|Siehe [Power View in Excel Services oder Excel Web App auf SharePoint Online](#bkmk_powerview_on_ExcelServices).|  
  
###  <a name="bkmk_powerview_on_SSRS"></a> Power View in SharePoint Server und SharePoint integrierten Modus von Reporting Services  
 In der folgenden Tabelle werden die Browserversionen für [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] zusammengefasst, die unterstützt werden, wenn ein Benutzer einen Power View-Bericht (.RDLX) auf einer SharePoint-Farm öffnet, auf der eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendung und das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint installiert und konfiguriert ist.  
  
- Die Tabelle gilt für SharePoint 2010 und SharePoint 2013.  
  
- Weitere Informationen zur SharePoint 2013-Browserunterstützung finden Sie unter [Planen der Browserunterstützung in SharePoint 2013](https://technet.microsoft.com//library/cc263526\(office.15\).aspx) (https://technet.microsoft.com/library/cc263526(office.15).aspx).  
  
- Weitere Informationen zur SharePoint 2010-Browserunterstützung finden Sie unter [Planen der Browserunterstützung (SharePoint Server 2010)](https://technet.microsoft.com/library/cc263526\(office.14\).aspx) (https://technet.microsoft.com/library/cc263526(office.14).aspx).  
  
|**Browser**|**Windows 8 und 8.1**|**Windows 7**|**Windows Server 2012 und 2012 R2**|**Windows Server 2008 R2**|**Windows Server 2008**|**Mac OS X 10.6-10.9**|  
|-----------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-----------------------------|------------------------------|  
|**Internet Explorer 11 (für den Desktop)**|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|Nicht unterstützt|  
|**Internet Explorer 10 (für den Desktop)**|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|Nicht unterstützt|  
|**InternetExplorer 9**|Nicht unterstützt|32-Bit, 64-Bit|Nicht unterstützt|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|  
|**InternetExplorer 8**|Nicht unterstützt|32-Bit, 64-Bit|Nicht unterstützt|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|  
|**Mozilla Firefox (neueste öffentlich freigegebene Version)**|32-Bit|32-Bit|32-Bit|32-Bit|32-Bit|Nicht unterstützt|  
|**Apple Safari (neueste öffentlich freigegebene Version)**|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|32-Bit, 64-Bit|  
  
> [!NOTE]  
> "32-Bit" bezieht sich auf den Browser und nicht auf das Betriebssystem. Sie können z. B. eine 32-Bit-Version von Internet Explorer 9 unter einer 64-Bit-Version von Windows 7 verwenden.  
  
#### <a name="inprivate-browsing-feature-in-internet-explorer"></a>InPrivate-Browsen in Internet Explorer

 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] unterstützt nicht die Funktion InPrivate-Browsen in [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 8 und Internet Explorer 9. Weitere Informationen zum InPrivate-Browsen finden Sie unter [Was ist InPrivate-Browsen?](http://windows.microsoft.com/Windows7/What-is-InPrivate-Browsing) (http://windows.microsoft.com/Windows7/What-is-InPrivate-Browsing).  
  
###  <a name="bkmk_powerview_on_ExcelServices"></a> Power View in Excel Services oder Excel Web App auf SharePoint Online

 In der folgenden Tabelle werden die Browserversionen für [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] zusammengefasst, die unterstützt werden, wenn ein Benutzer eine Excel 2013-Arbeitsmappe mit Power View-Blättern auf einem SharePoint Server öffnet, auf dem Excel Services ausgeführt wird:  
  
-   Weitere Informationen zur SharePoint 2013-Browserunterstützung finden Sie unter [Planen der Browserunterstützung in SharePoint 2013](https://technet.microsoft.com/library/cc263526\(office.15\).aspx) (https://technet.microsoft.com/library/cc263526(office.15).aspx).  
  
|**Browser**|**Windows 8 und 8.1**|**Windows 7**|**Windows Server 2012 und 2012 R2**|**Windows Server 2008 R2**|**Windows Server 2008**|**Mac OS X 10.6-10.9**|  
|-----------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-----------------------------|------------------------------|  
|**Internet Explorer 11 (für den Desktop)**|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|Nicht unterstützt|  
|**Internet Explorer 10 (für den Desktop)**|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|Nicht unterstützt|  
|**InternetExplorer 9**|Nicht unterstützt|32-Bit, 64-Bit|Nicht unterstützt|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|  
|**InternetExplorer 8**|Nicht unterstützt|32-Bit, 64-Bit|Nicht unterstützt|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|  
|**Mozilla Firefox (neueste öffentlich freigegebene Version)**|32-Bit|32-Bit|32-Bit|32-Bit|32-Bit|32-Bit, 64-Bit|  
|**Apple Safari (neueste öffentlich freigegebene Version)**|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|32-Bit, 64-Bit|  
|**Google Chrome (neueste öffentlich freigegebene Version)**|32-Bit- **(\*)** für begrenzte Zeit|32-Bit- **(\*)** für begrenzte Zeit|32-Bit- **(\*)** für begrenzte Zeit|32-Bit- **(\*)** für begrenzte Zeit|32-Bit- **(\*)** für begrenzte Zeit|Nicht unterstützt|  
  
 **(\*)** Chrome wird die Unterstützung der Netscape-Plug-Ins API (NPAPI) von Silverlight verwendete eingestellt. Power View ist von Silverlight abhängig.  Weitere Informationen finden Sie unter [Countdown für NPAPI](http://blog.chromium.org/2014/11/the-final-countdown-for-npapi.html).  
  
##  <a name="bkmk_reportmanager"></a> Browseranforderungen für Berichts-Manager (einheitlicher Modus)

 Im Folgenden finden Sie die die aktuelle Liste der unterstützten Browser, mit denen Sie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichts-Manager im einheitlichen Modus ausführen können, um Berichte und den Berichtsserver zu verwalten.  
  
|-Browser|  
|-------------|  
|Internet Explorer 7 oder höher, und Skripts müssen aktiviert sein.|  
|Mozilla FireFox (neueste öffentlich freigegebene Version)|  
|Apple Safari (neueste öffentlich freigegebene Version)|  
|Google Chrome (neueste öffentlich freigegebene Version)|  
  
##  <a name="bkmk_reportviewer"></a> Browseranforderungen zum Anzeigen von Berichten

 Im Folgenden finden Sie die aktuelle Liste der Browser und Funktionen, die mit dem Berichts-Viewer unterstützt werden. Der Berichts-Viewer unterstützt die Anzeige von Berichten vom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichts-Manager und von den SharePoint-Bibliotheken.  
  
|**Browser**|**Windows 8 und 8.1**|**Windows 7**|**Windows Server 2012 und 2012 R2**|**Windows Server 2008 R2**|**Windows Server 2008**|**Mac OS X 10.6-10.9**|**iOS 6-7 für iPad**|  
|-----------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-----------------------------|------------------------------|----------------------------|  
|**Internet Explorer 11 (für den Desktop)**|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|  
|**Internet Explorer 10 (für den Desktop)**|32-Bit, 64-Bit|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|  
|**InternetExplorer 9**|Nicht unterstützt|32-Bit, 64-Bit|Nicht unterstützt|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|Nicht unterstützt|  
|**InternetExplorer 8**|Nicht unterstützt|32-Bit, 64-Bit|Nicht unterstützt|32-Bit, 64-Bit|32-Bit, 64-Bit|Nicht unterstützt|Nicht unterstützt|  
|**InternetExplorer 7**|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|32-Bit, 64-Bit|Nicht unterstützt|Nicht unterstützt|  
|**Mozilla Firefox (neueste öffentlich freigegebene Version)**|32-Bit|32-Bit|32-Bit|32-Bit|32-Bit|Nicht unterstützt|Nicht unterstützt|  
|**Apple Safari (neueste öffentlich freigegebene Version)**|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|32-Bit, 64-Bit|Unterstützt mit eingeschränkten Funktionen <sup>(1)</sup>|  
|**Google Chrome (neueste öffentlich freigegebene Version)**|32-Bit|32-Bit|32-Bit|32-Bit|32-Bit|Nicht unterstützt|Nicht unterstützt|  
  
 **<sup>(1)</sup>**  Die folgenden Funktionen werden unterstützt:  
  
- Exportieren in das PDF- und TIFF-Format.  
  
- Interaktives Anzeigen von Berichten in Apple Safari auf iOS-Geräten. Die unterstützten Funktionen umfassen das Erweitern/Reduzieren, den Parameterbereich sowie die interaktive Sortierung.  
  
- Weitere Informationen finden Sie unter [anzeigen Reporting Services-Berichten auf Microsoft Surface-Geräten und Apple iOS-Geräten](../../2014/reporting-services/view-reporting-services-reports-surface-ios-devices.md).  
  
 **Hinweis** Wenn Sie von einem Macintosh-Computer auf einen Berichtsserver zugreifen, empfiehlt sich die Verwendung von Safari. Informationen bei Verwendung eines SharePoint-Produkts, das in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]integriert ist, finden Sie unter [Browserunterstützung (Windows SharePoint Services)](https://go.microsoft.com/fwlink/?LinkId=183583).  
  
### <a name="url-access-for-viewing-reports"></a>URL-Zugriff zum Anzeigen von Berichten

 Um Berichte nicht im Berichts-Manager, sondern direkt anzuzeigen, stellen Sie über den URL-Zugriff eine Verbindung mit dem Bericht und Berichts-Viewer her. Der URL-Zugriff unterstützt verschiedene Browser.  
  
 Weitere Informationen zum URL-Zugriff finden Sie im folgenden Thema:  
  
- [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](url-access-parameter-reference.md)  
  
###  <a name="bkmk_authentication"></a> Anforderungen für die Authentifizierung

 Browser unterstützen spezifische Authentifizierungsschemas, die vom Berichtsserver verarbeitet werden müssen, damit die Clientanforderung nicht fehlschlägt. In der folgenden Tabelle sind die Standardauthentifizierungstypen angegeben, die von den einzelnen unter einem Windows-Betriebssystem ausgeführten Browsern unterstützt werden.  
  
|**Browsertyp**|**Unterstützt**|**Browserstandard**|**Serverstandard**|  
|----------------------|------------------|-------------------------|------------------------|  
|**InternetExplorer**|Ausgehandelt, Kerberos, NTLM, Standard|Aushandeln|Ja. Die Standardauthentifizierungseinstellungen können mit Internet Explorer verwendet werden.|  
|**Firefox**|NTLM, Standard|NTLM|Ja. Die Standardauthentifizierungseinstellungen können mit Firefox verwendet werden.|  
|**Safari**|Standard|Standard|Ja. Die Standardauthentifizierungseinstellungen können mit Safari verwendet werden.|  
|**Chrome**|Ausgehandelt, NTLM, Standard|Ausgehandelt|Ja. Die Standardauthentifizierungseinstellungen können mit Chrome verwendet werden.|  
  
### <a name="script-requirements"></a>Skriptanforderungen

 Um den Berichts-Viewer zu verwenden, konfigurieren Sie den Browser für die Ausführung von Skripts.  
  
 Wenn die Skripterstellung nicht aktiviert ist, wird beim Öffnen eines Berichts eine Fehlermeldung ähnlich der folgenden angezeigt:  
  
- **Der Browser unterstützt keine Skripts oder konfiguriert wurde, dass die Ausführung von Skripts nicht zulässig. Klicken Sie hier, um den Bericht ohne Skripts anzuzeigen**.  
  
 Wenn Sie den Bericht ohne Skriptunterstützung anzeigen, wird der Bericht ohne Funktionen des Berichts-Viewers, wie z. B. die Berichtssymbolleiste oder die Dokumentstruktur, in HTML gerendert.  
  
> [!NOTE]  
> Die Berichtssymbolleiste ist Teil der HTML-Viewerkomponente. Die Symbolleiste wird standardmäßig oberhalb der jeweiligen in einem Browserfenster gerenderten Berichte angezeigt. Der Berichts-Viewer stellt Funktionen bereit, mit denen Sie den Bericht nach Informationen durchsuchen, einen Bildlauf zu einer bestimmten Seite durchführen und die Seitengröße aus Darstellungsgründen anpassen können. Weitere Informationen zur Berichtssymbolleiste oder zum HTML-Viewer finden Sie unter [HTML Viewer and the Report Toolbar](html-viewer-and-the-report-toolbar.md).  
  
##  <a name="bkmk_controls"></a> Browserunterstützung für ReportViewer-Webserversteuerelemente in Visual Studio

 Das ReportViewer-Webserversteuerelement wird verwendet, um Berichtsfunktionen in eine ASP.NET-Webanwendung einzubetten. Die Steuerelemente sind in Visual Studio enthalten und unterstützen andere Browser und Browserversionen als die anderen in diesem Thema beschriebenen Komponenten. Der Browsertyp, mit dem die Anwendung angezeigt wird, bestimmt die Art der ReportViewer-Funktionalität, die Sie in der Anwendung bereitstellen können. Ermitteln Sie mithilfe der Tabelle in diesem Thema, welche der unterstützten Browser Einschränkungen bei den Berichtsfunktionen unterliegen und welche Plattformen unterstützt werden.  
  
 Aufgrund von Unterschieden in den Rendering-Engines der unterstützten Browser können einige erweiterte Berichtsfunktionen in verschiedenen Browsern unterschiedlich angezeigt werden.  Dies gilt z. B. für die Textdrehung.  
  
### <a name="scripting-requirements"></a>Skriptanforderungen

 Verwenden Sie einen Browser, in dem die Skriptunterstützung aktiviert ist. Wenn der Browser keine Skripts ausführen kann, können Sie den Bericht nicht anzeigen.  
  
### <a name="browser-requirements-for-viewing-reports-with-the-reportviewer-web-server-controls"></a>Browseranforderungen zum Anzeigen von Berichten mit den ReportViewer-Webserversteuerelementen

 Unterstützung für interaktive Berichtfunktionen variieren je nach Browsertyp. Die folgende Unterstützungsmatrix veranschaulicht, welche Browsertypen auf welchen Plattformen unterstützt werden. Dies unterliegt jedoch den Einschränkungen in der Spalte mit den Hinweisen.  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|**Browser**|**Windows 8** und **Windows 8.1**|**Windows 7**|**Windows Server 2012** und **2012 R2**|**Windows Server 2008** und **2008 R2**|**Windows Server 2003**|**Mac OS X 10.6-10.9**|**Hinweise**|  
|**Internet Explorer 11 (für den desktop**|Ja|Ja|Ja|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Internet Explorer unterstützt sämtliche ReportViewer-Funktionen.|  
|**Internet Explorer 10 (für den Desktop)**|Ja|Ja|Ja|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Internet Explorer unterstützt sämtliche ReportViewer-Funktionen.|  
|**InternetExplorer 9**|Nicht unterstützt|Ja|Nicht unterstützt|Ja|Ja|Ja|Internet Explorer unterstützt sämtliche ReportViewer-Funktionen.|  
|**Internet Explorer 8.0**|Nicht unterstützt|Ja|Nicht unterstützt|Ja|Ja<sup>1</sup>|Nicht unterstützt|Internet Explorer unterstützt sämtliche ReportViewer-Funktionen. <sup>1</sup>|  
|**Internet Explorer 7.0**|Nicht unterstützt|Ja|Nicht unterstützt|Ja|Ja<sup>1</sup>|Nicht unterstützt|Internet Explorer unterstützt sämtliche ReportViewer-Funktionen. <sup>1</sup>|  
|**Firefox (neueste öffentlich freigegebene Version)**|Ja|Ja|Ja|Ja|Ja|Nicht unterstützt|Drucken und Zoomen werden nicht unterstützt.|  
|**Safari (neueste öffentlich freigegebene Version)**|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|Ja|Drucken und Zoomen werden nicht unterstützt.<br /><br /> Das Kalender-Steuerelement zur Auswahl von Datumsangaben in einem parametrisierten Bericht ist in diesem Browser deaktiviert. Benutzer müssen die gewünschten Datumsangaben manuell im Eingabeaufforderungsbereich für Parameter eingeben.|  
|**Chrome (neueste öffentlich freigegebene Version)**|Ja|Ja|Ja|Ja|Ja|Nicht unterstützt|Drucken und Zoomen werden nicht unterstützt.|  
  
 <sup>1</sup>im Standardmodus, Internet Explorer 7.0 und 8.0 werden nicht angezeigt Schräge Zeilen in Berichten. Wenn Sie schräge Zeilen in den Berichten verwenden, legen Sie für die ASP.NET-Seite fest, dass sie im Internet Explorer im Quirksmodus ausgeführt wird. Suchen Sie dazu die \<! DOCTYPE >-Tag auf der ASP.NET-Seite. Oder suchen Sie bei Verwendung einer Masterseite das Tag in der MASTER-Datei. Dieses Tag sieht folgendermaßen aus:  
  
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
```
  
 Ersetzen Sie die \<! DOCTYPE >-Tag mit dem folgenden Tag:  
  
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">  
```
  
 Weitere Informationen zu Kompatibilitätsmodi in Internet Explorer finden Sie unter [Definieren der Dokumentkompatibilität](https://go.microsoft.com/fwlink/?LinkId=180380) (https://go.microsoft.com/fwlink/?LinkId=180380).  
  
 Weitere Informationen zum Verwenden der ReportViewer-Steuerelemente finden Sie unter [Bereitstellen von Berichten und ReportViewer-Steuerelemente](https://msdn.microsoft.com/library/ms251723.aspx) (https://msdn.microsoft.com/library/ms251723.aspx).  
  
## <a name="next-steps"></a>Nächste Schritte

 [Reporting Services-Tools](tools/reporting-services-tools.md) [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41; ](../../2014/reporting-services/report-manager-ssrs-native-mode.md) [HTML Viewer and the Report Toolbar](html-viewer-and-the-report-toolbar.md) [URL-Zugriffsparameterverweis](url-access-parameter-reference.md)  
