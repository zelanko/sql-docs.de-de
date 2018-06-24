---
title: Verwenden von geschachtelten Tabellendaten als Eingabe für ein Genauigkeitsdiagramm | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], nested tables
- Mining Accuracy Chart [Analysis Services], input tables
- nested tables
- adding nested tables
ms.assetid: 162e0686-ada3-4dd3-9151-9589926e6613
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 63f25ca15b3ce9cdf8c97a15f91d192ef6e7de96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057304"
---
# <a name="using-nested-table-data-as-an-input-for-an-accuracy-chart"></a>Verwenden von geschachtelten Tabellendaten als Eingabe für ein Genauigkeitsdiagramm
  Wenn Sie zum Testen der Genauigkeit eines Miningmodells externe Daten verwenden und das Miningmodell geschachtelte Tabellen enthält, müssen die externen Daten auch eine Falltabelle und eine verbundene geschachtelte Tabelle enthalten.  
  
 In diesem Thema wird beschrieben, wie Sie mit für Modelltests verwendeten geschachtelten Tabellen arbeiten, wie Sie geschachtelte Tabellen und Falltabellen im Modus zuordnen und wie Sie einen Filter auf eine geschachtelte Tabelle anwenden.  
  
 Wenn Sie mit geschachtelten Tabellen arbeiten, denken Sie an folgende Tipps:  
  
-   Wenn Sie die Option **Testfälle für Miningmodell verwenden** oder **Testfälle für Miningstruktur verwenden**auswählen, muss keine Falltabelle oder geschachtelte Tabelle angegeben werden. Mit diesen Optionen wird die Definition der Testdaten in der Miningstruktur gespeichert, und die Testdaten werden automatisch ausgewählt, wenn Sie das Genauigkeitsdiagramm erstellen.  
  
-   Falls bereits eine Beziehung zwischen der Falltabelle und der geschachtelten Tabelle in der Datenquelle besteht, werden die Spalten der Miningstruktur automatisch den gleichnamigen Spalten der Eingabetabelle zugeordnet.  
  
-   Sie können erst eine geschachtelte Tabelle auswählen, nachdem Sie die Falltabelle angegeben haben. Außerdem können Sie nur dann eine geschachtelte Tabelle als Eingabe angeben, wenn das Miningmodell eine Falltabelle und eine geschachtelte Tabellenstruktur verwendet.  
  
### <a name="use-a-nested-table-as-input-to-an-accuracy-chart"></a>Verwenden einer geschachtelten Tabelle als Eingabe für ein Genauigkeitsdiagramm  
  
1.  Doppelklicken Sie auf die Miningstruktur, um sie in Data Mining-Designer zu öffnen.  
  
2.  Wählen Sie die Registerkarte **Mininggenauigkeitsdiagramm** und anschließend die Registerkarte **Eingabeauswahl** aus.  
  
3.  Wählen Sie unter **Dataset auswählen, das für das Genauigkeitsdiagramm verwendet werden soll**die Option **Anderes Dataset verwenden**aus.  
  
4.  Klicken Sie auf die Schaltfläche „Durchsuchen“ **(...)** , um das externe Dataset in einer Liste mit Datenquellensichten auf dem aktuellen Server auszuwählen.  
  
5.  Klicken Sie auf **Falltabelle auswählen**. Wählen Sie im Dialogfeld **Tabelle auswählen** in der Datenquellensicht die Tabelle aus, die die Falldaten enthält. Klicken Sie anschließend auf **OK**.  
  
6.  Klicken Sie auf **Geschachtelte Tabelle auswählen**. Wählen Sie im Dialogfeld **Tabelle auswählen** die Tabelle aus, die die geschachtelten Daten enthält. Klicken Sie anschließend auf **OK**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Wenn Sie die Beziehung zwischen der geschachtelten Tabelle und der Falltabelle ändern müssen, klicken Sie auf **Join ändern** , um das Dialogfeld **Beziehung erstellen** zu öffnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen und Zuordnen von Modelltestdaten](choose-and-map-model-testing-data.md)   
 [Anwenden von Filtern zum Modellieren von Testdaten](apply-filters-to-model-testing-data.md)  
  
  