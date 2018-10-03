---
title: Erstellen eines freigegebenen Datasets oder eingebetteten Datasets (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: d1d7bc71-f0e9-4ce5-b3ad-6fee54388a31
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 39f8f2b9f8926a81c808e82f57cad13934336902
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133260"
---
# <a name="create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs"></a>Erstellen eines freigegebenen Datasets oder eingebetteten Datasets (Berichts-Generator und SSRS)
  Sie können ein eingebettetes Dataset zur Verwendung in einem einzelnen Bericht oder ein freigegebenes Dataset erstellen, das auf einem Berichtsserver gespeichert und von mehreren Berichten verwendet werden kann. Damit Sie ein Dataset erstellen können, muss eine eingebettete oder freigegebene Datenquelle vorhanden sein.  
  
 Verwenden Sie Berichts-Generator für folgende Tasks:  
  
-   Erstellen eines freigegebenen Datasets in der Datasetentwurfsansicht. Für freigegebene Datasets müssen veröffentlichte freigegebene Datenquellen verwendet werden.  
  
-   Erstellen eines eingebetteten Datasets in der Berichtsentwurfsansicht.  
  
-   Speichern Sie das Dataset direkt auf dem Berichtsserver oder der SharePoint-Website.  
  
 Verwenden Sie Berichts-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , um die folgenden Tasks auszuführen:  
  
1.  Erstellen Sie im Projektmappen-Explorer ein freigegebenes Dataset. Für freigegebene Datasets müssen Datenquellen aus dem Ordner Freigegebene Datenquellen im Projektmappen-Explorer verwendet werden.  
  
2.  Erstellen Sie im Berichtsdatenbereich ein eingebettetes Dataset.  
  
3.  Stellen Sie die freigegebenen Datasets und freigegebene Datenquelle mit dem Bericht optional bereit. Verwenden Sie für jeden Elementtyp Projekteigenschaften, um Pfade zu Ordnern auf dem Berichtsserver oder einer SharePoint-Website anzugeben.  
  
 Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-open-report-builder-and-create-a-shared-dataset"></a>So öffnen Sie den Berichts-Generator und erstellen ein freigegebenes Dataset  
  
1.  So öffnen Sie den Berichts-Generator. Der Bereich **Neuer Bericht oder neues Dataset** wird geöffnet, wie in der folgenden Abbildung dargestellt:  
  
     ![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")  
  
    > [!NOTE]  
    >  Wenn der Bereich **Neuer Bericht oder neues Dataset** nicht angezeigt wird, klicken Sie in der Schaltfläche „Berichts-Generator“ auf **Neu**.  
  
2.  Klicken Sie im linken Bereich unter **Dataset erstellen**auf **Freigegebenes Dataset**.  
  
3.  Klicken Sie im rechten Bereich auf **Durchsuchen** , um eine freigegebene Datenquelle vom Berichtsserver auszuwählen, und klicken Sie dann auf **Erstellen**. Der mit der freigegebenen Datenquelle verknüpfte Abfrage-Designer wird geöffnet.  
  
4.  Geben Sie im Abfrage-Designer die Felder an, die in das Dataset einbezogen werden sollen.  
  
5.  Klicken Sie auf **Ausführen** (**!**), um die Abfrage auszuführen.  
  
6.  Klicken Sie in der Schaltfläche **Berichts-Generator** auf **Speichern** oder **Speichern unter** , um das freigegebene Dataset auf dem Berichtsserver zu speichern.  
  
7.  Um den Berichts-Generator zu beenden, klicken Sie auf **Berichts-Generator**und dann auf **Berichts-Generator beenden**. Um mit Berichten zu arbeiten, klicken Sie auf **Berichts-Generator**und dann auf **Neu** oder **Öffnen**.  
  
### <a name="to-set-query-parameter-options"></a>So legen Sie Abfrageparameteroptionen fest  
  
1.  So öffnen Sie den Berichts-Generator.  
  
2.  Klicken Sie auf **Öffnen**.  
  
3.  Wechseln Sie zum Berichtsserver, und wählen Sie den Ordner für die freigegebene Datenquelle aus.  
  
4.  Klicken Sie unter **Elemente des Typs**in der Dropdownliste auf „Datasets (*.rsd)“.  
  
5.  Wählen Sie das freigegebene Dataset aus, und klicken Sie dann auf **Öffnen**. Der verknüpfte Abfrage-Designer wird geöffnet.  
  
6.  Klicken Sie im Menüband auf **Dataseteigenschaften**.  
  
7.  Klicken Sie auf **Parameter**. Legen Sie auf dieser Seite als Standardwert eine Konstante oder einen Ausdruck fest, markieren Sie den Parameter als schreibgeschützt, auf NULL festlegbar oder mit **In Abfrage auslassen**. Weitere Informationen finden Sie unter [Dataseteigenschaften &#40;Dialogfeld, Parameter, Berichts-Generator&#41;](../dataset-properties-dialog-box-parameters-report-builder.md).  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
### <a name="to-create-a-dataset-from-a-sql-server-relational-database"></a>So erstellen Sie ein Dataset aus einer relationalen SQL Server-Datenbank  
  
1.  Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf den Namen der Datenquelle, und klicken Sie dann auf **Dataset hinzufügen**. Die Seite **Abfrage** des Dialogfelds **Dataseteigenschaften** wird aufgerufen.  
  
2.  Geben Sie im Textfeld **Name**einen Namen für das Dataset ein, oder übernehmen Sie den Standardnamen.  
  
    > [!NOTE]  
    >  Der Name des Datasets wird intern im Bericht verwendet. Zur Verdeutlichung sollte der Name des Datasets die Daten beschreiben, die von der Abfrage zurückgegeben werden.  
  
3.  Wählen Sie aus der Liste **Datenquelle**eine vorhandene freigegebene Datenquelle aus, oder klicken Sie auf **Neu** , um eine neue eingebettete Datenquelle zu erstellen.  
  
4.  Wählen Sie einen **Abfragetyp** . Die verfügbaren Optionen sind vom Datenquellentyp abhängig.  
  
    -   Wählen Sie **Text** aus, um eine Abfrage zu schreiben, die die Abfragesprache der Datenquelle verwendet.  
  
    -   Wählen Sie **Table** aus, um alle Felder in einer relationalen Datenbanktabelle zurückzugeben.  
  
    -   Wählen Sie **Gespeicherte Prozedur** , um eine gespeicherte Prozedur nach Namen auszuführen.  
  
5.  Geben Sie in **Abfrage**die Abfrage, die gespeicherte Prozedur oder den Tabellennamen ein. Oder klicken Sie auf **Abfrage-Designer** , um den grafischen oder textbasierten Abfrage-Designer zu öffnen, oder auf **Importieren** , um die Abfrage aus einem vorhandenen Bericht zu importieren.  
  
     In einigen Fällen kann die von der Abfrage angegebene Feldauflistung nur durch Anwendung der Abfrage auf die Datenquelle ermittelt werden. Eine gespeicherte Prozedur gibt möglicherweise im Resultset eine variable Feldauflistung zurück. Klicken Sie auf **Felder aktualisieren** , um die Abfrage auf die Datenquelle anzuwenden und die Feldnamen abzurufen, die erforderlich sind, um die Dataset-Feldauflistung im Berichtsdatenbereich aufzufüllen. Die Feldauflistung wird unter dem Datasetknoten angezeigt, nachdem Sie das Dialogfeld **Dataseteigenschaften** geschlossen haben.  
  
6.  Geben Sie in das Feld **Timeout**die Anzahl der Sekunden ein, die der Berichtsserver auf eine Antwort von der Datenbank warten soll. Der Standardwert beträgt 0 Sekunden. Bei diesem Wert gibt es keinen Timeout.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Das Dataset und seine Feldauflistung werden im Berichtsdatenbereich unter dem Datenquellenknoten angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)   
 [Abfrage-Designer &#40;Berichts-Generator&#41;](../query-designers-report-builder.md)   
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md)   
 [Eingebettete und freigegebene Datasets &#40;Berichts-Generator und SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
