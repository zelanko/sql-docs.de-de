---
title: 'Lektion 4: Erstellen von Beziehungen | Microsoft-Dokumentation'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bbddc0966729b93b2e9ac202966dff645c28c32c
ms.sourcegitcommit: e8e013b4d4fbd3b25f85fd6318d3ca8ddf73f31e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42792030"
---
# <a name="lesson-4-create-relationships"></a>Lektion 4: Erstellen von Beziehungen
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion überprüfen Sie die Beziehungen, die beim Importieren von Daten automatisch erstellt wurden. Zudem fügen Sie neue Beziehungen zwischen verschiedenen Tabellen hinzu. Eine Beziehung ist eine Verbindung zwischen zwei Tabellen, die festlegt, wie die Daten in diesen Tabellen miteinander in Beziehung gesetzt werden sollen. Die DimProduct-Tabelle und die DimProductSubcategory-Tabelle haben beispielsweise eine Beziehung, die darauf beruht, dass jedes Produkt zu einer Unterkategorie gehört. Weitere Informationen finden Sie unter [Beziehungen](../analysis-services/tabular-models/relationships-ssas-tabular.md).
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion an, Sie sollten die vorherige Lektion abgeschlossen haben: [Lektion 3: Markieren als Datumstabelle](../analysis-services/lesson-3-mark-as-date-table.md). 
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>Überprüfen vorhandener Beziehungen und Hinzufügen neuer Beziehungen  
Wenn Sie Daten mithilfe des Tabellenimport-Assistenten importiert haben, haben Sie sieben Tabellen aus der Datenbank "AdventureWorksDW". Wenn Sie Daten aus einer relationalen Quelle importieren, werden im Allgemeinen vorhandene Beziehungen automatisch zusammen mit den Daten importiert. Bevor Sie jedoch mit der Erstellung des Modells fortfahren, überprüfen Sie, ob die Beziehungen zwischen den Tabellen ordnungsgemäß erstellt wurden. In diesem Lernprogramm fügen Sie auch drei neue Beziehungen hinzu.  
  
#### <a name="to-review-existing-relationships"></a>So überprüfen Sie vorhandene Beziehungen  
  
1.  Klicken Sie auf die **Modell** Menü > **Modellansicht** > **Diagrammansicht**.  

    Der Modell-Designer wird jetzt in der Diagrammsicht angezeigt. Hierbei handelt es sich um ein grafisches Format, in dem alle von Ihnen importierten Tabellen mit Zeilen zwischen den Tabellen angezeigt werden. Die Zeilen zwischen den Tabellen geben die Beziehungen an, die automatisch beim Importieren der Daten erstellt wurden.
    
    ![als – tabellarische-lesson4-Diagramm](../analysis-services/media/as-tabular-lesson4-diagram.png)
  
    Verwenden Sie die Steuerelemente der Miniaturkarte unten rechts im Modell-Designer, um die Sicht so anzupassen, dass so viele Tabellen wie möglich berücksichtigt werden. Sie können auch klicken und ziehen Sie Tabellen an unterschiedliche Positionen verschieben, näher zusammen, oder Sie sie in einer bestimmten Reihenfolge anordnen. Das Verschieben von Tabellen beeinflusst nicht die bereits zwischen den Tabellen bestehenden Beziehungen. Um alle Spalten in einer bestimmten Tabelle anzuzeigen, klicken Sie auf, und ziehen Sie auf einer Tabellenkante zu erweitern oder zu verkleinern.  
  
2.  Klicken Sie auf die durchgezogene Linie zwischen den **DimCustomer** Tabelle und die **DimGeography** Tabelle. Die durchgezogene Linie zwischen diesen zwei Tabellen zeigt an, dass diese Beziehung aktiv ist. Sie wird folglich bei der Berechnung von DAX-Formeln standardmäßig verwendet.  
  
    Beachten Sie, dass die **GeographyKey** -Spalte in der **DimCustomer** Tabelle und die **GeographyKey** -Spalte in der **DimGeography** Tabelle jetzt sowohl Jede in ein Feld angezeigt werden. Diese Anzeige sind die Spalten in der Beziehung verwendet. Die Eigenschaften der Beziehung werden jetzt auch im Fenster **Eigenschaften** angezeigt.  
  
    > [!TIP]  
    > Zusätzlich zur Verwendung im Modell-Designers in der Diagrammsicht können auch können das Dialogfeld "Beziehungen verwalten" Sie die Beziehungen zwischen allen Tabellen in einem Tabellenformat anzuzeigen. Mit der rechten Maustaste **Beziehungen** tabellarischer Modell-Explorer, und klicken Sie auf **Beziehungen verwalten**. Das Dialogfeld "Beziehungen verwalten" anzeigen, der Beziehungen, die beim Importieren von Daten automatisch erstellt wurden.  
  
