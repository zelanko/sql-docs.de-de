---
title: Anzeigen von Reporting Services-Berichten auf Microsoft Surface-Geräten und Apple iOS-Geräten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
caps.latest.revision: 21
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 683a20afc442b7e10a64cac86aa0502c57dabbc0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166321"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a>Anzeigen von Reporting Services-Berichten auf Microsoft Surface-Geräten und Apple iOS-Geräten
  In diesem Artikel werden die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Funktionen und -Workflows beschrieben, die für Microsoft Surface-Geräte sowie für Geräte mit Apple iOS 6 und Apple Safari (z. B. iPad) unterstützt werden.  
  
## <a name="view-and-interact-with-reports"></a>Anzeigen und Interagieren mit Berichten  
 Beginnend mit [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die Anzeige und grundlegende interaktive Berichtsfunktionen auf Microsoft Surface-Geräte und Geräte mit Apple iOS 6 und Apple Safari-Browser wie dem iPad. Sie können Berichte auch mit Microsoft Surface-Geräten veröffentlichen.  
  
 ![IPad-Desktop](media/videothumbnail.jpg "IPad-Desktop")  
Schauen Sie sich eine Demo der Berichtsanzeige auf einem iPad an.  
  
 Sie können [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Berichte auch auf einem Windows Phone 8-Gerät anzeigen.  
  
 Um die in diesem Thema beschriebenen Funktionen zu nutzen, installieren Sie eine der folgenden Komponenten:  
  
-   Berichtsserver im einheitlichen Modus: Installieren Sie [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] oder höher.  
  
     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] steht für den Download der [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=35575).  
  
-   Für einen Berichtsserver im SharePoint-Modus installieren [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] oder höher von der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in für SharePoint-Produkte.  
  
 **Zum Anzeigen und interagieren mit einem Bericht auf einem iPad oder Microsoft Surface-Gerät**  
  
1.  Stellen Sie sicher, dass Sie mit dem Berichtsserver oder der SharePoint-Website, auf dem bzw. der sich der Bericht befindet, eine Verbindung herstellen können.  
  
2.  Öffnen Sie den Bericht, indem Sie einen der folgenden Schritte ausführen.  
  
    -   **Starten Sie über E-mail:** aus einer E-mail, die erstellt wird eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Abonnement, tippen Sie auf die URL des Berichts. Der Bericht wird im Browser geöffnet.  
  
    -   **Starten vom Berichtsserver:** durchsuchen Sie das Verzeichnis auf dem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Berichtsserver, und tippen Sie dann auf den Berichtsnamen, um den Bericht zu öffnen.  
  
    -   **Starten von einer SharePoint-Dokumentbibliothek:** navigieren Sie zu einer SharePoint-Dokumentbibliothek, die enthält [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] meldet, und tippen Sie dann auf den Namen des Berichts. Sie können den Bericht anzeigen und damit interagieren.  
  
        > [!IMPORTANT]  
        >  Achten Sie bei einem iPad darauf, dass die Eigenschaft **Privates Surfen** für Safari deaktiviert ist.  
  
    -   **SharePoint-Webpart:** , wenn das Webpart zu einer SharePoint-Seite hinzugefügt wurde, können Sie anzeigen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Berichte.  
  
3.  Auf Ihrem Microsoft Surface-Gerät können Sie den Bericht auch mithilfe des Berichts-Managers öffnen. Durchsuchen Sie das Verzeichnis in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Berichts-Manager, und tippen Sie dann auf den Berichtsnamen, um den Bericht zu öffnen.  
  
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
  
        -   Wenn Sie den Bericht auf einem Microsoft Surface-Gerät anzeigen, können Sie den Bericht in einem der folgenden Formate exportieren.  
  
            -   XML-Datei mit Berichtsdaten  
  
            -   CSV (durch Trennzeichen getrennt)  
  
            -   PDF  
  
            -   MHTML (Webarchiv)  
  
            -   Excel  
  
            -   TIFF  
  
            -   Wort  
  
        -   Wenn Sie den Bericht auf einem iPad anzeigen, können Sie den Bericht als TIFF- oder PDF-Datei exportieren.  
  
## <a name="authentication"></a>Authentifizierung  
 RSWindowsNTLM-Authentifizierung und die RSWindowsBasic-Authentifizierung arbeiten mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im einheitlichen Modus und dem iPad.  
  
 Im Allgemeinen wird davon abgeraten, RSWindowsBasic in Nicht-HTTPS-Umgebungen zu verwenden, da dieser Authentifizierungstyp keine Vertrauenswürdigkeit für übermittelte Anmeldeinformationen bietet.  
  
 Weitere Informationen zur Rswindowsntlm- und RSWindowsBasic-Authentifizierung finden Sie unter [Authentifizierung mit dem Berichtsserver](security/authentication-with-the-report-server.md).  
  
## <a name="uploading-reports"></a>Hochladen von Berichten  
 Mit den entsprechenden Berechtigungen können Sie Berichte mithilfe der folgenden Methoden über ein Microsoft Surface-Gerät veröffentlichen.  
  
> [!IMPORTANT]  
>  Auf dem iPad werden diese Methoden nicht unterstützt.  
  
-   Hochladen einer Berichtsdefinitionsdatei (RDL) in eine SharePoint-Dokumentbibliothek, indem Sie die Bibliothek öffnen und auf **Dokument hochladen**tippen.  
  
-   Hochladen einer Berichtsdefinitionsdatei in die Berichtsserver-Datenbank, indem Sie den Berichts-Manager öffnen und auf **Datei hochladen**tippen.  
  
## <a name="additional-information"></a>Weitere Informationen  
 Weitere Informationen zu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] und unterstützte Browsern finden Sie unter:  
  
-   [Browserunterstützung für Reporting Services und Power View-Browserunterstützung &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)  
  
 Weitere Informationen zu Microsoft Business Intelligence und mobilen Geräten finden Sie unter:  
  
-   [Übersicht über mobile Geräte und SharePoint 2013](http://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) (http://technet.microsoft.com/library/fp161351(v=office.15).aspx).  
  
-   [In SharePoint 2013 unterstützte Browser für mobile Geräte](http://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (http://technet.microsoft.com/library/fp161353(v=office.15).aspx).  
  
-   [Anzeigen von Berichten und Scorecards auf Apple iPads (SharePoint Server 2010)](http://technet.microsoft.com/library/hh697482.aspx) (http://technet.microsoft.com/library/hh697482.aspx).  
  
-   [Anzeigen von Reporting Services-Berichten auf einem iPad (Video)](http://technet.microsoft.com/sqlserver/jj873792.aspx) (http://technet.microsoft.com/sqlserver/jj873792.aspx).  
  
-   [Anzeigen von Reporting Services-Berichten auf einem Microsoft Surface RT-Gerät (video)](http://technet.microsoft.com/sqlserver/dn146017)  
  
  
