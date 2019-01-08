---
title: Ändern der Product-Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 430ac56191fcfc2c601c50f9f31de128d5d58368
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52523330"
---
# <a name="modifying-the-product-dimension"></a>Ändern der Product-Dimension
  In den Aufgaben in diesem Thema verwenden Sie eine benannte Berechnung, um aussagekräftigere Namen für Produktlinien zur Verfügung zu stellen, definieren eine Hierarchie in der Product-Dimension, und geben den (All) -Elementnamen für die Hierarchie an. Außerdem gruppieren Sie Attribute in Anzeigeordner.  
  
## <a name="adding-a-named-calculation"></a>Hinzufügen einer benannten Berechnung  
 Sie können einer Tabelle in einer Datenquellensicht eine benannte Berechnung hinzufügen. In der folgenden Aufgabe erstellen Sie eine benannte Berechnung, die den vollständigen Produktliniennamen anzeigt.  
  
#### <a name="to-add-a-named-calculation"></a>So fügen Sie eine benannte Berechnung hinzu  
  
1.  Um die **Adventure Works DW 2012** -Datenquellensicht zu öffnen, doppelklicken Sie im Projektmappen-Explorer im Ordner **Datenquellensichten** auf **Adventure Works DW 2012** .  
  
2.  Klicken Sie unten im Diagrammbereich mit der rechten Maustaste auf die Tabellenüberschrift **Product** . Klicken Sie anschließend auf **Neue benannte Berechnung**.  
  
3.  In der **benannte Berechnung erstellen** (Dialogfeld), Typ `ProductLineName` in die **Spaltenname** Feld.  
  
4.  Geben Sie in das Feld **Ausdruck** die folgende **CASE** -Anweisung ein (Sie können sie auch kopieren und einfügen):  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
     Diese **CASE** -Anweisung erstellt benutzerfreundliche Namen für jede Produktlinie im Cube.  
  
5.  Klicken Sie auf **OK** zum Erstellen der `ProductLineName` benannte Berechnung. Sie müssen möglicherweise einen Moment warten.  
  
6.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a>Ändern der NameColumn-Eigenschaft eines Attributs  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a>So ändern Sie den Wert der NameColumns-Eigenschaft eines Attributs  
  
1.  Wechseln Sie zum Dimensions-Designer für die Product-Dimension. Doppelklicken Sie dazu auf die **Product** -Dimension im **Dimensionen** -Knoten des Projektmappen-Explorers.  
  
2.  Wählen Sie im Bereich **Attribute** der Registerkarte **Dimensionsstruktur** die Option **Product Line**aus.  
  
3.  Klicken Sie im Eigenschaftenfenster auf der rechten Seite des Bildschirms auf die **NameColumn** Eigenschaftenfeld am unteren Rand des Fensters, und klicken Sie dann auf die Schaltfläche zum Durchsuchen (**...** ) die Schaltfläche, um die **Spalte "Name"** Dialogfeld. (Sie müssen ggf. auf die Registerkarte **Eigenschaften** auf der rechten Seite vom Bildschirm klicken, um das Eigenschaftenfenster zu öffnen).  
  
4.  Wählen Sie `ProductLineName` am unteren Rand der **Quellspalte** aus, und klicken Sie dann auf **OK**.  
  
     Das Feld „NameColumn“ enthält jetzt den Text **Product.ProductLineName (WChar)**. Die Elemente der Attributhierarchie **Product Line** zeigen nun den vollständigen Namen der Produktlinie anstelle eines abgekürzten Produktliniennamens an.  
  
5.  Wählen Sie im Bereich **Attribute** der Registerkarte **Dimensionsstruktur** die Option **Product Key**aus.  
  
6.  Klicken Sie im Eigenschaftenfenster auf die **NameColumn** Eigenschaft ein, und klicken Sie dann auf den Auslassungspunkten (**...** ) die Schaltfläche, um die **Spalte "Name"** Dialogfeld.  
  
7.  Wählen Sie **EnglishProductName** in der Liste **Quellspalte** aus, und klicken Sie auf **OK**.  
  
     Das Feld "NameColumn" enthält jetzt den Text **Product.EnglishProductName (WChar)**.  
  
8.  Klicken Sie im Eigenschaftenfenster einen Bildlauf nach oben, klicken Sie auf die **Namen** Eigenschaftenfeld, und geben Sie dann `Product Name`.  
  
## <a name="creating-a-hierarchy"></a>Erstellen einer Hierarchie  
  
#### <a name="to-create-a-hierarchy"></a>So erstellen Sie eine Hierarchie  
  
1.  Ziehen Sie das **Product Line** -Attribut vom Bereich **Attribute** in den Bereich **Hierarchien** .  
  
2.  Ziehen Sie die **Modellname** -Attribut aus der **Attribute** -Bereich in die  **\<ungeahnte >** Zelle der **Hierarchien** unterhalb der **Product Line** Ebene.  
  
3.  Ziehen Sie die `Product Name` -Attribut aus der **Attribute** -Bereich in die  **\<neue Ebene >** Zelle die **Hierarchien** Bereich unterhalb der  **Modellname** Ebene. (Sie haben im vorherigen Abschnitt Product Key in Product Name umbenannt.)  
  
4.  In der **Hierarchien** im Bereich der **Dimensionsstruktur** Registerkarte der rechten Maustaste auf der Titelleiste des Fensters der **Hierarchie** Hierarchie, klicken Sie auf **umbenennen** , und geben Sie dann `Product Model Lines`.  
  
     Der Name der Hierarchie lautet jetzt `Product Model Lines`.  
  
