---
title: Konvertieren von Datenquellen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
- data sources [Reporting Services], shared
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8ebc39fb525c85fad333637d37aeb235ea9d0a5c
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50027925"
---
# <a name="convert-data-sources-report-builder-and-ssrs"></a>Konvertieren von Datenquellen (Berichts-Generator und SSRS)
  Jede Datenquelle im Berichtsdatenbereich ist eingebettet und bezieht sich speziell auf den Bericht, oder sie ist freigegeben. In Berichts-Generator verweist eine freigegebene Datenquelle auf eine veröffentlichte freigegebene Datenquelle auf einem Berichtsserver oder einer SharePoint-Website. In Berichts-Designer verweist eine freigegebene Datenquellenreferenz auf eine freigegebene Datenquelle im Ordner **Freigegebene Datenquellen** in Projektmappen-Explorer.  
  
 Weitere Informationen zu den Unterschieden zwischen eingebetteten und freigegebenen Datenquellen finden Sie unter [Eingebettete und freigegebene Datenverbindungen oder Datenquellen (Berichts-Generator und SSRS)](https://msdn.microsoft.com/library/f417782c-b85a-4c4d-8a40-839176daba56).  
  
 Weitere Informationen zum Erstellen einer freigegebenen Datenquelle finden Sie unter [Erstellen einer eingebetteten oder freigegebenen Datenquelle (SSRS)](https://msdn.microsoft.com/library/b111a8d0-a60d-4c8b-b00a-51644b19c34b).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-designer"></a>Berichts-Designer  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a>So konvertieren Sie eine Datenquelle von "eingebettet" in "freigegeben"  
  
-   Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf die Datenquelle, und klicken Sie anschließend auf **In freigegebene Datenquelle konvertieren**.  
  
    > [!NOTE]  
    >  Zum Anzeigen des Berichtsdatenbereichs klicken Sie im Menü **Ansicht** auf **Berichtsdaten**. Wenn der Bereich als unverankertes Fenster geöffnet wird, können Sie es andocken. Weitere Informationen finden Sie unter [Andocken des Berichtsdatenbereichs im Berichts-Designer &#40;SSRS&#41;](../../reporting-services/tools/dock-the-report-data-pane-in-report-designer-ssrs.md).  
  
     Im Berichtsdatenbereich ändert sich das Datenquellensymbol in das Symbol für freigegebene Datenquellen. Im Projektmappen-Explorer wird eine freigegebene Datenquelle mit demselben Namen im Ordner **Freigegebene Datenquelle** angezeigt.  
  
### <a name="to-convert-a-data-source-from-shared-to-embedded"></a>So konvertieren Sie eine Datenquelle von "freigegeben" in "eingebettet"  
  
-   Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf die Datenquelle, öffnen Sie das Dialogfeld **Datenquelleneigenschaften** , und klicken Sie anschließend auf **Eingebettete Verbindung**. Geben Sie die erforderlichen Informationen ein.  
  
     Im Berichtsdatenbereich ändert sich das Datenquellensymbol in das Symbol für freigegebene Datenquellen.  
  
## <a name="report-builder"></a>Berichts-Generator  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a>So konvertieren Sie eine Datenquelle von "eingebettet" in "freigegeben"  
  
-   Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf die Datenquelle, öffnen Sie das Dialogfeld **Datenquelleneigenschaften** , und klicken Sie anschließend auf **Eingebettete Verbindung**. Geben Sie die erforderlichen Informationen ein.  
  
     Im Berichtsdatenbereich ändert sich das Datenquellensymbol in das Symbol für freigegebene Datenquellen.  
  
#### <a name="to-convert-a-data-source-from-shared-to-embedded"></a>So konvertieren Sie eine Datenquelle von "freigegeben" in "eingebettet"  
  
-   Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf die Datenquelle, öffnen Sie das Dialogfeld **Datenquelleneigenschaften** , und klicken Sie anschließend auf **Eingebettete Verbindung**. Geben Sie die erforderlichen Informationen ein.  
  
     Im Berichtsdatenbereich ändert sich das Datenquellensymbol in das Symbol für freigegebene Datenquellen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwalten von Berichtsdatenquellen](../../reporting-services/report-data/manage-report-data-sources.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
