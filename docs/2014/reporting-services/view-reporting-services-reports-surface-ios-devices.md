---
title: Anzeigen von Reporting Services-Berichten auf Microsoft Surface-Geräten und Apple iOS-Geräten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 89560cb29adfe83435d9b02a4b10e568a79ad352
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013401"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a>Anzeigen von Reporting Services-Berichten auf Microsoft Surface-Geräten und Apple iOS-Geräten
  In diesem Artikel werden die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen und -Workflows beschrieben, die für Microsoft Surface-Geräte sowie für Geräte mit Apple iOS 6 und Apple Safari (z. B. iPad) unterstützt werden.  
  
## <a name="view-and-interact-with-reports"></a>Anzeigen und Interagieren mit Berichten  
 Ab [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]unterstützt [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] die Anzeige und grundlegende interaktive Berichtsfunktionen auf Microsoft Surface-Geräten sowie Geräten mit Apple iOS 6 und dem Apple Safari-Browser (z. B. iPad). Sie können Berichte auch mit Microsoft Surface-Geräten veröffentlichen.  
  
 ![IPad-Desktop](media/videothumbnail.jpg "IPad-Desktop")  
Schauen Sie sich eine Demo der Berichtsanzeige auf einem iPad an.  
  
 Sie können [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichte auch auf einem Windows Phone 8-Gerät anzeigen.  
  
 Um die in diesem Thema beschriebenen Funktionen zu nutzen, installieren Sie eine der folgenden Komponenten:  
  
-   Berichtsserver im einheitlichen Modus: Installieren Sie [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] oder höher.  
  
     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] steht für den Download der [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=35575).  
  
-   Berichtsserver im SharePoint-Modus: Installieren Sie [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] oder höher aus dem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte.  
  
 **Zum Anzeigen und interagieren mit einem Bericht auf einem iPad oder Microsoft Surface-Gerät**  
  
1.  Stellen Sie sicher, dass Sie mit dem Berichtsserver oder der SharePoint-Website, auf dem bzw. der sich der Bericht befindet, eine Verbindung herstellen können.  
  
