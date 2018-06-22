---
title: Dataseteigenschaften (Dialogfeld), Felder (Berichts-Generator) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
caps.latest.revision: 14
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 8e9fa18bb0edfc2edac3e58e22467ba49a01cf50
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050493"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a>Dataseteigenschaften (Dialogfeld), Felder (Berichts-Generator)
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Felder** aus, um die Feldauflistung für das Berichtsdataset zu ändern. Die Felderliste wird automatisch aufgefüllt, Sie können jedoch mithilfe der Option **Felder** Abfragefelder und berechnete Felder hinzufügen, bearbeiten und löschen.  
  
 Berechnete Felder werden nur bei eingebetteten Datasets unterstützt. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 **Hinzufügen**  
 Fügt dem Dataset ein neues Abfragefeld oder berechnetes Feld hinzu.  
  
 **Delete**  
 Löscht das ausgewählte Feld aus dem Dataset.  
  
 **Feldname**  
 Geben Sie einen Namen für das Feld ein. Der Name des Felds muss innerhalb des Datasets eindeutig sein. Für jedes vorhandene Feld im Dataset ist der Name voraufgefüllt.  
  
 **Feldquelle**  
 Geben Sie einen Wert für das Feld ein.  
  
 Bei einem berechneten Feld muss die Feldquelle dem Namen eines vorhandenen Felds, das von der Datasetabfrage abgerufen wird, oder einem Ausdruck entsprechen, den Sie erstellen. Beispiel: Um ein Feld zu erstellen, das 10 mal den Wert im Abfragefeld Sales darstellt, verwenden Sie folgenden Ausdruck `=10 * Fields!Sales.Value`.  
  
 Bei einem Abfragefeld muss die Feldquelle dem Namen eines vorhandenen Felds entsprechen, das von der Datasetabfrage abgerufen wurde.  
  
 **Ausdruck (fx)**  
 Fügen Sie einen Ausdruck für das neue berechnete Feld hinzu, oder ändern Sie diesen. Diese Schaltfläche wird nur angezeigt, wenn Sie auf **Hinzufügen** klicken und **Berechnetes Feld**auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Dataseteigenschaften (Dialogfeld), Optionen &#40;Berichts-Generator&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md)   
 [Dataseteigenschaften (Dialogfeld), filtert &#40;Berichts-Generator&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md)   
 [Dataseteigenschaften (Dialogfeld), Parameter &#40;Berichts-Generator&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md)   
 [Dataseteigenschaften (Dialogfeld), Abfrage &#40;Berichts-Generator&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  