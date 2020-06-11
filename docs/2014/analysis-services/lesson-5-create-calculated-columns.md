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
ms.openlocfilehash: b39909acacb29f68b0de49ba2093c9b812510172
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542712"
---
# <a name="lesson-6-create-calculated-columns"></a>Lektion 6: Erstellen von berechneten Spalten
  In dieser Lektion erstellen Sie neue Daten in Ihrem Modell durch Hinzufügen von berechneten Spalten. Eine berechnete Spalte basiert auf Daten, die bereits im Modell vorhanden sind. Weitere Informationen finden Sie unter [Berechnete Spalten &#40;SSAS – tabellarisch&#41;](tabular-models/ssas-calculated-columns.md).  
  
 Sie erstellen fünf neue berechnete Spalten in drei verschiedenen Tabellen. Die Schritte sind für jede Aufgabe etwas anders. Damit sollen Ihnen verschiedene Methoden zum Erstellen neuer Spalten, zum Umbenennen der Spalten und zum Platzieren der Spalten an verschiedenen Positionen in einer Tabelle aufgezeigt werden.  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema ist Teil eines Tutorials zur Tabellenmodellierung, das in der richtigen Reihenfolge absolviert werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 5: Erstellen von Beziehungen](lesson-4-create-relationships.md).  
  
## <a name="create-calculated-columns"></a>Erstellen von berechneten Spalten  
  
#### <a name="create-a-month-calendar-calculated-column-in-the-date-table"></a>Erstellen einer berechneten Spalte "Month Calendar" in der Date-Tabelle  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** , zeigen Sie auf **Modellansicht**, und klicken Sie anschließend auf **Datensicht**.  
  
     Berechnete Spalten können nur mit dem Modell-Designer in der Datensicht erstellt werden.  
  
2.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Date** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Spalte **Calendar Quarter** , und klicken Sie dann auf **Spalte einfügen**.  
  
     Links von der Spalte **Calendar Quarter** wird eine neue Spalte mit dem Namen **CalculatedColumn1** eingefügt.  
  
4.  Geben Sie in der Bearbeitungsleiste über der Tabelle die folgende Formel ein. Die Funktion AutoVervollständigen unterstützt Sie beim Eingeben des vollqualifizierten Namens von Spalten und Tabellen und listet die verfügbaren Funktionen auf.  
  
     `=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
     Anschließend werden Werte für alle Zeilen in der berechneten Spalte aufgefüllt. Wenn Sie durch die Tabelle scrollen, werden Sie sehen, dass die Zeilen über verschiedene Werte für diese Spalte verfügen, basierend auf den Daten in jeder Zeile.  
  
    > [!NOTE]  
    >  Wenn Sie einen Fehler erhalten, überprüfen Sie, ob die Spaltennamen in der Formel mit den von Ihnen in [Lektion 3: Umbenennen von Spalten](rename-columns.md)geänderten Spaltennamen übereinstimmen.  
  
5.  Benennen Sie diese Spalte in um `Month Calendar` .  
  
 Die berechnete Spalte "Month Calendar" bietet einen sortierbaren Namen für den Monat.  
  
#### <a name="create-a-day-of-week-calculated-column-in-the-date-table"></a>Erstellen einer berechneten Spalte "Day of Week" in der Date-Tabelle  
  
1.  Klicken Sie bei nach wie vor aktiver Tabelle **Date** auf das Menü **Spalte** und anschließend auf **Spalte hinzufügen**.  
  
     Ganz rechts von der Tabelle wird eine neue Spalte hinzugefügt.  
  
2.  Geben Sie in der Bearbeitungsleiste folgende Formel ein:  
  
     `=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
3.  Benennen Sie die Spalte in um `Day of Week` .  
  
4.  Klicken Sie auf die Spaltenüberschrift und ziehen Sie die Spalte zwischen die Spalte **Day Name** und die Spalte **Day of Month** .  
  
    > [!TIP]  
    >  Durch das Verschieben von Spalten in der Tabelle wird die Navigation vereinfacht.  
  
 Die berechnete Spalte "Day of Week" bietet einen sortierbaren Namen für den Wochentag.  
  
#### <a name="create-a-product-subcategory-name-calculated-column-in-the-product-table"></a>Erstellen einer berechneten Spalte "Product Subcategory Name" in der Product-Tabelle  
  
1.  Wählen Sie im Modell-Designer die Tabelle **Product** aus.  
  
2.  Führen Sie in der Tabelle einen Bildlauf nach ganz rechts aus. Beachten Sie, dass die Spalte ganz rechts **Spalte hinzufügen** (in Kursivdruck) benannt ist, und klicken Sie auf die Spaltenüberschrift.  
  
3.  Geben Sie in der Bearbeitungsleiste folgende Formel ein.  
  
     `=RELATED('Product Subcategory'[Product Subcategory Name])`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
4.  Benennen Sie die Spalte in um `Product Subcategory Name` .  
  
 Die berechnete Spalte "Product Subcategory Name" wird verwendet, um eine Hierarchie in der Product-Tabelle zu erstellen, in der Daten der Spalte "Product Subcategory Name" in der Tabelle " Product Subcategory" enthalten sind. Hierarchien können nicht mehr als eine Tabelle umfassen. Sie erstellen Hierarchien später in Lektion 7.  
  
#### <a name="create-a-product-category-name-calculated-column-in-the-product-table"></a>Erstellen einer berechneten Spalte "Product Category Name" in der Product-Tabelle  
  
1.  Klicken Sie bei nach wie vor aktiver Tabelle **Product** auf das Menü **Spalte** und anschließend auf **Spalte hinzufügen**.  
  
2.  Geben Sie in der Bearbeitungsleiste folgende Formel ein:  
  
     `=RELATED('Product Category'[Product Category Name])`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
3.  Benennen Sie die Spalte in um `Product Category Name` .  
  
 Die berechnete Spalte "Product Category Name" wird verwendet, um eine Hierarchie in der Product-Tabelle zu erstellen, in der Daten der Spalte "Product Category Name" in der Tabelle " Product Category" enthalten sind. Hierarchien können nicht mehr als eine Tabelle umfassen.  
  
#### <a name="create-a-margin-calculated-column-in-the-internet-sales-table"></a>Erstellen einer berechneten Spalte "Margin" in der Internet Sales-Tabelle  
  
1.  Wählen Sie im Modell-Designer die Tabelle **Internet Sales** aus.  
  
2.  Fügt eine neue Spalte hinzu.  
  
3.  Geben Sie in der Bearbeitungsleiste folgende Formel ein:  
  
     `=[Sales Amount]-[Total Product Cost]`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
4.  Benennen Sie die Spalte in um `Margin` .  
  
5.  Ziehen Sie die Spalte zwischen die Spalte **Sales Amount** und die Spalte **Tax Amt** .  
  
 Die berechnete Spalte "Margin" dient zur Analyse von Gewinnspannen für jede Zeile (Produktzeile).  
  
## <a name="next-step"></a>Nächster Schritt  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 7: Erstellen von Measures](lesson-6-create-measures.md).  
  
  
