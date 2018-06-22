---
title: Geben Sie die Spalte zuordnen (Dialogfeld) (Mininggenauigkeitsdiagramm) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 350b0f55f7ae4d445945905984f3e68a34d5c318
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049051"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a>Spaltenzuordnung angeben (Dialogfeld, Mininggenauigkeitsdiagramm)
  Auf der Registerkarte **Spaltenzuordnung angeben** können Sie Tabellen aus einer externen Datenquelle auswählen und die Spalten einem Data Mining-Modell zuordnen. Mithilfe der externen Daten können Sie dann die Genauigkeit eines Miningmodells testen und die Ergebnisse im Genauigkeitsdiagramm anzeigen.  
  
 **Weitere Informationen:** [Tests und Überprüfung &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Tastatur  
 **Miningstruktur**  
 Zeigt die ausgewählte Miningstruktur mit dem zu testenden Modell an.  
  
 **Struktur auswählen**  
 Klicken Sie auf diese Option, um das Dialogfeld **Miningstruktur auswählen** zu öffnen und eine andere Miningstruktur auszuwählen.  
  
 **Eingabetabelle(n) auswählen**  
 Zeigt die zum Generieren des Prognosegütediagramms ausgewählten Eingabetabellen an. Wählen Sie die Tabelle mit den Testdaten aus, die Sie zum Testen der Genauigkeit des Modells verwenden möchten.  
  
> [!NOTE]  
>  Klicken Sie auf **Falltabelle auswählen** , wenn der Bereich keine Tabellen enthält, um Tabellen aus einer Datenquellensicht hinzuzufügen.  
  
 **Tabelle entfernen**  
 Entfernt die ausgewählte Tabelle. Diese Schaltfläche ist deaktiviert, wenn keine Tabelle ausgewählt wurde oder in der Liste **Eingabetabelle(n) auswählen** keine Tabellen angezeigt werden.  
  
 **Falltabelle auswählen**  
 Klicken Sie auf diese Option, um das Dialogfeld **Tabelle auswählen** zu öffnen und eine Datenquellensicht auszuwählen.  
  
 **Hinweis** Diese Schaltfläche wird nur angezeigt, wenn noch keine Falltabelle ausgewählt wurde. Löschen Sie die Liste, indem Sie alle vorhandenen Tabellen auswählen und anschließend auf **Tabelle entfernen**klicken, um die Schaltfläche zu aktivieren und eine andere Falltabelle auswählen zu können.  
  
 **Geschachtelte Tabelle auswählen**  
 Öffnet das Dialogfeld **Tabelle auswählen** . Diese Schaltfläche wird nur angezeigt, wenn eine Falltabelle ausgewählt wurde. Wenn die entsprechende Miningstruktur keine geschachtelte Tabelle enthält, ist diese Schaltfläche deaktiviert.  
  
 **Join ändern**  
 Öffnet das Dialogfeld **Geschachtelten Join angeben** . Diese Schaltfläche ist nur aktiviert, wenn eine geschachtelte Tabelle ausgewählt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Tests und Überprüfung miningmodelltasks und &#40;Datamining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Mining-Genauigkeitsdiagramm-Designer &#40;Datamining&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  