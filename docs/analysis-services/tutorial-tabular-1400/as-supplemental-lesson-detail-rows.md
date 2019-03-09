---
title: 'Analysis Services Tutorial ergänzende Lektion: Detailzeilen | Microsoft-Dokumentation'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 20f5f32d4cca8b69d94410296e3653a92a1d6d46
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685241"
---
# <a name="supplemental-lesson---detail-rows"></a>Ergänzende Lektion: Detailzeilen

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser ergänzenden Lektion verwenden Sie den DAX-Editor, um einen benutzerdefinierten Detailzeilenausdruck zu definieren. Ein Detailzeilenausdrucks ist es sich um eine Eigenschaft auf ein Measure, die Endbenutzer Weitere Informationen zu aggregierten Ergebnissen eines Measures. 
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

In diesem Artikel ergänzende Lektion ist Teil einer Tutorials zur tabellenmodellierung. Vor dem Ausführen der Aufgaben in dieser ergänzenden Lektion an, Sie sollten abgeschlossen haben alle vorherige Lektionen oder über einen abgeschlossenen Adventure Works Internet Sales-Beispiel-Modellprojekt.  
  
## <a name="whats-the-issue"></a>Was ist das Problem?

Betrachten Sie die Details des Measure "internettotalsales" an, bevor Sie einen Detailzeilenausdruck hinzufügen.

1.  Klicken Sie in SSDT auf das **Modell** Menü > **in Excel analysieren** öffnen Excel und erstellen eine leere PivotTable.
  
2.  In **PivotTable Fields**, Hinzufügen der **"internettotalsales" an** Measure aus der Tabelle "factinternetsales", um **Werte**, **"calendaryear"** aus der DimDate-Tabelle zu **Spalten**, und **EnglishCountryRegionName** zu **Zeilen**. Die PivotTable zeigt nun ein aggregiertes Ergebnis aus dem Measure "internettotalsales" nach Region und Jahr an. 

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-pivottable.png)

3. Doppelklicken Sie auf einen aggregierten Wert für ein Jahr und einen Regionsnamen, in der PivotTable. Hier doppelklicken Sie den Wert für Australien und das Jahr 2014. Ein neues Blatt wird geöffnet, mit Daten, aber nicht wirklich hilfreich sind.

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-sheet.png)
  
Was wir hier ist eine Tabelle mit Spalten und Zeilen mit Daten, die zum aggregierten Ergebnis des Measure "internettotalsales" an beitragen möchten. Zu diesem Zweck können Sie einen Detailzeilenausdruck als Eigenschaft des Measure hinzufügen.

## <a name="add-a-detail-rows-expression"></a>Fügen Sie einen Detailzeilenausdruck

#### <a name="to-create-a-detail-rows-expression"></a>Erstellen Sie einen Detailzeilenausdruck 
  
1. Klicken Sie im measureraster der Tabelle "factinternetsales" auf die **"internettotalsales" an** Measure. 

2. In **Eigenschaften** > **Detailzeilenausdruck**, klicken Sie auf die Schaltfläche "Editor", um den DAX-Editor zu öffnen.

    ![as-lesson-detail-rows-ellipse](../tutorial-tabular-1400/media/as-lesson-detail-rows-ellipse.png)

3. Geben Sie im DAX-Editor den folgenden Ausdruck ein:

    ```
    SELECTCOLUMNS(
    FactInternetSales,
    "Sales Order Number", FactInternetSales[SalesOrderNumber],
    "Customer First Name", RELATED(DimCustomer[FirstName]),
    "Customer Last Name", RELATED(DimCustomer[LastName]),
    "City", RELATED(DimGeography[City]),
    "Order Date", FactInternetSales[OrderDate],
    "Internet Total Sales", [InternetTotalSales]
    )

    ```

    Dieser Ausdruck gibt die Namen, Spalten und Berechnungsergebnisse aus der Tabelle "factinternetsales" und die verknüpfte Tabellen werden zurückgegeben, wenn ein Benutzer ein aggregiertes Ergebnis in einer PivotTable oder eines Berichts doppelklickt.

4. Löschen Sie in Excel das Blatt, das in Schritt 3 erstellt haben, und doppelklicken Sie dann einen aggregierten Wert. Dieses Mal öffnet mit einem detailzeilenausdruck für das Measure definiert, ein neues Blatt mit viel mehr hilfreichen Daten.

    ![als-Lektion-Detail-Zeilen-detailsheet](../tutorial-tabular-1400/media/as-lesson-detail-rows-detailsheet.png)

5. Stellen Sie Ihr Modell erneut bereit.

  
## <a name="see-also"></a>Siehe auch  

[SELECTCOLUMNS-Funktion (DAX)](https://msdn.microsoft.com/library/mt761759.aspx)  
[Ergänzende Lektion – Dynamische Sicherheit](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Ergänzende Lektion – Unregelmäßige Hierarchien](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)  
