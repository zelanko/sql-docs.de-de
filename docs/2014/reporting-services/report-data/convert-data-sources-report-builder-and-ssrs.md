---
title: Konvertieren einer Datenquelle aus den eingebetteten in freigegebene Datenquelle (Berichts-Generator und SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data sources [Reporting Services], embedded
- data sources [Reporting Services], shared
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
caps.latest.revision: 15
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 6a56cf7b9f2e087f44166f2ded7cb55ebf95b01c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058445"
---
# <a name="convert-a-data-source-from-embedded-to-shared-report-builder-and-ssrs"></a>Konvertieren einer eingebetteten Datenquelle in eine freigegebene Datenquelle (Berichts-Generator und SSRS)
  Jede Datenquelle im Berichtsdatenbereich ist eingebettet und bezieht sich speziell auf den Bericht, oder sie ist freigegeben. In Berichts-Generator verweist eine freigegebene Datenquelle auf eine veröffentlichte freigegebene Datenquelle auf einem Berichtsserver oder einer SharePoint-Website. In Berichts-Designer verweist eine freigegebene Datenquellenreferenz auf eine freigegebene Datenquelle im Ordner **Freigegebene Datenquellen** in Projektmappen-Explorer.  
  
 Weitere Informationen zu den Unterschieden zwischen eingebetteten und freigegebenen Datenquellen finden Sie unter [Eingebettete und freigegebene Datenverbindungen oder Datenquellen (Berichts-Generator und SSRS)](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).  
  
 Weitere Informationen zum Erstellen einer freigegebenen Datenquelle finden Sie unter [Erstellen einer eingebetteten oder freigegebenen Datenquelle (SSRS)](../create-an-embedded-or-shared-data-source-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-designer"></a>Berichts-Designer  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a>So konvertieren Sie eine Datenquelle von "eingebettet" in "freigegeben"  
  
-   Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf die Datenquelle, und klicken Sie anschließend auf **In freigegebene Datenquelle konvertieren**.  
  
    > [!NOTE]  
    >  Zum Anzeigen des Berichtsdatenbereichs klicken Sie im Menü **Ansicht** auf **Berichtsdaten**. Wenn der Bereich als unverankertes Fenster geöffnet wird, können Sie es andocken. Weitere Informationen finden Sie unter [Andocken des Berichtsdatenbereichs im Berichts-Designer &#40;SSRS&#41;](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md).  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Berichtsdatenquellen](manage-report-data-sources.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  