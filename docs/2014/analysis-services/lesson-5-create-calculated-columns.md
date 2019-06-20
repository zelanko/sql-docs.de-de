---
title: 'Lektion 6: Erstellen von berechneten Spalten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58ba761f3e32f13ddcf81dc9875057195298c705
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66078562"
---
# <a name="lesson-6-create-calculated-columns"></a>Lektion 6: Erstellen von berechneten Spalten
  In dieser Lektion erstellen Sie neue Daten in Ihrem Modell durch Hinzufügen von berechneten Spalten. Eine berechnete Spalte basiert auf Daten, die bereits im Modell vorhanden sind. Weitere Informationen finden Sie unter [Berechnete Spalten &#40;SSAS – tabellarisch&#41;](tabular-models/ssas-calculated-columns.md).  
  
 Sie erstellen fünf neue berechnete Spalten in drei verschiedenen Tabellen. Die Schritte sind für jede Aufgabe etwas anders. Damit sollen Ihnen verschiedene Methoden zum Erstellen neuer Spalten, zum Umbenennen der Spalten und zum Platzieren der Spalten an verschiedenen Positionen in einer Tabelle aufgezeigt werden.  
  
 Geschätzte Zeit zum Abschließen dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lesson 5: Erstellen von Beziehungen](lesson-4-create-relationships.md).  
  
## <a name="create-calculated-columns"></a>Erstellen von berechneten Spalten  
  
#### <a name="create-a-month-calendar-calculated-column-in-the-date-table"></a>Erstellen einer berechneten Spalte "Month Calendar" in der Date-Tabelle  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] auf das Menü **Modell**, zeigen Sie auf **Modellansicht**, und klicken Sie anschließend auf **Datensicht**.  
  
     Berechnete Spalten können nur mit dem Modell-Designer in der Datensicht erstellt werden.  
  
2.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Date** .  
  
3.  Mit der rechten Maustaste die **Calendar Quarter** Spalte, und klicken Sie dann auf **Spalte einfügen**.  
  
     Eine neue Spalte namens **CalculatedColumn1** eingefügt wird, auf der linken Seite von der **Calendar Quarter** Spalte.  
  
4.  Geben Sie in der Bearbeitungsleiste über der Tabelle die folgende Formel ein. Mit der AutoVervollständigen-Funktion können Sie die vollqualifizierten Namen von Spalten und Tabellen auf einfache Weise eingeben und die verfügbaren Funktionen auflisten.  
  
     `=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
     Werte werden dann für alle Zeilen in der berechneten Spalte eingetragen. Wenn Sie in der Tabelle einen Bildlauf nach unten durchführen, sehen Sie, dass Zeilen für diese Spalte je nach den Daten in jeder Zeile unterschiedliche Werte haben können.  
  
    > [!NOTE]  
    >  Wenn Sie eine Fehlermeldung erhalten, überprüfen Sie die Spaltennamen in der Formel entsprechen, die Spaltennamen, die Sie geändert, im haben [Lektion 3: Umbenennen von Spalten](rename-columns.md).  
  
5.  Benennen Sie diese Spalte in `Month Calendar`.  
  
 Die berechnete Spalte "Month Calendar" bietet einen sortierbaren Namen für den Monat.  
  
#### <a name="create-a-day-of-week-calculated-column-in-the-date-table"></a>Erstellen einer berechneten Spalte "Day of Week" in der Date-Tabelle  
  
1.  Klicken Sie bei nach wie vor aktiver Tabelle **Date** auf das Menü **Spalte** und anschließend auf **Spalte hinzufügen**.  
  
     Ganz rechts von der Tabelle wird eine neue Spalte hinzugefügt.  
  
2.  Geben Sie in der Bearbeitungsleiste folgende Formel ein:  
  
     `=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
3.  Benennen Sie die Spalte in `Day of Week`.  
  
4.  Klicken Sie auf die Spaltenüberschrift und ziehen Sie die Spalte zwischen die Spalte **Day Name** und die Spalte **Day of Month** .  
  
    > [!TIP]  
    >  Durch das Verschieben von Spalten in der Tabelle wird die Navigation vereinfacht.  
  
 Die berechnete Spalte "Day of Week" bietet einen sortierbaren Namen für den Wochentag.  
  
#### <a name="create-a-product-subcategory-name-calculated-column-in-the-product-table"></a>Erstellen einer berechneten Spalte "Product Subcategory Name" in der Product-Tabelle  
  
1.  Wählen Sie im Modell-Designer die Tabelle **Product** aus.  
  
2.  Führen Sie in der Tabelle einen Bildlauf nach ganz rechts aus. Beachten Sie, dass die ganz rechts stehende Spalte **Spalte hinzufügen** heißt (in Kursivschrift). Klicken Sie auf die Spaltenüberschrift.  
  
3.  Geben Sie in der Bearbeitungsleiste folgende Formel ein.  
  
     `=RELATED('Product Subcategory'[Product Subcategory Name])`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
4.  Benennen Sie die Spalte in `Product Subcategory Name`.  
  
 Die berechnete Spalte "Product Subcategory Name" wird verwendet, um eine Hierarchie in der Product-Tabelle zu erstellen, in der Daten der Spalte "Product Subcategory Name" in der Tabelle " Product Subcategory" enthalten sind. Hierarchien können maximal eine Tabelle umfassen. Sie erstellen Hierarchien später in Lektion 7.  
  
#### <a name="create-a-product-category-name-calculated-column-in-the-product-table"></a>Erstellen einer berechneten Spalte "Product Category Name" in der Product-Tabelle  
  
1.  Klicken Sie bei nach wie vor aktiver Tabelle **Product** auf das Menü **Spalte** und anschließend auf **Spalte hinzufügen**.  
  
2.  Geben Sie in der Bearbeitungsleiste folgende Formel ein:  
  
     `=RELATED('Product Category'[Product Category Name])`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
3.  Benennen Sie die Spalte in `Product Category Name`.  
  
 Die berechnete Spalte "Product Category Name" wird verwendet, um eine Hierarchie in der Product-Tabelle zu erstellen, in der Daten der Spalte "Product Category Name" in der Tabelle " Product Category" enthalten sind. Hierarchien können maximal eine Tabelle umfassen.  
  
#### <a name="create-a-margin-calculated-column-in-the-internet-sales-table"></a>Erstellen einer berechneten Spalte "Margin" in der Internet Sales-Tabelle  
  
1.  Wählen Sie im Modell-Designer die Tabelle **Internet Sales** aus.  
  
2.  Fügt eine neue Spalte hinzu.  
  
3.  Geben Sie in der Bearbeitungsleiste folgende Formel ein:  
  
     `=[Sales Amount]-[Total Product Cost]`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
4.  Benennen Sie die Spalte in `Margin`.  
  
5.  Ziehen Sie die Spalte zwischen die Spalte **Sales Amount** und die Spalte **Tax Amt** .  
  
 Die berechnete Spalte "Margin" dient zur Analyse von Gewinnspannen für jede Zeile (Produktzeile).  
  
## <a name="next-step"></a>Nächster Schritt  
 Um dieses Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 7: Erstellen von Measures](lesson-6-create-measures.md).  
  
  
