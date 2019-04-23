---
title: DataSet Properties Dialog Box, Felder | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasetproperties.fields.f1
- "10140"
ms.assetid: e1367556-736e-4a6b-b9e7-10432a3e50b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3b1c49beb22a3a91e3d42aa7ce4ed99b5e107b4d
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59956926"
---
# <a name="dataset-properties-dialog-box-fields"></a>Dataseteigenschaften (Dialogfeld), Felder
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Felder** aus, um die Feldauflistung für das Berichtsdataset zu ändern. Die Felderliste wird automatisch aufgefüllt, Sie können jedoch mithilfe der Option **Felder** Abfragefelder und berechnete Felder hinzufügen, bearbeiten und löschen.  
  
## <a name="options"></a>Optionen  
 **Hinzufügen**  
 Fügt dem Dataset ein neues Abfragefeld oder berechnetes Feld hinzu.  
  
 **Delete**  
 Löscht das ausgewählte Feld aus dem Dataset.  
  
 **Name des Felds**  
 Geben Sie einen Namen für das Feld ein. Der Name des Felds muss innerhalb des Datasets eindeutig sein. Für jedes vorhandene Feld in der Datasetabfrage ist der Name bereits eingetragen.  
  
 **Feldquelle**  
 Geben Sie einen Wert für das Feld ein.  
  
 Bei einem berechneten Feld muss die Feldquelle dem Namen eines vorhandenen Felds, das von der Datasetabfrage abgerufen wird, oder einem Ausdruck entsprechen, den Sie erstellen. Beispiel: Um ein Feld zu erstellen, das 10 mal den Wert im Abfragefeld Sales darstellt, verwenden Sie folgenden Ausdruck `=10 * Fields!Sales.Value`.  
  
 Bei einem Abfragefeld muss die Feldquelle dem Namen eines vorhandenen Felds entsprechen, das von der Datasetabfrage abgerufen wurde.  
  
 **Ausdruck (fx)**  
 Fügen Sie einen Ausdruck für das berechnete Feld hinzu, oder ändern Sie diesen. Diese Schaltfläche wird nur angezeigt, wenn Sie auf **Hinzufügen** klicken und **Berechnetes Feld**auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
  
