---
title: Exportieren von Berichten (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10437"
ms.assetid: a2bab8c1-505d-4da3-b1db-ea0ae13b2336
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d8b4fe6e791f84f0949b0657b890c79db99dfbf9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107947"
---
# <a name="exporting-reports-report-builder-and-ssrs"></a>Exportieren von Berichten (Berichts-Generator und SSRS)
  Nachdem Sie einen Bericht ausgeführt haben, können Sie ihn in ein anderes Format exportieren, z.B. Excel oder PDF. Sie können den Bericht auch durch Generieren eines Atom-Dienstdokuments exportieren. Dabei werden die im Bericht verfügbaren Atom-konformen Datenfeeds aufgelistet.  
  
 Exportieren Sie einen Bericht, um folgende Aufgaben auszuführen:  
  
-   Verwenden der Berichtsdaten in einer anderen Anwendung. Sie können den Bericht z. B. nach Excel exportieren und anschließend in Excel mit den Daten arbeiten.  
  
-   Drucken des Berichts in einem anderen Format. Sie können den Bericht z. B. in das PDF-Dateiformat exportieren und anschließend ausdrucken.  
  
-   Speichern einer Kopie des Berichts in einem anderen Dateiformat. Sie können einen Bericht z. B. nach Word exportieren und speichern, um eine Kopie des Berichts zu erstellen.  
  
-   Verwenden von Berichtsdaten als Datenfeeds in Anwendungen. Beispielsweise können Sie Atom-kompatible Datenfeeds generieren, die vom [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Client verwendet werden können, und dann in [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]mit den Daten arbeiten.  
  
 Die Exportoption ist auf der Berichts-Viewer-Symbolleiste im Berichts-Manager verfügbar, die beim Anzeigen eines Bericht auf dem Berichtsserver am oberen Rand jedes Berichts angezeigt wird, und auf dem Menüband im Berichts-Generator, wenn Sie einen Bericht in der Vorschau anzeigen. Die Datenfeedoption ist nur im Berichts-Manager verfügbar.  
  
 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet viele Renderingerweiterungen und unterstützt den Export von Berichten in gebräuchliche Dateiformate. Die Renderingerweiterungen unterstützen Dateiformate mit bedingten Umbrüchen (z. B. Word oder Excel), festen Seitenumbrüche (z. B. PDF oder TIFF) oder nur Daten (z. B. CSV oder Atom-kompatibles XML).  
  
 Informationen zu den ersten Schritten beim Exportieren von Berichten und Generieren von Atom-kompatiblen Datenfeeds aus Berichten finden Sie unter [Exportieren eines Berichts als anderer Dateityp &#40;Berichts-Generator und SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md) und [Generieren von Datenfeeds aus einem Bericht &#40;Berichts-Generator und SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="RendererTypes"></a>Renderingerweiterung  
 Drei Arten von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Renderingerweiterungen sind verfügbar:  
  
-   **Erweiterungen für Datenrenderer** Datenrenderingerweiterungen entfernen alle Formatierungs-und Layoutinformationen aus dem Bericht und zeigen nur die Daten an. Die mithilfe dieser Option erstellte Datei kann zum Importieren der Rohberichtsdaten in einen anderen Dateityp verwendet werden, z. B. Excel, eine andere Datenbank, eine XML-Datennachricht oder eine benutzerdefinierte Anwendung. Datenrenderer unterstützen keine Seitenumbrüche.  
  
     Die folgenden Datenrenderingerweiterungen werden unterstützt: CSV, XML und Atom.  
  
-   **Renderererweiterungen mit weichem Seitenumbruch** Renderingerweiterungen mit weichem Seitenumbruch behalten das Berichtslayout und die Formatierung bei. Die mithilfe dieser Option erstellte Datei wird für die Bildschirmanzeige und -bereitstellung optimiert, z.B. auf einer Webseite oder in den **ReportViewer** -Steuerelementen.  
  
     Die folgenden Renderingerweiterungen mit bedingtem Seitenumbruch werden unterstützt: [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word und Webarchiv (MHTML).  
  
-   **Renderingerweiterungen mit hartem Seitenumbruch** Renderererweiterungen mit hartem Seitenumbruch behalten das Berichtslayout und die Formatierung bei. Die mithilfe dieser Option erstellte Datei wird für einen konsistenten Druck oder für die Onlineanzeige in einem Buchformat optimiert.  
  
     Die folgenden Renderingerweiterungen mit festem Seitenumbruch werden unterstützt: TIFF und PDF  
  
##  <a name="ExportFormats"></a>Export Formate  
 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt Renderingerweiterungen bereit, die Berichte in anderen Formaten rendern. Wenn Sie diese Funktion verwenden möchten, sollten Sie den Berichtsentwurf für das gewählte Dateiformat optimieren. In den Themen zu den einzelnen Renderingerweiterungen finden Sie ausführliche Informationen dazu, wie der Bericht in diesem Format gerendert wird.  
  
 Die folgende Tabelle enthält die verfügbaren Formate.  
  
|Format|Renderingerweiterungstyp|BESCHREIBUNG|  
|------------|------------------------------|-----------------|  
|CSV|Data|Die durch Trennzeichen getrennte CSV (Comma-Separated Value)-Renderingerweiterung rendert Berichte als vereinfachte Darstellung der Daten eines Berichts in einem standardisierten Nur-Text-Format, das leicht lesbar und mit anderen Anwendungen austauschbar ist.<br /><br /> Weitere Informationen finden Sie unter [Exportieren als CSV-Datei &#40;Berichts-Generator und SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md)mit den Daten arbeiten.|  
|Excel|Bedingter Seitenumbruch|Die Excel-Renderingerweiterung rendert einen Bericht als Excel-Dokument, das mit [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007-2010 und [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2003 kompatibel ist, wenn das Microsoft Office Compatibility Pack für Word, Excel und PowerPoint installiert ist. Der Bericht wird in ein Excel-Arbeitsblatt exportiert, wobei einige Layout-und ursprüngliche Entwurfs Elemente entfernt werden. Eigenschaften des Berichts und der Gruppen im Bericht können festgelegt werden, um die Benennung von Arbeitsblatt Registerkarten beim Exportieren nach Excel zu aktivieren. Die Erweiterung des Dateinamens bei Dateien, die von diesem Renderer generiert werden, lautet XLSX.<br /><br /> Weitere Informationen finden Sie unter [Exportieren nach Microsoft Excel &#40;Berichts-Generator und SSRS&#41;](exporting-to-microsoft-excel-report-builder-and-ssrs.md) (Exportieren nach Microsoft Excel (Berichts-Generator und SSRS)).<br /><br /> Hinweis: die Excel 2003-Renderingerweiterung, die in das [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] systemeigene Format von 2003 rendert, ist in einigen Berichts Szenarien verfügbar.|  
|Wort|Bedingter Seitenumbruch|Die Word-Renderingerweiterung rendert einen Bericht als Word-Dokument, das mit [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010 und [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2003 kompatibel ist, wenn das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Compatibility Pack für Word, Excel und PowerPoint installiert ist. Nachdem der Bericht in ein Word-Dokument exportiert wurde, können Sie den Inhalt bearbeiten und dokumentartige Berichte wie Adressetiketten, Bestellungen oder Serienbriefe entwerfen. Die Dateinamenerweiterung der von diesem Renderer generierten Dateien lautet DOCX.<br /><br /> Weitere Informationen finden Sie unter [Exportieren nach Microsoft Word &#40;Berichts-Generator und SSRS&#41;](exporting-to-microsoft-word-report-builder-and-ssrs.md)mit den Daten arbeiten.<br /><br /> Hinweis: die Word 2003-Renderingerweiterung, die in das [!INCLUDE[ofprword](../../includes/ofprword-md.md)] systemeigene Format von 2003 rendert, ist in einigen Berichts Szenarien verfügbar.|  
|Webarchiv|Bedingter Seitenumbruch|Die HTML-Renderingerweiterung rendert einen Bericht im HTML-Format. Die Renderingerweiterung kann außerdem vollständige HTML-Seiten oder HTML-Fragmente zum Einbetten in andere HTML-Seiten erstellen. HTML wird stets mit UTF-8-Codierung erstellt.<br /><br /> Die HTML-Renderingerweiterung ist die Standardrenderingerweiterung für Berichte, die im Berichts-Generator in der Vorschau angezeigt und in einem Browser angezeigt werden. Dies gilt auch bei der Ausführung im Berichts-Manager.<br /><br /> Weitere Informationen finden Sie unter [Rendern in das HTML-Format &#40;Berichts-Generator und SSRS&#41;](rendering-to-html-report-builder-and-ssrs.md)mit den Daten arbeiten.|  
|Acrobat-Datei (PDF-Datei)|Fester Seitenumbruch|Die PDF-Renderingerweiterung rendert Berichte in einem Dateiformat, das in Adobe Acrobat und anderen PDF-Viewern von Drittanbietern geöffnet werden kann, die das Format PDF 1.3 unterstützen. Obwohl PDF 1.3 mit Adobe Acrobat 4.0 oder höher kompatibel ist, wird Adobe Acrobat von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erst ab Version 6 unterstützt. Die Renderingerweiterung erfordert keine Adobe-Software, um Berichte zu rendern. Zum Anzeigen oder Drucken von Berichten im PDF-Format sind allerdings PDF-Viewer wie Adobe Acrobat erforderlich.<br /><br /> Weitere Informationen finden Sie unter [Exportieren als PDF-Datei &#40;Berichts-Generator und SSRS&#41;](exporting-to-a-pdf-file-report-builder-and-ssrs.md)mit den Daten arbeiten.|  
|TIFF-Datei|Fester Seitenumbruch|Die Bildrenderingerweiterung rendert einen Bericht als Bitmap oder Metadatei. Standardmäßig erstellt die Bildrenderingerweiterung eine TIFF-Datei des Berichts, die auf mehreren Seiten angezeigt werden kann. Nachdem der Client das Bild erhalten hat, kann es in einem Image Viewer angezeigt und gedruckt werden.<br /><br /> Die Bildrenderingerweiterung kann Dateien in allen von [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]unterstützten Formaten generieren: BMP, EMF, EMFPlus, GIF, JPEG, PNG und TIFF.<br /><br /> Weitere Informationen finden Sie unter [Exportieren in eine Bilddatei &#40;Berichts-Generator und SSRS&#41;](exporting-to-an-image-file-report-builder-and-ssrs.md)mit den Daten arbeiten.|  
|XML|Data|Die XML-Renderingerweiterung gibt einen Bericht im XML-Format zurück. Das Schema der Bericht-XML-Ausgabe hängt vom jeweiligen Bericht ab und enthält nur Daten. Layoutinformationen werden von der XML-Renderingerweiterung nicht gerendert, und die Paginierung wird nicht beibehalten. Der von dieser Erweiterung generierte XML-Code kann in eine Datenbank importiert, als XML-Datennachricht verwendet oder an eine benutzerdefinierte Anwendung gesendet werden.<br /><br /> Weitere Informationen finden Sie unter [Exportieren nach XML &#40;Berichts-Generator und SSRS&#41;](exporting-to-xml-report-builder-and-ssrs.md)mit den Daten arbeiten.|  
|Atom|Data|Die Atom-Renderingerweiterung generiert Atom-kompatible Datenfeeds aus Berichten. Die Datenfeeds sind mit Anwendungen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , die Atom-kompatible Datenfeeds nutzen können, lesbar und austauschbar.<br /><br /> Die Ausgabe ist ein Atom-Dienstdokument, in dem die in einem Bericht verfügbaren Datenfeeds aufgeführt sind. Mindestens ein Datenfeed wird für jeden Datenbereich in einem Bericht erstellt. Abhängig vom Typ des Datenbereichs und den darin angezeigten Daten können mehrere Datenfeeds generiert werden.<br /><br /> Weitere Informationen finden Sie unter [Erstellen von Daten Feeds aus Berichten &#40;Berichts-Generator und SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md).|  
  
##  <a name="ExportingReport"></a>Exportieren eines Berichts  
 Führen Sie den Bericht zum Exportieren im Berichts-Manager oder Berichts-Generator aus, und wählen Sie anschließend in der Dropdownliste "Exportieren" ein Format aus. In einer Eingabeaufforderung werden Sie gefragt, ob die Datei gespeichert oder geöffnet werden soll. Wenn Sie **Öffnen**auswählen, wird der Bericht in der Anwendung geöffnet, die dem ausgewählten Renderingformat zugeordnet ist. (Bei Auswahl von **Excel** wird der Bericht beispielsweise in Excel geöffnet). Wenn Sie **Speichern**auswählten, wird der Bericht gespeichert. Wenn Sie z. B. nach Excel exportieren, wird der Bericht als XLS-Datei gespeichert. Welche Anwendung für ein bestimmtes Renderingformat verwendet wird, hängt von den für den lokalen Computer definierten Dateizuordnungen ab. Weitere Informationen finden Sie unter [Exportieren eines Berichts als anderer Dateityp &#40;Berichts-Generator und SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md).  
  
 Der Bericht wird vom Berichtsserver so exportiert, wie er in der aktuellen Benutzersitzung vorliegt. Wenn eine aktualisierte Version des Berichts veröffentlicht wird, während Sie den Bericht geöffnet haben, oder sich die im Bericht angezeigten Daten ändern, wird der exportierte Bericht nicht aktualisiert.  
  
 Unter Umständen bestehen Auswirkungen auf die Berichtspaginierung, wenn Sie einen Bericht in ein anderes Format exportieren. In der Vorschau wird ein Bericht so angezeigt, wie er von der HTML-Renderingerweiterung gerendert wird, in der Regeln für bedingte Seitenumbrüche angewendet werden. Wenn Sie einen Bericht in ein anderes Dateiformat exportieren (z. B. Adobe Acrobat, PDF), basiert die Paginierung auf der physischen Seitengröße und folgt Regeln für feste Seitenumbrüche. Die Seiten können auch durch logische Seitenumbrüche getrennt werden, die Sie zu einem Bericht hinzufügen. Die tatsächliche Länge einer Seite variiert jedoch je nach dem verwendeten Renderertyp. Sie sollten mit dem Paginierungsverhalten der ausgewählten Renderingerweiterung vertraut sein, wenn Sie die Paginierung Ihres Berichts ändern möchten. Möglicherweise müssen Sie den Entwurf des Berichtslayouts für diese Renderingerweiterung anpassen. Weitere Informationen finden Sie unter [Seiten Layout und Rendering &#40;Berichts-Generator und SSRS&#41;](../report-design/page-layout-and-rendering-report-builder-and-ssrs.md).  
  
##  <a name="GeneratingDataFeedsFromReport"></a>Erstellen von Daten Feeds aus einem Bericht  
 Führen Sie den Bericht im Berichts-Manager aus, und klicken Sie dann auf der Symbolleiste des Berichts-Managers auf das Symbol **Datenfeed generieren** , um Datenfeeds aus einem Bericht zu generieren. In einer Eingabeaufforderung werden Sie gefragt, ob die Datei gespeichert oder geöffnet werden soll. Wenn Sie **Öffnen**auswählen, wird das Atom-Dienstdokument in der Anwendung geöffnet, die der Dateierweiterung ".atomsvc" zugeordnet ist. Wenn Sie **Speichern**auswählen, wird das Dokument als ATOMSVC-Datei gespeichert. Standardmäßig wird der Name des Berichts als Dateiname verwendet. Sie können den Namen ändern, um einen sinnvolleren Namen anzugeben.  
  
 Das Atom-Dienstdokument wird auf dem Computer gespeichert. Sie können es später auf einen Berichtsserver oder einen anderen Server hochladen, um es für andere Benutzer verfügbar zu machen. Weitere Informationen finden Sie unter [Generieren von Datenfeeds aus Berichten &#40;Berichts-Generator und SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md) und [Generieren von Datenfeeds aus einem Bericht &#40;Berichts-Generator und SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md).  
  
##  <a name="Troubleshooting"></a>Problembehandlung bei exportierten  
 Gelegentlich sehen die Berichte anders aus, oder sie funktionieren nach dem Exportieren in ein anderes Format nicht wunschgemäß. Dies liegt daran, dass für den Renderer möglicherweise bestimmte Regeln und Einschränkungen gelten. Sie können vielen Einschränkungen dadurch begegnen, dass Sie sie beim Erstellen des Berichts berücksichtigen. Sie müssen im Bericht ggf. ein etwas anderes Layout verwenden, die Elemente im Bericht sorgfältig ausrichten, die Fußzeilen im Bericht auf eine Textzeile beschränken usw.  
  
 Falls Ihr Bericht Unicode-Text mit arabischen Zahlen oder arabische Daten enthält, werden die Daten und Zahlen nicht korrekt gerendert, wenn Sie den Bericht in eines der folgenden Formate exportieren oder ausdrucken.  
  
-   PDF  
  
-   Wort  
  
-   Excel  
  
-   Image/TIFF  
  
 Wenn Sie den Bericht als HTML exportieren, werden die Daten und Zahlen korrekt gerendert.  
  
 In den Themen zu bestimmten Renderern werden neben dem Rendern von Berichtselementen und Datenbereichen auch die Einschränkungen und Lösungen für jeden Renderer beschrieben.  
  
-   [Exportieren in eine CSV-Datei &#40;Berichts-Generator und SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md)  
  
-   [Exportieren nach Microsoft Excel &#40;Berichts-Generator und SSRS&#41;](exporting-to-microsoft-excel-report-builder-and-ssrs.md)  
  
-   [Exportieren nach Microsoft Word &#40;Berichts-Generator und SSRS&#41;](exporting-to-microsoft-word-report-builder-and-ssrs.md)  
  
-   [Rendern in HTML (Berichts-Generator und SSRS)](rendering-to-html-report-builder-and-ssrs.md)  
  
-   [Exportieren in eine PDF-Datei &#40;Berichts-Generator und SSRS&#41;](exporting-to-a-pdf-file-report-builder-and-ssrs.md)  
  
-   [Exportieren in eine Bilddatei &#40;Berichts-Generator und SSRS&#41;](exporting-to-an-image-file-report-builder-and-ssrs.md)  
  
-   [Exportieren nach XML-&#40;Berichts-Generator und SSRS&#41;](exporting-to-xml-report-builder-and-ssrs.md)  
  
-   [Erstellen von Daten Feeds aus Berichten &#40;Berichts-Generator und SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md)  
  
 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet zusätzliche Funktionen, mit denen Berichte erstellt werden können, die in anderen Formaten problemlos funktionieren. Durch Seitenumbrüche in Tablix-Datenbereichen (Tabelle, Matrix und Liste), Gruppen und Rechtecke lässt sich die Berichtspaginierung besser steuern. Durch Seitenumbrüche begrenzte Berichtsseiten können über unterschiedliche Seitennamen verfügen und die Seitennummerierung zurücksetzen. Mithilfe von Ausdrücken können die Seitennamen und Seitenzahlen bei Ausführung des Berichts dynamisch aktualisiert werden. Weitere Informationen finden Sie unter [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md).  
  
 Zudem können Sie mit dem integrierten globalen Objekt in RenderFormat bedingt unterschiedliche Berichtslayouts für verschiedene Renderer übernehmen. Weitere Informationen finden Sie unter [Integrierte globale Werte und Benutzerverweise &#40;Berichts-Generator und SSRS&#41;](../report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md).  
  
##  <a name="OtherWaysExportingReports"></a>Weitere Methoden zum Exportieren von Berichten  
 Beim Exportieren eines Berichts handelt es sich um eine bedarfsgesteuerte Aufgabe, die Sie für einen im Berichts-Manager oder Berichts-Generator geöffneten Bericht ausführen. Falls Sie einen Exportvorgang automatisieren möchten (z. B. um einen Bericht in einem wiederkehrenden Zeitplan als spezifischen Dateityp in einen freigegebenen Ordner zu exportieren), erstellen Sie ein Abonnement, durch das der Bericht an einen freigegebenen Ordner übermittelt wird. Weitere Informationen finden Sie unter [File Share Delivery in Reporting Services](../subscriptions/file-share-delivery-in-reporting-services.md).  
  
 Berichte, die mit den Berichtstools in der Vorschau angezeigt oder in einer Browseranwendung wie dem Berichts-Manager geöffnet werden, werden stets zuerst in HTML gerendert. Sie können keine andere Renderingerweiterung als Standarderweiterung für die Anzeige angeben. Sie können jedoch ein Abonnement erstellen, durch das ein Bericht im gewünschten Renderingformat für die nachfolgende Übermittlung an ein E-Mail-Postfach oder an einen freigegebenen Ordner erstellt wird. Weitere Informationen finden Sie unter [erstellen, ändern und Löschen von Standard Abonnements &#40;Reporting Services im einheitlichen Modus&#41;](../subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md) und [erstellen, ändern und Löschen eines datengesteuerten Abonnements](../subscriptions/data-driven-subscriptions.md).  
  
 Sie können auch über eine URL, in der eine Renderingerweiterung als URL-Parameter angegeben ist, auf einen Bericht zugreifen und ihn direkt im angegebenen Format rendern, ohne ihn zuerst in HTML zu rendern. Im folgenden Beispiel wird ein Bericht im Excel-Format gerendert:  
  
```  
http://<Server Name>/reportserver?/Sales/YearlySalesSummary&rs:Format=Excel&rs:Command=Render  
```  
  
 Weitere Informationen finden Sie unter [Exportieren von Berichten über URL-Zugriff](../export-a-report-using-url-access.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Steuern von Seitenumbrüchen, Überschriften, Spalten und Zeilen &#40;Berichts-Generator und SSRS&#41;](../report-design/controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md)   
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS)](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Drucken von Berichten &#40;Berichts-Generator und SSRS&#41;](print-reports-report-builder-and-ssrs.md)   
 [Speichern von Berichten &#40;Berichts-Generator&#41;](saving-reports-report-builder.md)  
  
  