5.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="specifying-folder-names-and-all-member-names"></a>Angeben von Ordnernamen und Namen für alle Elemente  
  
#### <a name="to-specify-the-folder-and-member-names"></a>So geben Sie die Ordner- und Elementnamen an  
  
1.  Wählen Sie im Bereich **Attribute** die folgenden Attribute, indem Sie beim Klicken die STRG-Taste gedrückt halten:  
  
    -   **Klasse**  
  
    -   **Farbe**  
  
    -   **Days To Manufacture**  
  
    -   **Reorder Point**  
  
    -   **Safety Stock Level**  
  
    -   **Größe**  
  
    -   **Size Range**  
  
    -   **Stil**  
  
    -   **Weight**  
  
2.  In der **AttributeHierarchyDisplayFolder** Eigenschaftenfeld im Fenster Eigenschaften den Typ `Stocking`.  
  
     Sie haben diese Attribute jetzt in einen einzigen Anzeigeordner gruppiert.  
  
3.  Wählen Sie im Bereich **Attribute** die folgenden Attribute aus:  
  
    -   **Dealer Price**  
  
    -   **List Price**  
  
    -   **Standard Cost**  
  
4.  In der **AttributeHierarchyDisplayFolder** eigenschaftenzelle im Fenster Eigenschaften den Typ `Financial`.  
  
     Sie haben diese Attribute jetzt in einen zweiten Anzeigeordner gruppiert.  
  
5.  Wählen Sie im Bereich **Attribute** die folgenden Attribute aus:  
  
    -   **End Date**  
  
    -   **Startdatum**  
  
    -   **Status**  
  
6.  In der **AttributeHierarchyDisplayFolder** eigenschaftenzelle im Fenster Eigenschaften den Typ `History`.  
  
     Sie haben diese Attribute jetzt in einen dritten Anzeigeordner gruppiert.  
  
7.  Wählen Sie die `Product Model Lines` Hierarchie in der **Hierarchien** Bereich, und ändern Sie dann die **AllMemberName** Eigenschaft im Eigenschaftenfenster zu `All Products`.  
  
8.  Klicken Sie auf einen offenen Bereich, der die **Hierarchien** Bereich, und ändern Sie dann die **AttributeAllMemberName** Eigenschaft am oberen Rand des Fensters "Eigenschaften" auf `All Products`.  
  
     Durch das Anklicken eines offenen Bereichs können Sie Eigenschaften der Produktdimension selbst ändern. Sie können auch auf **Product** am oberen Rand der Attributliste im Bereich **Attribute** klicken.  
  
9. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="defining-attribute-relationships"></a>Definieren von Attributbeziehungen  
 Sofern die zugrunde liegenden Daten dies unterstützen, sollten Sie auch Attributbeziehungen zwischen Attributen definieren. Durch Definieren von Attributbeziehungen wird die Dimensions-, Partitions- und Abfrageverarbeitung beschleunigt. Weitere Informationen finden Sie unter [Definieren von Attributbeziehungen](multidimensional-models/attribute-relationships-define.md) und [Attributbeziehungen](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
#### <a name="to-define-attribute-relationships"></a>So definieren Sie Attributbeziehungen  
  
1.  Klicken Sie im **Dimensions-Designer** für die Product-Dimension auf die Registerkarte **Attributbeziehungen** .  
  
2.  Klicken Sie im Diagramm mit der rechten Maustaste auf das **Model Name** -Attribut und anschließend auf **Neue Attributbeziehung**.  
  
3.  Im Dialogfeld **Attributbeziehung erstellen** lautet das **Quellattribut** **Model Name**. Legen Sie für **Verknüpftes Attribut** die Einstellung **Produktgruppe**fest.  
  
     Belassen Sie in der Liste **Beziehungstyp** den Beziehungstyp auf **Flexibel** , da sich Beziehungen zwischen den Elementen im Laufe der Zeit ändern können. So könnte ein Produktmodell beispielsweise in eine andere Produktlinie verschoben werden.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="reviewing-product-dimension-changes"></a>Überprüfen von Produktdimensionsänderungen  
  
#### <a name="to-review-the-product-dimension-changes"></a>So überprüfen Sie die Produktdimensionsänderungen  
  
1.  Klicken Sie im Menü **Erstellen** von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf **Analysis Services Tutorial bereitstellen**.  
  
2.  Nachdem die Meldung **Bereitstellung erfolgreich abgeschlossen** angezeigt wird, klicken Sie auf die Registerkarte **Browser** im **Dimensions-Designer** für die **Product** -Dimension und anschließend auf der Symbolleiste auf die Schaltfläche zum Wiederherstellen der Verbindung.  
  
3.  Überprüfen Sie, ob `Product Model Lines` ausgewählt ist, der **Hierarchie** aus, und erweitern Sie dann `All Products`.  
  
     Beachten Sie, dass der Name des der **alle** Element angezeigt wird, als `All Products`. Dies ist, da Sie geändert haben die **AllMemberName** -Eigenschaft für die Hierarchie `All Products` weiter oben in der Lektion. Auch verfügen die Elemente der **Product Line** -Ebene jetzt über benutzerfreundliche Namen anstelle von Abkürzungen aus einem Buchstaben.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Ändern der Date-Dimension](lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von benannten Berechnungen in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)   
 [Erstellen von benutzerdefinierten Hierarchien](multidimensional-models/user-defined-hierarchies-create.md)   
 [Konfigurieren der Ebene &#40;Alle&#41; für Attributhierarchien](multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
