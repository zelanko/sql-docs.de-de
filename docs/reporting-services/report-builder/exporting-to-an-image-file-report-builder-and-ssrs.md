---
title: Exportieren in eine Bilddatei (Berichts-Generator) | Microsoft-Dokumentation
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: 020d8ea2-de07-4212-a2bb-2ed0df2c8db8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2393769b4d6ca1676833b4e208e7f09dfcd444df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "77081378"
---
# <a name="exporting-to-an-image-file-report-builder-and-ssrs"></a>Exportieren in eine Bilddatei (Berichts-Generator und SSRS)
  Die Bildrenderingerweiterung rendert einen paginierten Bericht als Bitmap- oder Metadatei. Standardmäßig erstellt die Bildrenderingerweiterung eine TIFF-Datei des Berichts, die auf mehreren Seiten angezeigt werden kann. Nachdem der Client das Bild erhalten hat, kann es in einem Image Viewer angezeigt und gedruckt werden. Dieses Thema enthält für das Bildrendering spezifische Informationen und beschreibt Ausnahmen zu den Renderingregeln.  
  
 Die Bildrenderingerweiterung kann Dateien in allen von [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)] unterstützten Formaten erstellen: BMP, EMF, EMFPlus, GIF, JPEG, PNG und TIFF. Für TIFF lautet der Dateiname des primären Datenstromes *ReportName*.tif. Für alle anderen Formate, die als Einzelseite pro Datei gerendert werden, lautet der Dateiname *ReportName_Page.ext* . Dabei ist*ext* die Dateierweiterung für das ausgewählte Format. Geben Sie eine der oben aufgeführten Zeichenfolgen in der **OutputFormatDeviceInfo** -Einstellung an, um eine Datei in einem anderen bildunterstützten Format zu erstellen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="SupportedImageFormats"></a> Unterstützte Bildformate  
 In der folgenden Tabelle werden die Dateierweiterung und der MIME-Typ für jedes Bildrendererformat angezeigt.  
  
|**Typ**|**Erweiterung**|**MIMEType**|  
|--------------|-------------------|------------------|  
|BMP|BMP|image/bmp|  
|GIF|GIF|image/gif|  
|JPEG|JPEG|image/jpeg|  
|PNG|png|image/png|  
|TIFF|tif|image/tiff|  
|EMF|EMF|image/emf|  
|EMFPlus|EMF|image/emf|  
  
  
##  <a name="RenderingMultiplePages"></a> Rendern von mehreren Seiten  
 TIFF ist das einzige Format, das mehrseitige Dokumente in einer einzelnen Datei unterstützt. Andere Formate, wie JPG oder PNG, geben jeweils nur eine Seite aus und erfordern für jede Seite einen separaten Aufruf der Renderingerweiterung.  
  
  
##  <a name="Interactivity"></a> Interaktivität  
 Interaktivität wird von keinem der durch diesen Renderer generierten Bildformate unterstützt. Die folgenden interaktiven Elemente werden nicht gerendert:  
  
-   Links  
  
-   Anzeigen oder ausblenden  
  
-   Dokumentstruktur  
  
-   Drillthrough oder Links mit Durchklicken  
  
-   Endbenutzersortierung  
  
-   Feste Berichtsköpfe  
  
-   Lesezeichen  
  
  
##  <a name="DeviceInfo"></a> Geräteinformationseinstellungen  
 Sie können einige Standardeinstellungen für diesen Renderer ändern, indem Sie die Geräteinformationseinstellungen ändern. Weitere Informationen finden Sie unter [Image Device Information Settings](../../reporting-services/image-device-information-settings.md).  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Renderingverhalten (Berichts-Generator und SSRS)](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-builder/interactive-functionality-different-report-rendering-extensions.md)   
 [Rendern von Berichtselementen (Berichts-Generator und SSRS)](../../reporting-services/report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
