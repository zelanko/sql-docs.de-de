---
title: Berichts-Viewer-Webpart auf einer SharePoint-Website | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: b6341a73-172f-4632-a9e9-cc79fed3f36b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 84afc267fe7b61ee850395750128a5cad15f716f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063470"
---
# <a name="report-viewer-web-part-on-a-sharepoint-site"></a>Berichts-Viewer-Webpart auf einer SharePoint-Website
  Das Berichts-Viewer-Webpart ist ein benutzerdefiniertes Webpart, das vom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte installiert wird. Mit diesem Webpart können Sie Berichte auf einem Berichtsserver, der für die Ausführung im integrierten SharePoint-Modus konfiguriert ist, anzeigen, drucken, exportieren und in diesen navigieren. Das Berichts-Viewer-Webpart ist Berichtsdefinitionsdateien (RDL), die von verarbeitet werden zugeordnet eine [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Berichtsserver. Für andere Berichtsdokumente, die Sie mit anderen Softwareprodukten erstellen, kann es nicht verwendet werden.  
  
 Zum Installieren des Webparts müssen Sie das Setup für das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Add-In ausführen. Sie sollten das Webpart nicht unabhängig installieren oder deinstallieren. Es bildet einen Teil des Add-Ins und kann nur über das Add-In-Setuppaket installiert werden. Der Berichts-Viewer-Webpart-Dateiname ist ReportViewer.dwp. Die Datei befindet sich im Ordner Programme\Common Files\Microsoft Shared\web server extensions\12\template\features\reportserver und darf nicht in andere Ordner verschoben werden.  
  
 Um das Webpart verwenden zu können, müssen Sie das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Add-In installiert und konfiguriert und den Berichtsserver für die SharePoint-Integration konfiguriert haben. Ferner werden Berichte benötigt, die im Viewer angezeigt werden können. Sie können nur Berichte öffnen, die sich in einer Bibliothek, einem Bibliotheksordner oder einem Berichtsverlauf befinden oder einen Link von Bibliothekswebpart zu einem Berichts-Viewer-Webpart verwenden. Sie können keine Berichte öffnen, die als Anlage zu einem Element einer benutzerdefinierten Liste gespeichert wurden.  
  
 Sie können Eigenschaften für das Berichts-Viewer-Webpart festlegen, um die Darstellung der Symbolleiste und des Ansichtsbereichs zu steuern und um das Webpart mit einem bestimmten Bericht zu verknüpfen. Im Berichts-Viewer wird entweder ein Bericht angezeigt, den Sie explizit damit verknüpft haben, oder eine beliebige geöffnete RDL-Datei.  
  
 Sie können nicht mehrere Berichte mit einer einzelnen Berichts-Viewer-Instanz verknüpfen, wenn Sie jedoch Berichte gruppieren möchten, können Sie ein Dashboard oder eine Webpartseite erstellen, in der mehrere Instanzen des Berichts-Viewer-Webparts auf einer einzelnen Seite eingebettet sind.  
  
 Das Webpart umfasst einen Ansichtsbereich, eine Symbolleiste, einen reduzierbaren Bereich zum Festlegen von Anmeldeinformationen und Parametern sowie Eigenschaften. Die folgende Grafik veranschaulicht das Webpart mit dem Company Sales-Beispielbericht und den Exportoptionen, die Sie auf der Symbolleiste aktivieren können.  
  
 ![Berichts-Viewer-Webpart](media/rs-sharepointrvwebpart.gif "Berichts-Viewer-Webpart")  
  
## <a name="web-part-components"></a>Webpartkomponenten  
 Im Ansichtsbereich wird ein Bericht als HTML angezeigt. Abhängig von der Konfiguration des Webparts kann der Ansichtsbereich maximiert werden, sodass der Bericht im Ganzseitenmodus angezeigt wird, oder der verfügbare Platz mit angrenzenden Bereichen und der Symbolleiste geteilt werden.  
  
 Die Symbolleiste stellt Funktionen für die Seitennavigation, Suche, Zoom und Export bereit, sodass Sie einen Bericht in einem anderen Anwendungsformat anzeigen können. Darüber hinaus wird optional eine Druckfunktionalität bereitgestellt, die eine paginierte Druckausgabe für HTML-Berichte sowie die Möglichkeit zum Ändern des Seitenlayouts und der Randeinstellungen bietet. **Mit dem Berichts-Generator öffnen, Abonnieren**, **Exportieren**und **Drucken** werden im Menü **Aktionen** auf der Symbolleiste bereitgestellt. Die Steuerelemente für Seitennavigation und Zoom befinden sich direkt auf der Symbolleiste.  
  
> [!NOTE]  
>  Die Symbolleiste kann nur angepasst werden, wenn Sie eigens Code für diesen Zweck schreiben, Sie können jedoch Eigenschaften festlegen, um alle oder einige Steuerelemente auszublenden.  
  
### <a name="export-action-on-the-report-toolbar"></a>Aktion Exportieren auf der Berichtssymbolleiste  
 Mit dem Befehl**Exportieren** im Menü **Aktionen** werden Anwendungsformate angezeigt, die den auf einem Berichtsserver bereitgestellten Renderingerweiterungen zugeordnet sind. Um die Verfügbarkeit eines bestimmten Formats zu bestimmen, können Sie eine Renderingerweiterung auf dem Berichtsserver hinzufügen oder entfernen oder Konfigurationseinstellungen ändern, um ein bestimmtes Exportformat aus der Liste zu entfernen. Sie können auch Konfigurationseinstellungen auf dem Berichtsserver angeben, um die verfügbaren Formate zu steuern. Sie können das Standardverhalten eines bestimmten Formats ändern, indem Sie Konfigurationseinstellungen für diese Renderingerweiterung hinzufügen und ändern.  
  
### <a name="print-action-on-the-report-toolbar"></a>Aktion Drucken auf der Berichtssymbolleiste  
 **Drucken** auf die **Aktionen** Menü ist, benutzerdefinierte Druckfunktionalität bereitgestellt, die über die bereitgestellten [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Wenn Sie auf **Drucken**klicken, wird ein clientseitiges ActiveX-Drucksteuerelement auf den Clientcomputer heruntergeladen. In den meisten Fällen muss der Benutzer, der auf **Drucken** klickt, über Administratorberechtigungen auf dem lokalen Computer verfügen. Üblicherweise ist der Download von ActiveX-Steuerelementen auf Benutzer mit Administratorberechtigungen beschränkt. Sie können die zentrale SharePoint-Verwaltung verwenden, um den Download der clientseitigen Drucksteuerung zu aktivieren oder zu deaktivieren.  
  
### <a name="find-action-on-the-report-toolbar"></a>Aktion Suchen auf der Berichtssymbolleiste  
 Der Befehl**Suchen** im Menü **Aktionen** bietet eine Möglichkeit, zu einer Zielposition im Bericht zu navigieren. Sie können nach Inhalten in einem Bericht suchen, indem Sie ein zu suchendes Wort oder eine zu suchende Wortgruppe eingeben. Der maximale Wert für einen Suchbegriff beträgt 256 Zeichen. Wenn die Suche zu einem übereinstimmenden Wert im Bericht führt, wird der Fokus auf den Teil des Berichts verschoben, der diesen Wert enthält.  
  
 Wenn Sie einen Wert für die Suche eingeben, geben Sie den Wert so ein, wie er vermutlich im Bericht angezeigt wird. Stellen Sie keine Frage (z. B. "wie hoch ist der durchschnittliche Gewinn für diesen Monat"), es sei denn, Sie gehen davon aus, dass jedes Wort des Satzes im Bericht vorkommt.  
  
 Sie können jeweils nur nach einem Begriff oder Wert suchen. Suchoperatoren (z. B. `AND` oder `OR`) oder Symbole und Platzhalter können nicht verwendet werden. Sie können eine Suche nicht für einen Querschnitt der Daten ausführen (beispielsweise die Suche nach Umsatzerlösen für einen bestimmten Monat für ein bestimmtes Produkt). Verwenden Sie für derartige Analysen den Berichts-Generator zum Erstellen von Berichten mit Durchklicken.  
  
 Für Suchvorgänge gelten Datenbank- und Modellsicherheitseinstellungen, mit denen der Zugriff auf Berichtsdaten eingeschränkt wird. Wenn Sie in einem Bericht mit Durchklicken nach einem Wert suchen, für den ein Modell als Datenquelle verwendet wird, und wenn Sie auf einen Teil des Modells keinen Zugriff haben, werden die Daten, die von diesem Teil des Modells dargestellt werden, von der Suche ausgeschlossen.  
  
### <a name="panes-for-specifying-credentials-and-parameters"></a>Bereiche für die Angabe von Anmeldeinformationen und Parametern  
 Die Bereiche**Anmeldeinformationen** und **Parameter** werden neben dem Ansichtsbereich angezeigt. **Anmeldeinformationen** wird angezeigt, wenn die Datenquellenverbindung für den Bericht so konfiguriert ist, dass vom Benutzer ein Konto und ein Kennwort mit den Berechtigungen zum Zugriff auf die Datenquelle angefordert werden. **Parameter** wird angezeigt, wenn der Bericht Benutzereingaben für im Bericht definierte Parameter annimmt.  
  
### <a name="setting-properties-on-the-report-viewer-web-part"></a>Festlegen benutzerdefinierter Eigenschaften für das Berichts-Viewer-Webpart  
 Zu den Eigenschaften des Webparts zählen benutzerdefinierte Eigenschaften, die nur für den Berichts-Viewer verwendet werden können, sowie allgemeine Eigenschaften, die Sie für jedes Webpart festlegen können. Weitere Informationen finden Sie unter [Anpassen des Berichts-Viewer-Webparts](../../2014/reporting-services/customize-the-report-viewer-web-part.md).  
  
 Berichte werden standardmäßig im Ganzseitenmodus geöffnet. Im Ganzseitenmodus wird die Symbolleiste angezeigt, von der die Seitennavigation, die Suche und weitere Funktionalität bereitgestellt werden. Sie können das Webpart bezüglich der Darstellung oder des standardmäßigen Verhaltens anpassen.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Hinzufügen des Berichts-Viewer-Webparts zu einer Webseite &#40;integrierten Reporting Services im SharePoint-Modus&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
  
