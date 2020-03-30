---
title: Hinzufügen eines Filters zu einem Dataset (Berichts-Generator) | Microsoft-Dokumentation
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: eed37e74-6a43-4d7c-9959-2d5fa6a6aba9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67fb8bd61f337c4de0476c8a3fdb8265202b0161
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "77081658"
---
# <a name="add-a-filter-to-a-dataset-report-builder-and-ssrs"></a>Hinzufügen eines Filters zu einem Dataset (Berichts-Generator und SSRS)
  Fügen Sie einem Dataset einen Filter hinzu, um die Daten in einem Bericht einzuschränken, nachdem die Daten aus einer externen Datenquelle abgerufen wurden. Wenn Sie einem Dataset einen Filter hinzufügen, verwenden alle Berichtsteile oder Datenbereiche nur Daten, die den Filterbedingungen entsprechen.  
  
 Bei einem freigegebenen Dataset muss ein Filter, der für alle abhängigen Elemente gilt, Teil der freigegebenen Datasetdefinition auf dem Berichtsserver sein. Ein Bericht oder ein Berichtsteil, der eine Instanz eines freigegebenen Datasets enthält, kann einen zusätzlichen Filter erstellen, der nur für die Instanz gilt.  
  
 Um einen Filter hinzuzufügen, müssen Sie eine oder mehrere Bedingungen angeben, die Filtergleichungen sind. Eine Filtergleichung besteht aus einem Ausdruck, der die zu filternden Daten definiert, einem Operator und dem Vergleichswert. Der Datentyp der gefilterten Daten und des Werts muss übereinstimmen. Das Filtern von aggregierten Werden für ein Dataset wird nicht unterstützt.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-filter-to-a-shared-dataset"></a>So fügen Sie einem freigegebenen Dataset einen Filter hinzu  
  
1.  Öffnen Sie im freigegebenen Datasetmodus ein freigegebenes Dataset.  
  
2.  Klicken Sie auf der Registerkarte **Home** in der Gruppe **Freigegebene Datasets** auf Datasets. Das Dialogfeld **Dataseteigenschaften** wird angezeigt.  
  
3.  Klicken Sie auf **Filter**. Die aktuelle Liste mit Filtergleichungen wird angezeigt. Standardmäßig ist die Liste leer.  
  
4.  Klicken Sie auf **Hinzufügen**. Es wird eine neue leere Filtergleichung angezeigt.  
  
5.  Geben Sie unter **Ausdruck**einen Ausdruck für das zu filternde Feld ein, oder wählen Sie einen Ausdruck aus. Wenn Sie den Ausdruck bearbeiten möchten, klicken Sie auf die Ausdrucksschaltfläche (*fx*).  
  
6.  Wählen Sie im Listenfeld den Datentyp aus, der dem Typ der Daten in dem Ausdruck entspricht, den Sie in Schritt 5 erstellt haben.  
  
7.  Wählen Sie im Feld **Operator** den Operator aus, der vom Filter zum Vergleichen der Werte in den Feldern **Ausdruck** und **Wert** verwendet werden soll. Der gewählte Operator bestimmt, wie viele Werte ab dem nächsten Schritt verwendet werden.  
  
8.  Geben Sie im Feld **Wert** den Ausdruck oder Wert ein, den der Filter mit dem Wert im Feld **Ausdruck**vergleichen soll.  
  
     Beispiele für Filtergleichungen finden Sie unter [Beispiele für Filtergleichungen (Berichts-Generator und SSRS)](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md).  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-filter-to-an-embedded-dataset-or-a-shared-dataset-instance"></a>So fügen Sie einem eingebetteten Dataset oder einer freigegebenen Datasetinstanz einen Filter hinzu  
  
1.  Öffnen Sie einen Bericht in der Entwurfsansicht.  
  
2.  Klicken Sie im Fenster **Berichtsdaten** mit der rechten Maustaste auf ein Dataset, und klicken Sie dann auf **Dataseteigenschaften**. Das Dialogfeld **Dataseteigenschaften** wird angezeigt.  
  
3.  Klicken Sie auf **Filter**. Die aktuelle Liste mit Filtergleichungen wird angezeigt. Standardmäßig ist die Liste leer.  
  
4.  Klicken Sie auf **Hinzufügen**. Es wird eine neue leere Filtergleichung angezeigt.  
  
5.  Geben Sie unter **Ausdruck**einen Ausdruck für das zu filternde Feld ein, oder wählen Sie einen Ausdruck aus. Wenn Sie den Ausdruck bearbeiten möchten, klicken Sie auf die Ausdrucksschaltfläche (*fx*).  
  
6.  Wählen Sie im Dropdownfeld den Datentyp aus, der dem Typ der Daten in dem Ausdruck entspricht, den Sie in Schritt 5 erstellt haben.  
  
7.  Wählen Sie im Feld **Operator** den Operator aus, der vom Filter zum Vergleichen der Werte in den Feldern **Ausdruck** und **Wert** verwendet werden soll. Der gewählte Operator bestimmt, wie viele Werte ab dem nächsten Schritt verwendet werden.  
  
8.  Geben Sie im Feld **Wert** den Ausdruck oder Wert ein, den der Filter mit dem Wert im Feld **Ausdruck**vergleichen soll.  
  
     Beispiele für Filtergleichungen finden Sie unter [Beispiele für Filtergleichungen (Berichts-Generator und SSRS)](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md).  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Datasetfiltern, Datenbereichsfiltern und Gruppenfiltern &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Hinzufügen eines Filters (Berichts-Generator und SSRS)](../../reporting-services/report-design/add-a-filter-report-builder-and-ssrs.md)  
  
  
