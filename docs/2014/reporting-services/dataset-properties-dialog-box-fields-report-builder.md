---
title: Dataseteigenschaften (Dialog Feld), Felder (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 375d8eda6f0863dbe3852f1a88ea2e58ecc85b80
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109433"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a>Dataseteigenschaften (Dialogfeld), Felder (Berichts-Generator)
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Felder** aus, um die Feldauflistung für das Berichtsdataset zu ändern. Die Felderliste wird automatisch aufgefüllt, Sie können jedoch mithilfe der Option **Felder** Abfragefelder und berechnete Felder hinzufügen, bearbeiten und löschen.  
  
 Berechnete Felder werden nur bei eingebetteten Datasets unterstützt. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 **Add (Hinzufügen)**  
 Fügt dem Dataset ein neues Abfragefeld oder berechnetes Feld hinzu.  
  
 **Löschen**  
 Löscht das ausgewählte Feld aus dem Dataset.  
  
 **Feldname**  
 Geben Sie einen Namen für das Feld ein. Der Name des Felds muss innerhalb des Datasets eindeutig sein. Für jedes vorhandene Feld im Dataset ist der Name voraufgefüllt.  
  
 **Feldquelle**  
 Geben Sie einen Wert für das Feld ein.  
  
 Bei einem berechneten Feld muss die Feldquelle dem Namen eines vorhandenen Felds, das von der Datasetabfrage abgerufen wird, oder einem Ausdruck entsprechen, den Sie erstellen. Beispiel: Um ein Feld zu erstellen, das 10 mal den Wert im Abfragefeld Sales darstellt, verwenden Sie folgenden Ausdruck `=10 * Fields!Sales.Value`.  
  
 Bei einem Abfragefeld muss die Feldquelle dem Namen eines vorhandenen Felds entsprechen, das von der Datasetabfrage abgerufen wurde.  
  
 **Ausdruck (fx)**  
 Fügen Sie einen Ausdruck für das neue berechnete Feld hinzu, oder ändern Sie diesen. Diese Schaltfläche wird nur angezeigt, wenn Sie auf **Hinzufügen** klicken und **Berechnetes Feld**auswählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Berichts-Generator Hilfe zu Dialog Feldern, Bereichen und Assistenten](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Dataseteigenschaften (Dialog Feld), Optionen &#40;Berichts-Generator&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md)   
 [Dataseteigenschaften (Dialog Feld), Filter &#40;Berichts-Generator&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md)   
 [Dataseteigenschaften (Dialog Feld), Parameter &#40;Berichts-Generator&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md)   
 [Dataseteigenschaften (Dialog Feld), Abfrage &#40;Berichts-Generator&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