3.  Den Modell-Designer in Diagrammsicht oder das Dialogfeld "Beziehungen verwalten" verwenden, um sicherzustellen, dass die folgenden Beziehungen erstellt wurden, wenn jede der Tabellen aus der AdventureWorksDW-Datenbank importiert wurden:  
  
    |Active|Tabelle|Verknüpfte Suchtabelle|  
    |----------|---------|------------------------|  
    |Benutzerkontensteuerung|**DimCustomer [GeographyKey]**|**DimGeography [GeographyKey]**|  
    |Benutzerkontensteuerung|**DimProduct [ProductSubcategoryKey]**|**DimProductSubcategory [ProductSubcategoryKey]**|  
    |Benutzerkontensteuerung|**DimProductSubcategory [ProductCategoryKey]**|**DimProductCategory [ProductCategoryKey]**|  
    |Benutzerkontensteuerung|**"Factinternetsales" [CustomerKey]**|**DimCustomer [CustomerKey]**|  
    |Benutzerkontensteuerung|**"Factinternetsales" [ProductKey]**|**DimProduct [ProductKey]**|  
  
    Wenn die Beziehungen in der obigen Tabelle nicht vorhanden sind, stellen Sie sicher, dass Ihr Modell in den folgenden Tabellen enthält: DimCustomer, DimDate, DimGeography, DimProduct, DimProductCategory, DimProductSubcategory und FactInternetSales. Werden Tabellen über die gleiche Datenquellenverbindung zu unterschiedlichen Zeitpunkten importiert, werden Beziehungen zwischen diesen Tabellen nicht automatisch erstellt, sondern sind manuell zu erstellen.  

### <a name="take-a-closer-look"></a>Ausführlichere Betrachtung
In der Diagrammansicht sehen Sie sich ein Pfeil, ein Sternchen und eine Zahl auf die Zeilen, die die Beziehung zwischen Tabellen veranschaulichen.

![als tabellarische-lesson4-Inline](../analysis-services/media/as-tabular-lesson4-line.png)

Der Pfeil zeigt der filterrichtung, das Sternchen zeigt Tabelle die n-Seite in der Kardinalität der Beziehung und die 1 verdeutlicht, dass diese Tabelle auf einer Seite der Beziehung ist. Wenn Sie eine Beziehung bearbeiten müssen. z. B. ändern Sie die Beziehung die filterrichtung oder Kardinalität zu, doppelklicken Sie auf die Beziehungslinie, in der Diagrammsicht, um das Dialogfeld "Beziehung bearbeiten" zu öffnen.

![als tabellarische-lesson4-bearbeiten](../analysis-services/media/as-tabular-lesson4-edit.png)

In den meisten Fällen müssen Sie nie eine Beziehung zu bearbeiten. Diese Features sind nur für den erweiterten datenmodellierung und befinden sich außerhalb des Bereichs in diesem Tutorial. Weitere Informationen finden Sie unter [bidirektionale kreuzfilter für tabellarische Modelle in SQL Server 2016 Analysis Services](../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md).

In einigen Fällen müssen Sie möglicherweise zusätzliche Beziehungen zwischen Tabellen im Modell erstellen, um eine bestimmte Geschäftslogik zu unterstützen. Für dieses Tutorial müssen Sie drei zusätzliche Beziehungen zwischen der FactInternetSales-Tabelle und der DimDate-Tabelle erstellen.  
  
#### <a name="to-add-new-relationships-between-tables"></a>So fügen Sie neue Beziehungen zwischen Tabellen hinzu  
  
1.  Im Modell-Designer in der **"factinternetsales"** Tabellen, warten Sie, und klicken Sie auf der **OrderDate** Spalte ziehen Sie dann den Cursor zu der **Datum** -Spalte in der  **DimDate** Tabelle, und veröffentlichen.  

    Eine durchgezogene Linie wird angezeigt, mit der Sie erstellt haben, eine aktive Beziehung zwischen der **OrderDate** -Spalte in der **Internetverkäufe** Tabelle und die **Datum** -Spalte in der **Datum** Tabelle. 
  
      ![als tabellarische-lesson4-neue](../analysis-services/media/as-tabular-lesson4-new.png) 
  
    > [!NOTE]  
    > Beim Erstellen von Beziehungen wird die Kardinalität und die filterrichtung zwischen der primären Tabelle und der zugehörigen Nachschlagetabelle automatisch ausgewählt.  
  
2.  In der **"factinternetsales"** Tabellen, warten Sie, und klicken Sie auf der **DueDate** Spalte ziehen Sie dann den Cursor zu der **Datum** -Spalte in der **DimDate** Tabelle, und klicken Sie dann Version.  
  
    Eine gepunktete Linie wird angezeigt, mit der Sie erstellt haben, eine inaktive Beziehung zwischen der **DueDate** -Spalte in der **"factinternetsales"** Tabelle und die **Datum** -Spalte in der  **DimDate** Tabelle. Mehrere Beziehungen zwischen Tabellen sind möglich. Doch nur eine Beziehung kann jeweils aktiv sein.  
  
3.  Erstellen Sie abschließend eine weitere Beziehung; in der **"factinternetsales"** Tabellen, warten Sie, und klicken Sie auf der **ShipDate** Spalte ziehen Sie dann den Cursor zu der **Datum** -Spalte in der **DimDate**Tabelle, und veröffentlichen.  
    
     ![als-tabellarische-lesson4-newinactive](../analysis-services/media/as-tabular-lesson4-newinactive.png)
  
## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 5: Erstellen von berechneten Spalten](../analysis-services/lesson-5-create-calculated-columns.md).
  
  
  
