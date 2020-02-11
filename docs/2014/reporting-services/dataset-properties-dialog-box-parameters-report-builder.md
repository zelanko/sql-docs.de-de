---
title: Dataseteigenschaften (Dialog Feld), Parameter (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10023"
ms.assetid: 3a0672ad-c969-455b-b952-585164ce1dda
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 295a40bc7964e50e5fc0c4a9ea0294b593fdde18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109389"
---
# <a name="dataset-properties-dialog-box-parameters-report-builder"></a>Dataseteigenschaften (Dialogfeld), Parameter (Berichts-Generator)
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Parameter** aus, um Abfrage Parameter hinzuzufügen, zu ändern und zu löschen.  
  
 Bei eingebetteten Datasets gelten die Optionen für das Dataset in der Berichtsdefinition.  
  
 Bei freigegebenen Datasets gelten die Optionen für die Definition des freigegebenen Datasets auf dem Berichtsserver.  
  
 Weitere Informationen finden Sie unter [Eingebettete und freigegebene Datasets (Berichts-Generator und SSRS)](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 **Add (Hinzufügen)**  
 Fügt der Liste einen neuen Parameter hinzu.  
  
 **Löschen**  
 Entfernt den ausgewählten Parameter aus der Liste.  
  
 **Pfeil nach oben**  
 Verschiebt den ausgewählten Parameter in der Liste nach oben.  
  
 **Pfeil nach unten**  
 Verschiebt den ausgewählten Parameter in der Liste nach unten.  
  
 **Parametername**  
 Geben Sie auf der Registerkarte **Abfrage** des Dialogfelds **Dataseteigenschaften** den Namen eines Abfrageparameters ein, den Sie zum Dataset hinzugefügt haben.  
  
 **Parameterwert**  
 Nur für eingebettete Datasets.  
  
 Geben Sie einen Wert für den Abfrageparameter ein. Dies kann ein statischer Wert sein oder ein Ausdruck, der sich auf ein Objekt innerhalb des Berichts bezieht. Der Ausdruck darf sich jedoch nicht auf Berichtselemente oder Felder beziehen. Standardmäßig enthält **Wert** einen Ausdruck, der auf einen Berichtsparameter verweist.  
  
 **Standardwert**  
 Nur für freigegebene Datasets.  
  
 Aktivieren Sie das Kontrollkästchen, um einen Standardwert anzugeben.  
  
 Geben Sie einen Standardwert ein. Dies kann ein statischer Wert oder ein Ausdruck sein, der auf ein Objekt innerhalb des Berichts verweist. Der Ausdruck kann nicht auf Berichtselemente, Berichtsparameter oder Felder verweisen.  
  
 Um ein Leerzeichen anzugeben, lassen Sie das Textfeld leer.  
  
 Um NULL anzugeben, aktivieren Sie die Option NULL zulassen.  
  
 **Nur Leseberechtigung**  
 Nur für freigegebene Datasets.  
  
 Aktivieren Sie diese Option, um diesen Parameter in der freigegebenen Datasetdefinition als schreibgeschützt zu markieren. Wenn das freigegebene Dataset einem Bericht hinzugefügt wird, wird der Parameter nicht in den Eigenschaften angezeigt. Wenn das freigegebene Dataset auf dem Berichtsserver zwischengespeichert wird, kann der Wert nicht geändert werden.  
  
 **Nullable**  
 Nur für freigegebene Datasets.  
  
 Aktivieren Sie diese Option, um NULL-Werte zuzulassen.  
  
 **In Abfrage auslassen**  
 Nur für freigegebene Datasets.  
  
 Aktivieren Sie diese Option, wenn ein Verweis auf einen Berichtsparameter sich in einem Ausdruck im freigegebenen Datasetfilter befindet und nicht in der Abfrage. Wenn Sie diese Option aktivieren, müssen Sie keinen Standardwert für diesen Parameter angeben, wenn die Abfrage ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Generator Hilfe zu Dialog Feldern, Bereichen und Assistenten](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Dataseteigenschaften (Dialog Feld), Abfrage &#40;Berichts-Generator&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Tutorial: Add a Parameter to Your Report (Report Builder) (Tutorial: Hinzufügen eines Parameters zu einem Bericht (Berichts-Generator))](tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Abfrage-Designer &#40;Berichts-Generator&#41;](../../2014/reporting-services/query-designers-report-builder.md)   
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
  
