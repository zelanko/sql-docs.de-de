---
title: Erstellen einer eingebettete oder freigegebene Datenquelle (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data sources [Reporting Services], creating
ms.assetid: b111a8d0-a60d-4c8b-b00a-51644b19c34b
caps.latest.revision: 40
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 28609edfbfc504d3949abb6a19f7f04098fde07b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050496"
---
# <a name="create-an-embedded-or-shared-data-source-ssrs"></a>Erstellen einer eingebettete oder freigegebenen Datenquelle (SSRS)
  Eine Berichtsdatenquelle gibt einen Namen und Verbindungsinformationen an. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt zwei Typen von Datenquellen: eingebettet und freigegeben. Eine eingebettete Datenquelle wird in einer Berichtsdefinition definiert und nur von diesem Bericht verwendet. Eine freigegebene Datenquelle wird als separates Element definiert und kann von mehreren Berichten verwendet werden. Weitere Informationen finden Sie unter [eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).  
  
 Wechseln Sie in Berichts-Generator zum Berichtsserver oder zu einer SharePoint-Website, und wählen Sie Datenquellen aus, oder erstellen Sie eingebettete Datenquellen. Freigegebene Datenquellen können in Berichts-Generator nicht erstellt werden.  
  
 In Berichts-Designer können Sie freigegebene oder eingebettete Datenquellen erstellen. Klicken Sie im Bereich "Berichtsdaten" beginnen, um einen Datenquellenverweis zu erstellen, und wählen Sie dann die **neu** Option. Nachdem Sie den Datenquellenverweis erstellt haben, wird dem Projektmappen-Explorer automatisch unter dem Ordner Freigegebene Datenquellen eine neue freigegebene Datenquelle hinzugefügt.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
 Sie können auch freigegebene Datenquellen auf einem Berichtsserver oder auf einer SharePoint-Website direkt erstellen. Weitere Informationen finden Sie unter [erstellen, löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41; ](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) oder [erstellen und verwalten freigegebene Datenquellen &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).  
  
### <a name="to-create-an-embedded-or-shared-data-source"></a>So erstellen Sie eine eingebettete bzw. eine freigegebene Datenquelle  
  
1.  Klicken Sie im Berichtsdatenbereich auf der Symbolleiste auf **Neu** , und klicken Sie dann auf **Datenquelle**. Das Dialogfeld **Datenquelleneigenschaften** wird angezeigt.  
  
    > [!NOTE]  
    >  Zum Anzeigen des Berichtsdatenbereichs klicken Sie im Menü **Ansicht** auf **Berichtsdaten** .  
  
2.  Geben Sie im Textfeld **Name** einen Namen für die Datenquelle ein, oder übernehmen Sie den Standardnamen. Der Name der Datenquelle wird intern für den Bericht verwendet. Zur Verdeutlichung sollte der Name der Datenquelle den Namen der Datenbank enthalten, die in der Verbindungszeichenfolge angegeben ist.  
  
3.  Überprüfen Sie für eine eingebettete Datenquelle **eingebettete Verbindung** ausgewählt ist.  
  
    1.  Wählen Sie in der Dropdownliste **Typ** einen Datenquellentyp aus, zum Beispiel **Microsoft SQL Server** oder **OLE DB**.  
  
    2.  Geben Sie eine Verbindungszeichenfolge an, indem Sie eine der folgenden Alternativen verwenden:  
  
    -   Geben Sie die Verbindungszeichenfolge direkt in das Textfeld **Verbindungszeichenfolge** ein. Eine Liste der Beispiele für Verbindungszeichenfolgen, finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) oder [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
    -   Klicken Sie auf die Ausdrucksschaltfläche (**fx)** , um einen Ausdruck zu erstellen, der als Verbindungszeichenfolge ausgewertet wird. Geben Sie den Ausdruck im Dialogfeld **Ausdruck** in den Bereich Ausdruck ein. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
    -   Klicken Sie auf **Bearbeiten** , um das Dialogfeld **Verbindungseigenschaften** für den Datenquellentyp zu öffnen, den Sie in Schritt 2 gewählt haben.  
  
         Füllen Sie die Felder im Dialogfeld **Verbindungseigenschaften** gemäß dem jeweiligen Datenquellentyp aus. Verbindungseigenschaften enthalten den Typ der Datenquelle, den Namen der Datenquelle und die zu verwendenden Anmeldeinformationen. Nachdem Sie in diesem Dialogfeld Werte angegeben haben, klicken Sie auf **Verbindung testen** , um zu überprüfen, ob die Datenquelle verfügbar ist und die angegebenen Anmeldeinformationen richtig sind. Weitere Informationen zu bestimmten Datenquellentypen finden Sie unter [Hinzufügen von Daten aus externen Datenquellen (SSRS)](report-data/add-data-from-external-data-sources-ssrs.md).  
  
4.  Überprüfen Sie für eine freigegebene Datenquelle **freigegebenen Datenquellenverweis verwenden** ausgewählt ist.  
  
    1.  Klicken Sie auf **Neu**. Führen Sie im Eigenschaftendialogfeld **Freigegebene Datenquelle** die Schritte 2 und 3 aus, um eine neue Datenquelle zu erstellen.  
  
    2.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
         Die neue freigegebene Datenquelle wird im Projektmappen-Explorer im Ordner Freigegebene Datenquellen angezeigt.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Die Datenquelle wird im Berichtsdatenbereich angezeigt. Im Berichtsdatenbereich verweist eine freigegebene Datenquelle auf die Datenquellendefinition. In Berichts-Generator befindet sich die Datenquellendefinition auf einem Berichtsserver oder einer SharePoint-Website. In Berichts-Designer ist die Datenquellendefinition eine Datei im Projektmappen-Explorer unter dem Ordner Freigegebene Datenquellen.  
  
### <a name="to-import-an-existing-data-source-in-report-designer"></a>So importieren Sie eine vorhandene Datenquelle in Berichts-Designer  
  
1.  Klicken Sie im Projektmappen-Explorer im Berichtsserverprojekt mit der rechten Maustaste auf den Ordner **Freigegebene Datenquellen** , und klicken Sie anschließend auf **Vorhandenes Element hinzufügen**. Das Dialogfeld **Vorhandenes Element hinzufügen** wird geöffnet.  
  
2.  Navigieren Sie zu einer vorhandenen RDS-Datenquelldatei (Report Definition Shared), und klicken Sie auf **Öffnen**.  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-convert-an-embedded-data-source-to-a-shared-data-source-in-report-designer"></a>So konvertieren Sie eine eingebettete Datenquelle in eine freigegebene Datenquelle in Berichts-Designer  
  
-   Klicken Sie im Bereich "Berichtsdaten" mit der rechten Maustaste in der Datenquelle, und klicken Sie dann auf **freigegebene Datenquelle konvertieren**.  
  
### <a name="to-convert-a-shared-data-source-to-an-embedded-data-source-in-report-builder"></a>So konvertieren Sie eine freigegebene Datenquelle in eine eingebettete Datenquelle in Berichts-Generator  
  
-   Klicken Sie im Bereich "Berichtsdaten" mit der rechten Maustaste in der Datenquelle, und öffnen Sie **Datenquelleneigenschaften**.  
  
-   Klicken Sie auf **eingebettete Verbindung** und Fertig stellen, die eingebettete Datenquelle erstellen, wie in einer vorherigen Vorgehensweise beschrieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Speichern von Anmeldeinformationen in einer Reporting Services-Datenquelle](report-data/store-credentials-in-a-reporting-services-data-source.md)   
 [Eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Konvertieren eine Datenquelle von eingebetteten freigegebene &#40;Berichts-Generator und SSRS&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md)   
 [Binden eines Berichts oder Modells an eine freigegebene Datenquelle &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md)   
 [Konfigurieren von Datenquelleneigenschaften für einen Bericht (Berichts-Manager)](report-data/configure-data-source-properties-for-a-report-report-manager.md)   
 [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  