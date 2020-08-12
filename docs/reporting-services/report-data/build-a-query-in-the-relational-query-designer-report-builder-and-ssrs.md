---
title: Erstellen einer Abfrage im relationalen Abfrage-Designer (Berichts-Generator und SSRS)
description: In diesem Artikel erfahren Sie, wie Sie im relationalen Abfrage-Designer eine Abfrage erstellen, damit Sie angeben können, welche Daten aus einer externen Datenquelle für ein Berichtsdataset abgerufen werden sollen.
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 04/25/2019
ms.openlocfilehash: 5ead07a1cf2afa13189b76c0c6eb75a472699543
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85808480"
---
# <a name="build-a-query-in-the-relational-query-designer-report-builder-and-ssrs"></a>Erstellen einer Abfrage im relationalen Abfrage-Designer (Berichts-Generator und SSRS)

Ein Abfrage-Designer unterstützt Sie beim Festlegen der Daten, die für ein Berichtsdataset aus einer externen Datenquelle abgerufen werden sollen. Sie verwenden einen Abfrage-Designer, wenn Sie in einem Assistenten eine Abfrage oder eine Datasetabfrage erstellen.  
  
> [!NOTE]  
> [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Ein Dataset basiert auf einer Datenquelle. Der Typ der Datenquelle und die Erstellungsumgebung bestimmen, welcher Abfrage-Designer geöffnet wird, wenn Sie die Datasetabfrage definieren. Die Funktionen eines Abfrage-Designers variieren abhängig von der zu Grunde liegenden Datenquelle. Weitere Informationen über Datenschichten finden Sie unter [Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).

 Ein Abfrage-Designer kann für die folgenden Aufgaben verwendet werden:  
  
-   Durchsuchen der Metadaten für mehrere Schemas in der externen Datenquelle  
  
-   Festlegen der für das Dataset abzurufenden Felder  
  
-   Festlegen von Beziehungen zwischen zwei Objekten, z. B. Tabellen  
  
-   Festlegen von Filtern, um die Daten vor dem Abruf als Berichtsdaten einzuschränken  
  
-   Angeben, ob Parameter erstellt werden  
  
-   Angeben von Aggregaten, um Berechnungen für die externe Datenquelle durchzuführen  
  
 Nach dem Öffnen eines Abfrage-Designers unterscheidet sich die Vorgehensweise zum Erstellen einer Abfrage für ein eingebettetes Dataset nicht von der für ein freigegebenes Dataset. In den folgenden Verfahren wird eine Abfrage für ein eingebettetes Dataset verwendet.  
  
 Weitere Informationen finden Sie unter [Benutzeroberfläche des relationalen Abfrage-Designers (Berichts-Generator)](../../reporting-services/report-data/relational-query-designer-user-interface-report-builder.md).  
  
### <a name="to-build-a-query-for-an-embedded-dataset-in-report-design-view"></a>So erstellen Sie in der Berichtsentwurfssicht eine Abfrage für ein eingebettetes Dataset  
  
1.  Öffnen Sie den Abfrage-Designer. Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf das Dataset, und klicken Sie anschließend auf **Abfrage**.  
  
     Der mit der Datenquelle verknüpfte Abfrage-Designer wird geöffnet.  
  
2.  Erweitern Sie im Bereich "Datenbanksicht" die Ordner, die eine hierarchische Ansicht von Datenbankschemaobjekten wie Tabellen, Sichten und gespeicherte Prozeduren enthalten. Klicken Sie auf das Auswahlfeld, um alle Felder für ein Objekt auszuwählen, oder erweitern Sie den Knoten, um einzelne Felder auszuwählen.  
  
     Die im Bereich "Datenbanksicht" ausgewählten Felder werden im Bereich **Felder auswählen** angezeigt.  
  
     Wenn Sie Felder aus mehreren verknüpften Datenbanktabellen auswählen, können Sie im Bereich "Beziehungen" die Tabellenbeziehungen anzeigen, die im Datenbankschema erkannt wurden.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Die Liste der Datasetfelder wird im Berichtsdatenbereich angezeigt.  
  
### <a name="to-specify-limits-for-a-query"></a>So geben Sie Grenzen für eine Abfrage an  
  
1.  Vergewissern Sie sich im relationalen Abfrage-Designer, dass Sie Felder ausgewählt haben und die Felder im Bereich **Ausgewählte Felder** angezeigt werden.  
  
2.  Klicken Sie auf der Symbolleiste des Bereichs "Angewendete Filter" auf **Filter hinzufügen**. Es wird ein neuer Zeilenfilter angezeigt.  
  
3.  Klicken Sie in das Feld **Feldname**, um die Dropdownliste der Felder anzuzeigen, und klicken Sie anschließend auf den Namen des Felds, nach dem Sie filtern möchten. Wenn Sie nach der Menge filtern möchten, klicken Sie z. B. auf das Feld, das die Anzahl von Elementen enthält.  
  
4.  Klicken Sie in das Feld **Operator**, um die Dropdownliste der Operatoren anzuzeigen, und wählen Sie anschließend den im Filter zu verwendenden Vergleichsoperator aus.  
  
5.  Geben Sie im Feld **Wert**den Wert ein, nach dem Sie filtern möchten. Wenn Sie z. B. nach Mengen größer 100 filtern möchten, geben Sie 100 ein.  
  
6.  Wählen Sie die Parameteroption in dieser Zeile aus, um einen Datasetparameter zu erstellen. Dadurch können Benutzer einen Filterwert angeben. Es wird automatisch ein Berichtsparameter erstellt, der dem Datasetparameter entspricht.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Die Liste der Datasetfelder wird im Berichtsdatenbereich angezeigt.  
  
### <a name="to-view-a-query-result-set"></a>So zeigen Sie ein Abfrageresultset an  
  
1.  Klicken Sie auf der Symbolleiste des Abfrage-Designers auf **Abfrage ausführen (!)** .  
  
    > [!NOTE]  
    >  Der Abfrage-Designer verwendet Entwurfszeitanmeldeinformationen, um die Abfrage auszuführen und das Resultset abzurufen. Weitere Informationen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](specify-credential-and-connection-information-for-report-data-sources.md).  
  
 Die Abfrage wird für die Datenquelle ausgeführt, und die zurückgegebenen Beispieldaten werden im Bereich "Abfrageergebnisse" angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsdatasets &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Hinzufügen von Daten aus externen Datenquellen (SSRS)](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md)   
 [Abfrageentwurfstools &#40;SSRS&#41;](query-design-tools-ssrs.md)   
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Berichtsentwurfsansicht &#40;Berichts-Generator&#41;](../../reporting-services/report-builder/report-design-view-report-builder.md)   
 [Freigegebene Datasetentwurfsansicht &#40;Report Builder&#41;](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
 [Abfrage-Designer in Reporting Services](https://msdn.microsoft.com/library/07efd3f1-804f-45f7-b62a-3e727a3d9835)  
  
  
