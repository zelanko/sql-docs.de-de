---
title: Exportieren in eine Bilddatei (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 020d8ea2-de07-4212-a2bb-2ed0df2c8db8
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 1d4ea909ce3682498755ab45fd3336e2586e539b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299790"
---
# <a name="exporting-to-an-image-file-report-builder-and-ssrs"></a>Exportieren in eine Bilddatei (Berichts-Generator und SSRS)
  Die Bildrenderingerweiterung rendert einen Bericht als Bitmap oder Metadatei. Standardmäßig erstellt die Bildrenderingerweiterung eine TIFF-Datei des Berichts, die auf mehreren Seiten angezeigt werden kann. Nachdem der Client das Bild erhalten hat, kann es in einem Image Viewer angezeigt und gedruckt werden. Dieses Thema enthält für das Bildrendering spezifische Informationen und beschreibt Ausnahmen zu den Renderingregeln.  
  
 Die Bildrenderingerweiterung kann Dateien in allen von [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]unterstützten Formaten generieren: BMP, EMF, EMFPlus, GIF, JPEG, PNG und TIFF. Für TIFF lautet der Dateiname des primären Datenstromes *ReportName*.tif. Für alle anderen Formate, die als Einzelseite pro Datei gerendert werden, lautet der Dateiname *ReportName_Page.ext* . Dabei ist*ext* die Dateierweiterung für das ausgewählte Format. Geben Sie eine der oben aufgeführten Zeichenfolgen in der **OutputFormatDeviceInfo** -Einstellung an, um eine Datei in einem anderen bildunterstützten Format zu erstellen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="SupportedImageFormats"></a> Unterstützte Bildformate  
 In der folgenden Tabelle werden die Dateierweiterung und der MIME-Typ für jedes Bildrendererformat angezeigt.  
  
|**Typ**|**Erweiterung**|**MIMEType**|  
|--------------|-------------------|------------------|  
|BMP|BMP|image/bmp|  
|GIF|GIF|image/gif|  
|JPEG|jpeg|image/jpeg|  
|PNG|png|image/png|  
|TIFF|tif|image/tiff|  
|EMF|EMF|image/emf|  
|EMFPlus|EMF|image/emf|  
  
  
##  <a name="RenderingMultiplePages"></a> Rendern von mehreren Seiten  
 TIFF ist das einzige Format, das mehrseitige Dokumente in einer einzelnen Datei unterstützt. Andere Formate, wie JPG oder PNG, geben jeweils nur eine Seite aus und erfordern für jede Seite einen separaten Aufruf der Renderingerweiterung.  
  
  
##  <a name="Interactivity"></a> Interaktivität  
 Interaktivität wird von keinem der durch diesen Renderer generierten Bildformate unterstützt. Die folgenden interaktiven Elemente werden nicht gerendert:  
  
-   Hyperlinks  
  
-   Anzeigen oder ausblenden  
  
-   Dokumentstruktur  
  
-   Drillthrough oder Links mit Durchklicken  
  
-   Endbenutzersortierung  
  
-   Feste Berichtsköpfe  
  
-   Lesezeichen  
  
  
##  <a name="DeviceInfo"></a> Geräteinformationseinstellungen  
 Sie können einige Standardeinstellungen für diesen Renderer ändern, indem Sie die Geräteinformationseinstellungen ändern. Weitere Informationen finden Sie unter [Image Device Information Settings](../image-device-information-settings.md).  
  
  
## <a name="see-also"></a>Siehe auch  
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Renderingverhalten (Berichts-Generator und SSRS)](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen &#40;Berichts-Generator und SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md)   
 [Rendern von Berichtselementen (Berichts-Generator und SSRS)](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
