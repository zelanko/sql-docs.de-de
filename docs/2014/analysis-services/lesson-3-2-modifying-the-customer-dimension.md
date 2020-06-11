---
title: Ändern der Customer-Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5b5aed99-1760-4bc7-b248-52ecb0b97ebc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 63cfc1fc4b5bcc3e1c468bbb456a660587757f2b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543442"
---
# <a name="modifying-the-customer-dimension"></a>Ändern der Customer-Dimension
  Es gibt viele verschiedene Möglichkeiten zum Verbessern der Benutzerfreundlichkeit und Funktionalität der Dimensionen in einem Cube. Mit den Schritten in diesem Thema ändern Sie die Customer-Dimension.  
  
## <a name="renaming-attributes"></a>Umbenennen von Attributen  
 Sie können Attributnamen auf der Registerkarte **Dimensionsstruktur** des Dimensions-Designers ändern.  
  
#### <a name="to-rename-an-attribute"></a>So benennen Sie ein Attribut um  
  
1.  Wechseln Sie in **zum** Dimensions-Designer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]für die Customer-Dimension. Doppelklicken Sie dazu auf die Dimension **Customer** im Knoten **Dimensionen** des Projektmappen-Explorers.  
  
2.  Klicken Sie im Bereich **Attribute** mit der rechten Maustaste auf **English Country Region Name**, und klicken Sie anschließend auf **Umbenennen**. Ändern Sie den Namen des Attributs in `Country-Region` .  
  
3.  Ändern Sie die Namen der folgenden Attribute auf die gleiche Art:  
  
    -   **English Education** -Attribut: ändern in`Education`  
  
    -   **English-Beruf** -Attribut-ändern in`Occupation`  
  
    -   **State Province Name** -Attribut-ändern in`State-Province`  
  
4.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="creating-a-hierarchy"></a>Erstellen einer Hierarchie  
 Sie können eine neue Hierarchie erstellen, indem Sie ein Attribut aus dem Bereich **Attribute** in den Bereich **Hierarchien** ziehen.  
  
#### <a name="to-create-a-hierarchy"></a>So erstellen Sie eine Hierarchie  
  
1.  Ziehen Sie das- `Country-Region` Attribut aus dem Bereich **Attribute** in den Bereich **Hierarchien** .  
  
2.  Ziehen Sie das- `State-Province` Attribut aus dem Bereich **Attribute** in die Zelle des Bereichs **\<new level>** **Hierarchien** unterhalb der `Country-Region` Ebene.  
  
3.  Ziehen Sie das **City** -Attribut aus dem Bereich **Attribute** in die Zelle des Bereichs **\<new level>** **Hierarchien** unterhalb der `State-Province` Ebene.  
  
4.  Klicken Sie im Bereich **Hierarchien** der Registerkarte **Dimensions Struktur** mit der rechten Maustaste auf die Titelleiste der **Hierarchie** Hierarchie, wählen Sie **Umbenennen**aus, und geben Sie dann ein `Customer Geography` .  
  
     Der Name der Hierarchie lautet jetzt `Customer Geography` .  
  
