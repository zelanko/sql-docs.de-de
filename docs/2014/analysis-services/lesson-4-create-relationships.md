---
title: 'Lektion 5: Erstellen von Beziehungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: abac1a00-f827-4c3e-a473-6db5c8a3a66f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7a80f607c3187e967404ce018b7eed00497d9c01
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078582"
---
# <a name="lesson-5-create-relationships"></a>Lektion 5: Erstellen von Beziehungen
  In dieser Lektion überprüfen Sie die Beziehungen, die beim Importieren von Daten automatisch erstellt wurden. Zudem fügen Sie neue Beziehungen zwischen verschiedenen Tabellen hinzu. Eine Beziehung ist eine Verbindung zwischen zwei Tabellen, die festlegt, wie die Daten in diesen Tabellen korreliert werden sollen. Die Product-Tabelle und die Product Subcategory-Tabelle haben beispielsweise eine Beziehung, die darauf beruht, dass jedes Produkt zu einer Unterkategorie gehört. Weitere Informationen finden Sie unter [Beziehungen &#40;SSAS – tabellarisch&#41;](tabular-models/relationships-ssas-tabular.md).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema ist Teil eines Tutorials zur Tabellenmodellierung, das in der vorgegebenen Reihenfolge durchgeführt werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 3: Umbenennen von Spalten](rename-columns.md).  
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>Überprüfen vorhandener Beziehungen und Hinzufügen neuer Beziehungen  
 Wenn Sie Daten mithilfe des Tabellenimport-Assistenten importiert haben, wurden sieben Tabellen aus der AdventureWorksDW-Datenbank importiert. Im Allgemeinen werden vorhandene Beziehungen automatisch zusammen mit den Daten importiert, wenn Sie Daten von einer relationalen Quelle importieren. Bevor Sie jedoch mit der Erstellung Ihres Modells fortfahren, sollten Sie überprüfen, ob die Beziehungen zwischen den Tabellen korrekt sind. In diesem Tutorial erlernen Sie auch das Hinzufügen drei neuer Beziehungen.  
  
#### <a name="to-review-existing-relationships"></a>Zum Überprüfen vorhandener Beziehungen, gehen Sie folgendermaßen vor:  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** , zeigen Sie auf **Modellansicht**, und klicken Sie anschließend auf **Diagrammsicht**.  
  
     Der Modell-Designer wird jetzt in der Diagrammansicht angezeigt, in der alle importierten Tabellen mit dazwischen angeordneten Linien in einem Grafikformat dargestellt werden. Die Linien zwischen den Tabellen stellen die Beziehungen dar, die beim Importieren der Daten automatisch erstellt wurden.  
  
     Verwenden Sie die Steuerelemente der Miniaturkarte oben rechts im Modell-Designer, um die Sicht so anzupassen, dass so viele Tabellen wie möglich berücksichtigt werden. Sie können die Tabellen auch per Drag & Drop an andere Positionen verschieben, sie näher zusammenbringen oder in einer bestimmten Reihenfolge anordnen. Das Verschieben der Tabellen hat keinen Einfluss auf die bestehenden Beziehungen zwischen den Tabellen. Zum Anzeigen aller Spalten einer bestimmten Tabelle, klicken Sie auf eine Ecke der Tabelle und ziehen sie bis zur gewünschten Größe.  
  
2.  Klicken Sie zwischen der Tabelle **Customer** und der Tabelle **Geography** auf die durchgezogene Linie. Die durchgezogene Linie zwischen diesen beiden Tabellen zeigt an, dass die Beziehung aktiv ist, d.h. dass sie bei der Berechnung von DAX-Formeln standardmäßig verwendet wird.  
  
     Beachten Sie, dass die Spalte **Geography Id** in der Tabelle **Customer** und die Spalte **Geography Id** in der Tabelle **Geography** jetzt jeweils innerhalb eines Felds angezeigt werden. Dadurch wird verdeutlicht, dass diese Spalten in der Beziehung verwendet werden. Die Eigenschaften der Beziehung werden jetzt auch im Fenster **Eigenschaften** angezeigt.  
  
    > [!TIP]  
    >  Zusätzlich zum Verwenden des Modell-Designers in der Diagramm Sicht können Sie auch das Dialogfeld **Beziehungen verwalten** verwenden, um die Beziehungen zwischen allen Tabellen in einem Tabellenformat anzuzeigen. Klicken Sie im Menü **Tabelle** auf **Beziehungen verwalten**. Das Dialogfeld **Beziehungen verwalten** zeigt die Beziehungen an, die beim Importieren von Daten automatisch erstellt wurden.  
  
3.  Verwenden Sie den Modell-Designer in der Diagramm Sicht oder das Dialogfeld **Beziehungen verwalten** , um zu überprüfen, ob die folgenden Beziehungen erstellt wurden, als jede der Tabellen aus der AdventureWorksDW-Datenbank importiert wurde:  
  
    |Aktiv|Tabelle|Verknüpfte Nachschlagetabelle|  
    |------------|-----------|--------------------------|  
    |Ja|**Customer [Geography Id]**|**Geography [Geography Id]**|  
    |Ja|**Product [Product Subcategory Id]**|**Product Subcategory [Product Subcategory Id]**|  
    |Ja|**Product Subcategory [Product Category Id]**|**Product Category [Product Category Id]**|  
    |Ja|**Internet Sales [Customer Id]**|**Customer [Customer Id]**|  
    |Ja|**Internet Sales [Product Id]**|**Product [Product Id]**|  
  
 Fehlt eine der in der oben stehenden Tabelle angegebenen Beziehungen, stellen Sie sicher, dass das Modell die folgenden Tabellen beinhaltet: Customer, Date, Geography, Product, Product Category, Product Subcategory und Internet Sales. Werden Tabellen aus derselben Datenquellenverbindung zu unterschiedlichen Zeitpunkten importiert, werden zwischen diesen Tabellen keine Beziehungen erstellt. Diese müssen anschließend manuell erstellt werden.  
  
 In einigen Fällen möchten Sie möglicherweise zusätzliche Beziehungen zwischen den Tabellen im Modell erstellen, um eine bestimmte Geschäftslogik zu unterstützen. Für dieses Lernprogramm müssen Sie drei zusätzliche Beziehungen zwischen der Internet Sales-Tabelle und der Date-Tabelle erstellen.  
  
#### <a name="to-add-new-relationships-between-tables"></a>Zum Hinzufügen neuer Beziehungen zwischen Tabellen, gehen Sie folgendermaßen vor:  
  
1.  Klicken Sie im Modell-Designer in der Tabelle **Internet Sales** auf die Spalte **Order Date** , und halten Sie sie gedrückt. Verschieben Sie die Spalte anschließend mit dem Cursor per Drag &amp; Drop in die Spalte **Date** der Tabelle **Date** .  
  
     Eine durchgezogene Linie wird angezeigt. Diese bedeutet, dass Sie eine aktive Beziehung zwischen der Spalte **Order Date** in der Tabelle **Internet Sales** und der Spalte **Date** in der Tabelle **Date** erstellt haben.  
  
    > [!NOTE]  
    >  Bei der Erstellung von Beziehungen wird die Reihenfolge zwischen der primären Tabelle und der zugehörigen Nachschlagetabelle automatisch entsprechend angepasst.  
  
2.  Klicken Sie in der Tabelle **Internet Sales** auf die Spalte **Due Date** , und halten Sie sie gedrückt. Verschieben Sie die Spalte anschließend mit dem Cursor per Drag &amp; Drop in die Spalte **Date** der Tabelle **Date** .  
  
     Eine gepunktete Linie wird angezeigt. Diese bedeutet, dass Sie eine inaktive Beziehung zwischen der Spalte **Due Date** in der Tabelle **Internet Sales** und der Spalte **Date** in der Tabelle **Date** erstellt haben. Zwischen Tabellen können mehrere Beziehungen bestehen, doch nur eine Beziehung kann jeweils aktiv sein.  
  
3.  Erstellen Sie abschließend eine weitere Beziehung. Klicken Sie in der Tabelle **Internet Sales** auf die Spalte **Ship Date** , und halten Sie die Auswahl gedrückt. Verschieben Sie die Auswahl anschließend mit dem Cursor per Drag &amp; Drop in die Spalte **Date** der Tabelle **Date** .  
  
     Eine gepunktete Linie wird angezeigt. Diese bedeutet, dass Sie eine inaktive Beziehung zwischen der Spalte **Ship Date** in der Tabelle **Internet Sales** und der Spalte **Date** in der Tabelle **Date** erstellt haben.  
  
## <a name="next-step"></a>Nächster Schritt  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 6: Erstellen von berechneten Spalten](lesson-5-create-calculated-columns.md).  
  
  