2.  Öffnen Sie den Bericht, indem Sie einen der folgenden Schritte ausführen.  
  
    -   **Starten von E-mail:** Tippen Sie in einer E-Mail, die von einem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Abonnement erstellt wurde, auf die URL des Berichts. Der Bericht wird im Browser geöffnet.  
  
    -   **Starten Sie vom Berichtsserver:** Durchsuchen Sie das Verzeichnis auf dem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Berichtsserver, und tippen Sie auf den Berichtsnamen, um den Bericht zu öffnen.  
  
    -   **Starten Sie von einer SharePoint-Dokumentbibliothek:** Navigieren Sie zu einer SharePoint-Dokumentbibliothek, die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Berichte enthält, und tippen Sie dann auf den Berichtsnamen. Sie können den Bericht anzeigen und damit interagieren.  
  
        > [!IMPORTANT]  
        >  Achten Sie bei einem iPad darauf, dass die Eigenschaft **Privates Surfen** für Safari deaktiviert ist.  
  
    -   **SharePoint-Webpart:** Wenn das Webpart einer SharePoint-Seite hinzugefügt wurde, können Sie [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Berichte anzeigen.  
  
3.  Auf Ihrem Microsoft Surface-Gerät können Sie den Bericht auch mithilfe des Berichts-Managers öffnen. Durchsuchen Sie das Verzeichnis im [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichts-Manager, und tippen Sie auf den Berichtsnamen, um den Bericht zu öffnen.  
  
    > [!IMPORTANT]  
    >  Das Anzeigen von Berichten im Berichts-Manager wird auf iPads nicht unterstützt.  
  
4.  Zum Durchführen eines Bildlaufs und Zoomen verfahren Sie wie folgt:  
  
    -   Um einen Bildlauf im Bericht durchzuführen, fahren Sie mit dem Finger (nach oben, unten, links oder rechts) über den Bildschirm. Diese Bewegung wird als "Streifen" bezeichnet.  
  
    -   Zum Vergrößern positionieren Sie zwei Finger auf dem Bildschirm und bewegen die Finger voneinander weg. Zum Verkleinern, positionieren Sie zwei Finger auf dem Bildschirm und bewegen die Finger aufeinander zu. Diese Bewegung wird als "Zusammendrücken" bezeichnet.  
  
5.  Um im Bericht zu navigieren und damit zu interagieren, verfahren Sie wie folgt:  
  
    -   Um Berichtselemente sowie Zeilen und Spalten, die Gruppen zugeordnet sind, zu reduzieren und zu erweitern, tippen Sie zum Reduzieren auf das Pluszeichen (+) und zum Erweitern auf das Minuszeichen (-).  
  
    -   Um Zeilen in einer Tabelle oder Zeilen und Spalten in einer Matrix aufsteigend oder absteigend zu sortieren, tippen Sie auf die Sortierschaltfläche. Die Sortierschaltfläche befindet sich normalerweise in der Spaltenüberschrift.  
  
    -   Um den Parameterbereich zu erweitern und zu reduzieren, tippen Sie auf die Pfeilschaltfläche am oberen Rand des Berichts.  
  
    -   Wählen Sie einen Parameterwert aus, indem Sie auf das Feld oder Steuerelement neben dem Parameter tippen. Tippen Sie auf **Bericht anzeigen** , um den Parameterwert auf den Bericht anzuwenden.  
  
    -   Um den Berichtsinhalt zu durchsuchen, tippen Sie auf das Feld neben **Suchen**, geben einen Suchbegriff ein und tippen dann auf **Suchen**.  
  
    -   Um durch die Berichtsseiten zu blättern, tippen Sie auf die Navigationsschaltflächen. Alternativ können Sie auf das Textfeld neben den Schaltflächen tippen und die Seitenzahl eingeben.  
  
    -   Um zu URLs zu navigieren, tippen Sie auf die Hyperlinks, die Berichtselementen, z. B. Textfeldern, Bildern, Diagrammen und Messgeräten, hinzugefügt wurden.  
  
    -   Exportieren Sie den Bericht, indem Sie auf das Symbol für das **Dropdownmenü "Exportieren"** und dann auf ein Dateiformat tippen.  
  
        -   Wenn Sie den Bericht auf einem Microsoft Surface-Gerät anzeigen, können Sie den Bericht auf einen der folgenden Formate exportieren.  
  
            -   XML-Datei mit Berichtsdaten  
  
            -   CSV (durch Trennzeichen getrennt)  
  
            -   PDF  
  
            -   MHTML (Webarchiv)  
  
            -   Excel  
  
            -   TIFF  
  
            -   Wort  
  
        -   Wenn Sie den Bericht auf einem iPad anzeigen, können Sie den Bericht als TIFF- oder PDF-Datei exportieren.  
  
## <a name="authentication"></a>Authentifizierung  
 Die RSWindowsNTLM-Authentifizierung und die RSWindowsBasic-Authentifizierung können mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im einheitlichen Modus auf dem iPad verwendet werden.  
  
 Im Allgemeinen wird davon abgeraten, RSWindowsBasic in Nicht-HTTPS-Umgebungen zu verwenden, da dieser Authentifizierungstyp keine Vertrauenswürdigkeit für übermittelte Anmeldeinformationen bietet.  
  
 Weitere Informationen zur RSWindowsNTLM- und RSWindowsBasic-Authentifizierung finden Sie unter [Authentication with the Report Server](security/authentication-with-the-report-server.md).  
  
## <a name="uploading-reports"></a>Hochladen von Berichten  
 Mit den entsprechenden Berechtigungen können Sie Berichte mithilfe der folgenden Methoden über ein Microsoft Surface-Gerät veröffentlichen.  
  
> [!IMPORTANT]  
>  Auf dem iPad werden diese Methoden nicht unterstützt.  
  
-   Hochladen einer Berichtsdefinitionsdatei (RDL) in eine SharePoint-Dokumentbibliothek, indem Sie die Bibliothek öffnen und auf **Dokument hochladen**tippen.  
  
-   Hochladen einer Berichtsdefinitionsdatei in die Berichtsserver-Datenbank, indem Sie den Berichts-Manager öffnen und auf **Datei hochladen**tippen.  
  
## <a name="additional-information"></a>Weitere Informationen  
 Weitere Informationen zu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] und unterstützten Browsern finden Sie unter:  
  
-   [Browserunterstützung für Reporting Services und Power View-Browserunterstützung &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)  
  
 Weitere Informationen zu Microsoft Business Intelligence und mobilen Geräten finden Sie unter:  
  
-   [Übersicht über mobile Geräte und SharePoint 2013](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161351(v=office.15).aspx).  
  
-   [In SharePoint 2013 unterstützte Browser für mobile Geräte](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161353(v=office.15).aspx).  
  
-   [Anzeigen von Berichten und Scorecards auf Apple iPads (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx).  
  
-   [Anzeigen von Reporting Services-Berichten auf einem iPad (Video)](https://technet.microsoft.com/sqlserver/jj873792.aspx) (https://technet.microsoft.com/sqlserver/jj873792.aspx).  
  
-   [Anzeigen von Reporting Services-Berichten auf einem Microsoft Surface RT-Gerät (video)](https://technet.microsoft.com/sqlserver/dn146017)  
  
  