5.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="adding-a-named-calculation"></a>Hinzufügen einer benannten Berechnung  
 Sie können eine benannte Berechnung, bei der es sich um einen SQL-Ausdruck handelt, der als eine berechnete Spalte dargestellt wird, zu einer Tabelle in einer Datenquellensicht hinzufügen. Der Ausdruck wird als Spalte in der Tabelle angezeigt und verhält sich auch so. Mithilfe von benannten Ausdrücken können Sie das relationale Schema von vorhandenen Tabellen in einer Datenquellensicht erweitern, ohne die Tabelle in der zugrunde liegenden Datenquelle zu ändern. Weitere Informationen finden Sie unter [Definieren von benannten Berechnungen in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
#### <a name="to-add-a-named-calculation"></a>So fügen Sie eine benannte Berechnung hinzu  
  
1.  Öffnen Sie die ** [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** -Datenquellen Sicht, indem Sie in Projektmappen-Explorer im Ordner **Datenquellen Sichten** darauf doppelklicken.  
  
2.  Klicken Sie mit der rechten Maustaste im Bereich **Tabellen** auf der linken Seite auf **Customer**und anschließend auf **Neue benannte Berechnung**.  
  
3.  Geben Sie im Dialogfeld **benannte Berechnung erstellen** `FullName` im Feld **Spaltenname** ein, und geben Sie dann die folgende `CASE` Anweisung in das Feld **Ausdruck** ein (Sie können die Anweisung auch kopieren und Einfügen):  
  
    ```  
    CASE  
       WHEN MiddleName IS NULL THEN  
       FirstName + ' ' + LastName  
       ELSE  
       FirstName + ' ' + MiddleName + ' ' + LastName  
    END  
    ```  
  
     Die `CASE` -Anweisung verkettet die Spalten **FirstName**, **MiddleName**und **LastName** in eine einzelne Spalte, die Sie in der Customer-Dimension als angezeigten Namen für das **Customer** -Attribut verwenden werden.  
  
4.  Klicken Sie auf **OK**, und erweitern Sie **Customer** im **Tabellen** -Bereich.  
  
     Die `FullName` benannte Berechnung wird in der Liste der Spalten in der Customer-Tabelle mit einem Symbol angezeigt, das angibt, dass es sich um eine benannte Berechnung handelt.  
  
5.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
6.  Klicken Sie im Bereich **Tabellen** mit der rechten Maustaste auf **Customer**, und klicken Sie anschließend auf **Daten durchsuchen**.  
  
7.  Überprüfen Sie die letzte Spalte in der Sicht **Customer-Tabelle durchsuchen** .  
  
     Beachten Sie, dass die `FullName` Spalte in der Datenquellen Sicht angezeigt wird, wobei Daten aus verschiedenen Spalten aus der zugrunde liegenden Datenquelle und ohne Änderung der ursprünglichen Datenquelle ordnungsgemäß verkettet werden.  
  
8.  Schließen Sie die Registerkarte **Customer-Tabelle durchsuchen** .  
  
## <a name="using-the-named-calculation-for-member-names"></a>Verwenden der benannten Berechnung für Elementnamen  
 Nachdem Sie eine benannte Berechnung in der Datenquellensicht erstellt haben, können Sie sie als Eigenschaft eines Attributs verwenden.  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a>So verwenden Sie die benannte Berechnung für Elementnamen  
  
1.  Wechseln Sie zum Dimensions-Designer für die Customer-Dimension.  
  
2.  Klicken Sie im Bereich **Attribute** der Registerkarte **Dimensionsstruktur** auf das **Customer Key** -Attribut.  
  
3.  Öffnen Sie das Fenster Eigenschaften, und klicken Sie in der Titelleiste auf die Schaltfläche **Automatisch im Hintergrund** , sodass dieses Fenster geöffnet bleibt.  
  
4.  Geben Sie im Eigenschaften Feld **Name den Namen** ein `Full Name` .  
  
5.  Klicken Sie unten auf das Eigenschafts Feld **namecolumzun** und dann auf die Schaltfläche zum Durchsuchen (**...**), um das Dialogfeld **Namensspalte** zu öffnen.  
  
6.  Wählen Sie `FullName` unten in der Liste **Quell Spalte** die Option aus, und klicken Sie dann auf **OK**.  
  
7.  Ziehen Sie auf der Registerkarte Dimensions Struktur das- `Full Name` Attribut aus dem Bereich **Attribute** in die Zelle des Bereichs **\<new level>** **Hierarchien** unterhalb der **City** -Ebene.  
  
8.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="defining-display-folders"></a>Definieren von Anzeigeordnern  
 Sie können Anzeigeordner verwenden, um Benutzer- und Attributhierarchien in Ordnerstrukturen zu gruppieren und so die Benutzerfreundlichkeit zu erhöhen.  
  
#### <a name="to-define-display-folders"></a>So definieren Sie Anzeigeordner  
  
1.  Öffnen Sie die Registerkarte **Dimensionsstruktur** für die Customer-Dimension.  
  
2.  Wählen Sie im Bereich **Attribute** die folgenden Attribute, indem Sie beim Klicken die STRG-Taste gedrückt halten:  
  
    -   **City (Ort)**  
  
    -   `Country-Region`  
  
    -   **Postleitzahl**  
  
    -   `State-Province`  
  
3.  Klicken Sie im Eigenschaftenfenster oben auf das **AttributeHierarchyDisplayFolder** -Eigenschaften Feld (möglicherweise müssen Sie darauf zeigen, um den vollständigen Namen anzuzeigen), und geben Sie dann ein `Location` .  
  
4.  Klicken Sie im Bereich **Hierarchien** `Customer Geography` auf, und wählen Sie dann in der Eigenschaftenfenster auf der rechten Seite `Location` als Wert der **DisplayFolder** -Eigenschaft aus.  
  
5.  Wählen Sie im Bereich **Attribute** die folgenden Attribute, indem Sie beim Klicken die STRG-Taste gedrückt halten:  
  
    -   **Commute Distance**  
  
    -   `Education`  
  
    -   **Geschlecht**  
  
    -   **House Owner Flag**  
  
    -   **Marital Status**  
  
    -   **Number Cars Owned**  
  
    -   **Anzahl der Kinder zu Hause**  
  
    -   `Occupation`  
  
    -   **Total Children**  
  
    -   **Yearly Income**  
  
6.  Klicken Sie in der Eigenschaftenfenster oben auf das Eigenschaften Feld **AttributeHierarchyDisplayFolder** , und geben Sie dann ein `Demographic` .  
  
7.  Wählen Sie im Bereich **Attribute** die folgenden Attribute, indem Sie beim Klicken die STRG-Taste gedrückt halten:  
  
    -   **E-Mail-Adresse**  
  
    -   **Phone**  
  
8.  Klicken Sie im Eigenschaftenfenster auf das **AttributeHierarchyDisplayFolder** -Eigenschaften Feld, und geben Sie ein `Contacts` .  
  
9. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="defining-composite-keycolumns"></a>Definieren von zusammengesetzten KeyColumns  
 Die Eigenschaft **KeyColumns** enthält die Spalte bzw. Spalten, die den Schlüssel für das Attribut darstellen. In dieser Lektion erstellen Sie einen zusammengesetzten Schlüssel für das **City** -Attribut und das- `State-Province` Attribut. Zusammengesetzte Schlüssel können hilfreich sein, wenn Sie ein Attribut eindeutig identifizieren müssen. Wenn Sie z. b. später in diesem Tutorial Attribut Beziehungen definieren, muss ein **City** -Attribut ein-Attribut eindeutig identifizieren `State-Province` . Es können jedoch mehrere Orte mit dem gleichen Namen in verschiedenen Staaten geben. Aus diesem Grund erstellen Sie für das **City** -Attribut einen zusammengesetzten Schlüssel, der sich aus den Spalten **StateProvinceName** und **City** zusammensetzt. Weitere Informationen finden Sie unter [Ändern der KeyColumn-Eigenschaft eines Attributs](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).  
  
#### <a name="to-define-composite-keycolumns-for-the-city-attribute"></a>So definieren Sie zusammengesetzte KeyColumns für das City-Attribut  
  
1.  Öffnen Sie die Registerkarte **Dimensionsstruktur** für die Customer-Dimension.  
  
2.  Klicken Sie im Bereich **Attribute** auf das **City** -Attribut.  
  
3.  Klicken Sie im Fenster **Eigenschaften** weiter unten auf das Feld **KeyColumns** und anschließend auf die Schaltfläche zum Durchsuchen (**...**).  
  
4.  Wählen Sie im Dialogfeld **Schlüsselspalten** die Spalte **StateProvinceName** in der Liste **Verfügbare Spalten**aus, und klicken Sie anschließend auf die Schaltfläche **>** .  
  
     Die Spalten **City** und **StateProvinceName** werden jetzt in der Liste **Schlüsselspalten** angezeigt.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Um die **NameColumn** -Eigenschaft des **City** -Attributs festzulegen, klicken Sie in das Feld **NameColumn** des Fensters „Eigenschaften“ und anschließend auf die Schaltfläche zum Durchsuchen (**...**).  
  
7.  Wählen Sie im Dialogfeld **Namensspalte** in der Liste **Quellspalte** die Option **City**aus, und klicken Sie anschließend auf **OK**.  
  
8.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
#### <a name="to-define-composite-keycolumns-for-the-state-province-attribute"></a>So definieren Sie zusammengesetzte KeyColumns für das State-Province-Attribut  
  
1.  Stellen Sie sicher, dass die Registerkarte **Dimensionsstruktur** für die Customer-Dimension geöffnet ist.  
  
2.  Klicken Sie im Bereich **Attribute** auf das `State-Province` Attribut.  
  
3.  Klicken Sie im Fenster **Eigenschaften** auf das Feld **KeyColumns** und anschließend auf die Schaltfläche zum Durchsuchen (**...**).  
  
4.  Wählen Sie im Dialogfeld **Schlüsselspalten** die Spalte **EnglishCountryRegionName** in der Liste **Verfügbare Spalten**aus, und klicken Sie anschließend auf die Schaltfläche **>** .  
  
     Die Spalten **EnglishCountryRegionName** und **StateProvinceName** werden jetzt in der Liste **Schlüsselspalten** angezeigt.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Um die **namecolumzun** -Eigenschaft des `State-Province` Attributs festzulegen, klicken Sie im Eigenschaftenfenster auf das Feld **namecolenn** und dann auf die Schaltfläche zum Durchsuchen (**..**.).  
  
7.  Wählen Sie im Dialogfeld **Namensspalte** in der Liste **Quellspalte** die Option **StateProvinceName**aus, und klicken Sie anschließend auf **OK**.  
  
8.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="defining-attribute-relationships"></a>Definieren von Attributbeziehungen  
 Sofern die zugrunde liegenden Daten dies unterstützen, sollten Sie auch Attributbeziehungen zwischen Attributen definieren. Durch Definieren von Attributbeziehungen wird die Dimensions-, Partitions- und Abfrageverarbeitung beschleunigt. Weitere Informationen finden Sie unter [Definieren von Attributbeziehungen](multidimensional-models/attribute-relationships-define.md) und [Attributbeziehungen](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
#### <a name="to-define-attribute-relationships"></a>So definieren Sie Attributbeziehungen  
  
1.  Klicken Sie im **Dimensions-Designer** für die Customer-Dimension auf die Registerkarte **Attribut Beziehungen** . Möglicherweise müssen Sie warten.  
  
2.  Klicken Sie im Diagramm mit der rechten Maustaste auf das **City** -Attribut, und wählen Sie anschließend **Neue Attributbeziehung**aus.  
  
3.  Im Dialogfeld **Attributbeziehung erstellen** ist das **Quellattribut****City**. Legen Sie das **zugehörige Attribut** auf fest `State-Province` .  
  
4.  Stellen Sie in der Liste **Beziehungstyp** den Beziehungstyp auf **Fest**ein.  
  
     Der Beziehungstyp ist **Fest** , da sich Beziehungen zwischen den Elementen nicht im Laufe der Zeit ändern. Ein Ort wird beispielsweise normalerweise nicht Teil eines anderen Bundeslands oder Kantons.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Klicken Sie im Diagramm mit der rechten Maustaste auf das `State-Province` Attribut, und wählen Sie dann **neue Attribut Beziehung**aus.  
  
7.  Im Dialogfeld **Attribut Beziehung erstellen** ist das **Quell Attribut** `State-Province` . Legen Sie das **zugehörige Attribut** auf fest `Country-Region` .  
  
8.  Stellen Sie in der Liste **Beziehungstyp** den Beziehungstyp auf **Fest**ein.  
  
9. Klicken Sie auf **OK**.  
  
10. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="deploying-changes-processing-the-objects-and-viewing-the-changes"></a>Bereitstellen von Änderungen, Verarbeiten der Objekte und Anzeigen der Änderungen  
 Nach dem Ändern von Attributen und Hierarchien müssen Sie die Änderungen bereitstellen und die verknüpften Objekte neu verarbeiten, bevor Sie die Änderungen anzeigen können.  
  
#### <a name="to-deploy-the-changes-process-the-objects-and-view-the-changes"></a>So stellen Sie die Änderungen bereit, verarbeiten die Objekte und zeigen die Änderungen an  
  
1.  Klicken Sie im Menü **Erstellen** von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf **Analysis Services Tutorial bereitstellen**.  
  
2.  Nachdem die Meldung angezeigt wird, dass die **Bereitstellung erfolgreich abgeschlossen** wurde, klicken Sie auf die Registerkarte **Browser** im Dimensions-Designer für die Customer-Dimension, und klicken Sie links in der Symbolleiste auf die Schaltfläche zum Wiederherstellen der Verbindung.  
  
3.  Vergewissern Sie sich, dass `Customer Geography` in der Liste **Hierarchie** ausgewählt ist, und erweitern Sie dann im Browserbereich **alle**, **Australien**, **New South Wales**und anschließend **Coffs Harbour**.  
  
     Im Browser werden die Kunden in dem Ort angezeigt.  
  
4.  Wechseln Sie zum **Cube-Designer** , um den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial Cube anzuzeigen. Doppelklicken Sie hierzu auf den **Analysis Services Tutorial** -Cube im **Cubes** -Knoten **Projektmappen-Explorer**.  
  
5.  Klicken Sie auf die Registerkarte **Browser** und anschließend in der Symbolleiste des Designers auf die Schaltfläche zum Wiederherstellen der Verbindung.  
  
6.  Erweitern Sie im Bereich **Measuregruppe** den Eintrag **Customer**.  
  
     Beachten Sie, dass anstelle einer langen Liste von Attributen nur die Anzeigeordner und Attribute, die keine Anzeigeordnerwerte aufweisen, unterhalb von Customer angezeigt werden.  
  
7.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Ändern der Product-Dimension](lesson-3-3-modifying-the-product-dimension.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions Attribut-Eigenschaften Referenz](multidimensional-models/dimension-attribute-properties-reference.md)   
 [Entfernen eines Attributs aus einer Dimension](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md)   
 [Umbenennen eines Attributs](multidimensional-models/attribute-properties-rename-an-attribute.md)   
 [Definieren von benannten Berechnungen in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
