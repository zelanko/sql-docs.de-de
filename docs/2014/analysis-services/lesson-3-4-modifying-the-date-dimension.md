---
title: Ändern der Date-Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4689d780-4bf6-4cf8-8fde-eb3f15dd668a
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 03e0f8938c5a35f917c921248d4f3913ae1667f7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216090"
---
# <a name="modifying-the-date-dimension"></a>Ändern der Date-Dimension
  In den Aufgaben dieses Themas erstellen Sie eine benutzerdefinierte Hierarchie und ändern die Elementnamen, die für die Attribute Date, Month, Calendar Quarter und Calendar Semester angezeigt werden. Außerdem definieren Sie zusammengesetzte Schlüssel für Attribute, steuern die Sortierreihenfolge von Dimensionselementen und definieren Attributbeziehungen.  
  
## <a name="adding-a-named-calculation"></a>Hinzufügen einer benannten Berechnung  
 Sie können eine benannte Berechnung, bei der es sich um einen SQL-Ausdruck handelt, der als eine berechnete Spalte dargestellt wird, zu einer Tabelle in einer Datenquellensicht hinzufügen. Der Ausdruck wird als Spalte in der Tabelle angezeigt und verhält sich auch so. Mithilfe von benannten Berechnungen können Sie das relationale Schema vorhandener Tabellen in einer Datenquellensicht erweitern, ohne die Tabelle in der zugrunde liegenden Datenquelle zu ändern. Weitere Informationen finden Sie unter [Definieren von benannten Berechnungen in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md).  
  
#### <a name="to-add-a-named-calculation"></a>So fügen Sie eine benannte Berechnung hinzu  
  
1.  Um die Datenquellensicht **Adventure Works DW 2012** zu öffnen, doppelklicken Sie im Projektmappen-Explorer im Ordner **Datenquellensichten** auf diese Sicht.  
  
2.  Am unteren Rand der **Tabellen** Bereich mit der rechten Maustaste `Date`, und klicken Sie dann auf **neue benannte Berechnung**.  
  
3.  In der **benannte Berechnung erstellen** (Dialogfeld), Typ `SimpleDate` in die **Spaltenname** , und geben Sie dann oder kopieren und fügen Sie die folgende `DATENAME` -Anweisung in der **Ausdruck**  Feld:  
  
    ```  
    DATENAME(mm, FullDateAlternateKey) + ' ' +  
    DATENAME(dd, FullDateAlternateKey) + ', ' +  
    DATENAME(yy, FullDateAlternateKey)  
    ```  
  
     Mithilfe dieser `DATENAME`-Anweisung werden Jahr-, Monats- und Tageswerte aus der FullDateAlternateKey-Spalte extrahiert. Sie verwenden diese neue Spalte als angezeigten Namen für das FullDateAlternateKey-Attribut.  
  
4.  Klicken Sie auf **OK**, und erweitern Sie dann `Date` in die **Tabellen** Bereich.  
  
     Die `SimpleDate` wird in der Liste der Spalten in der Date-Tabelle mit einem Symbol, der angibt, dass die It ist eine benannte Berechnung.  
  
5.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
6.  In der **Tabellen** Bereich mit der rechten Maustaste `Date`, und klicken Sie dann auf **Stichprobenoptionen**.  
  
7.  Scrollen Sie nach rechts, um die letzte Spalte in der Sicht **Explore Date Table** zu überprüfen.  
  
     Beachten Sie, dass die `SimpleDate` -Spalte in der Datenquellensicht angezeigt wird, wobei Daten aus verschiedenen Spalten aus der zugrunde liegenden Datenquelle ordnungsgemäß ohne Änderung der ursprünglichen Datenquelle verkettet.  
  
8.  Schließen Sie die Sicht **Explore Date Table** .  
  
## <a name="using-the-named-calculation-for-member-names"></a>Verwenden der benannten Berechnung für Elementnamen  
 Nachdem Sie eine benannte Berechnung in der Datenquellensicht erstellt haben, können Sie diese als Eigenschaft eines Attributs verwenden.  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a>So verwenden Sie die benannte Berechnung für Elementnamen  
  
1.  Öffnen Sie den **Dimensions-Designer** für die Date-Dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Zu diesem Zweck doppelklicken Sie auf die `Date` -dimension in der **Dimensionen** Knoten **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Bereich **Attribute** der Registerkarte **Dimensionsstruktur** auf das **Date Key** -Attribut.  
  
3.  Wenn das Eigenschaftenfenster nicht geöffnet ist, öffnen Sie es, und klicken Sie in der Titelleiste auf die Schaltfläche **Automatisch im Hintergrund** , damit es geöffnet bleibt.  
  
4.  Klicken Sie weiter unten im Fenster auf das Eigenschaftenfeld **NameColumn** und anschließend auf die Schaltfläche mit den Auslassungspunkten (**…**), um das Dialogfeld **Namensspalte** zu öffnen.  
  
5.  Wählen Sie `SimpleDate` am unteren Rand der **Quellspalte** aus, und klicken Sie dann auf **OK**.  
  
6.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="creating-a-hierarchy"></a>Erstellen einer Hierarchie  
 Sie können eine neue Hierarchie erstellen, indem Sie ein Attribut aus dem Bereich **Attribute** in den Bereich **Hierarchien** ziehen.  
  
#### <a name="to-create-a-hierarchy"></a>So erstellen Sie eine Hierarchie  
  
1.  In **Dimensionsstruktur** Registerkarte des Dimensions-Designers für die `Date` dimension, ziehen Sie die **Kalenderjahr** -Attribut aus der **Attribute** -Bereich in die **Hierarchien** Bereich.  
  
2.  Ziehen Sie die **Calendar Semester** -Attribut aus der **Attribute** -Bereich in die  **\<neue Ebene >** Zelle die **Hierarchien**unterhalb der **Kalenderjahr** Ebene.  
  
3.  Ziehen Sie die **Calendar Quarter** -Attribut aus der **Attribute** -Bereich in die  **\<neue Ebene >** Zelle die **Hierarchien**unterhalb der **Calendar Semester** Ebene.  
  
4.  Ziehen Sie die **English Month Name** -Attribut aus der **Attribute** -Bereich in die  **\<neue Ebene >** Zelle die **Hierarchien**unterhalb der **Calendar Quarter** Ebene.  
  
5.  Ziehen Sie die **Date Key** -Attribut aus der **Attribute** -Bereich in die  **\<neue Ebene >** Zelle die **Hierarchien** Bereich , darunter die **English Month Name** Ebene.  
  
6.  In der **Hierarchien** Bereich mit der rechten Maustaste in der Titelleiste des Fensters der **Hierarchie** Hierarchie, klicken Sie auf **umbenennen**, und geben Sie dann `Calendar Date`.  
  
7.  Mithilfe der im Kontextmenü mit der rechten Maustaste in die `Calendar Date` Hierarchie Umbenennen der **English Month Name** auf `Calendar Month`, und benennen Sie die **Date Key** auf `Date`.  
  
8.  Löschen Sie das **Full Date Alternate Key** -Attribut aus dem Bereich **Attribute** , da Sie es nicht verwenden. Klicken Sie im Bestätigungsfenster **Objekte löschen** auf **OK** .  
  
9. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="defining-attribute-relationships"></a>Definieren von Attributbeziehungen  
 Sofern die zugrunde liegenden Daten dies unterstützen, sollten Sie auch Attributbeziehungen zwischen Attributen definieren. Durch Definieren von Attributbeziehungen wird die Dimensions-, Partitions- und Abfrageverarbeitung beschleunigt.  
  
#### <a name="to-define-attribute-relationships"></a>So definieren Sie Attributbeziehungen  
  
1.  In der **Dimensions-Designer** für die `Date` dimension, klicken Sie auf die **Attributbeziehungen** Registerkarte.  
  
2.  Klicken Sie im Diagramm mit der rechten Maustaste auf das **English Month Name** -Attribut, und klicken Sie auf **Neue Attributbeziehung**.  
  
3.  Im Dialogfeld **Attributbeziehung erstellen** lautet das **Quellattribut** **English Month Name**. Legen Sie den Wert für **Verknüpftes Attribut** auf **Calendar Quarter**fest.  
  
4.  Stellen Sie in der Liste **Beziehungstyp** den Beziehungstyp auf **Fest** ein.  
  
     Der Beziehungstyp ist **Fest** , da sich Beziehungen zwischen den Elementen nicht im Laufe der Zeit ändern.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Klicken Sie im Diagramm mit der rechten Maustaste auf das **Calendar Quarter** -Attribut, und klicken Sie auf **Neue Attributbeziehung**.  
  
7.  Im Dialogfeld **Attributbeziehung erstellen** lautet das **Quellattribut** **Calendar Quarter**. Legen Sie den Wert für **Verknüpftes Attribut** auf **Calendar Semester**fest.  
  
8.  Stellen Sie in der Liste **Beziehungstyp** den Beziehungstyp auf **Fest**ein.  
  
9. Klicken Sie auf **OK**.  
  
10. Klicken Sie im Diagramm mit der rechten Maustaste auf das **Calendar Semester** -Attribut, und klicken Sie auf **Neue Attributbeziehung**.  
  
11. Im Dialogfeld **Attributbeziehung erstellen** lautet das **Quellattribut** **Calendar Semester**. Legen Sie den Wert für **Verknüpftes Attribut** auf **Calendar Year**fest.  
  
12. Stellen Sie in der Liste **Beziehungstyp** den Beziehungstyp auf **Fest**ein.  
  
13. Klicken Sie auf **OK**.  
  
14. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="providing-unique-dimension-member-names"></a>Angeben von eindeutigen Dimensionselementnamen  
 In dieser Aufgabe erstellen Sie benutzerfreundliche Namensspalten, die von den Attributen **EnglishMonthName**, **CalendarQuarter**und **CalendarSemester** verwendet werden.  
  
#### <a name="to-provide-unique-dimension-member-names"></a>So stellen Sie eindeutige Dimensionselementnamen zur Verfügung  
  
1.  Um zur Datenquellensicht **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** zu wechseln, doppelklicken Sie im Ordner **Datenquellensichten** des Projektmappen-Explorers auf diese Sicht.  
  
2.  In der **Tabellen** Bereich mit der rechten Maustaste `Date`, und klicken Sie dann auf **neue benannte Berechnung**.  
  
3.  In der **benannte Berechnung erstellen** (Dialogfeld), Typ `MonthName` in die **Spaltenname** Feld, und geben Sie dann oder kopieren Sie die folgende Anweisung in der **Ausdruck** Feld:  
  
    ```  
    EnglishMonthName+' '+ CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     Mit dieser Anweisung werden der Monat und das Jahr für jeden Monat in der Tabelle zu einer neuen Spalte verknüpft.  
  
4.  Klicken Sie auf **OK**.  
  
5.  In der **Tabellen** Bereich mit der rechten Maustaste `Date`, und klicken Sie dann auf **neue benannte Berechnung**.  
  
6.  In der **benannte Berechnung erstellen** (Dialogfeld), Typ `CalendarQuarterDesc` in der **Spaltenname** , und geben Sie dann oder kopieren und fügen Sie das folgende SQL-Skript in die **Ausdruck** Feld:  
  
    ```  
    'Q' + CONVERT(CHAR (1), CalendarQuarter) +' '+ 'CY ' +  
    CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     Mit diesem SQL-Skript werden das Kalenderquartal und das Jahr für jedes Quartal in der Tabelle zu einer neuen Spalte verknüpft.  
  
7.  Klicken Sie auf **OK**.  
  
8.  In der **Tabellen** Bereich mit der rechten Maustaste `Date`, und klicken Sie dann auf **neue benannte Berechnung**.  
  
9. In der **benannte Berechnung erstellen** (Dialogfeld), Typ `CalendarSemesterDesc` in der **Spaltenname** , und geben Sie dann oder kopieren und fügen Sie das folgende SQL-Skript in die **Ausdruck** Feld:  
  
    ```  
    CASE  
    WHEN CalendarSemester = 1 THEN 'H1' + ' ' + 'CY' + ' '   
           + CONVERT(CHAR(4), CalendarYear)  
    ELSE  
    'H2' + ' ' + 'CY' + ' ' + CONVERT(CHAR(4), CalendarYear)  
    END  
    ```  
  
     Mit diesem SQL-Skript werden das Kalendersemester und das Jahr für jedes Semester in der Tabelle zu einer neuen Spalte verknüpft.  
  
10. Klicken Sie auf **OK.**  
  
11. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="defining-composite-keycolumns-and-setting-the-name-column"></a>Definieren von zusammengesetzten KeyColumns und Festlegen der Namensspalte  
 Die Eigenschaft **KeyColumns** enthält die Spalte bzw. Spalten, die den Schlüssel für das Attribut darstellen. In dieser Aufgabe definieren Sie zusammengesetzte Schlüsselspalten ( **KeyColumns**).  
  
#### <a name="to-define-composite-keycolumns-for-the-english-month-name-attribute"></a>So definieren Sie zusammengesetzte KeyColumns für das English Month Name-Attribut  
  
1.  Öffnen Sie die Registerkarte **Dimensionsstruktur** für die Date-Dimension.  
  
2.  Klicken Sie im Bereich **Attribute** auf das **English Month Name** -Attribut.  
  
3.  Klicken Sie im Fenster **Eigenschaften** auf das Feld **KeyColumns** und anschließend auf die Schaltfläche zum Durchsuchen (**...**).  
  
4.  Wählen Sie im Dialogfeld **Schlüsselspalten** die Spalte **CalendarYear** in der Liste **Verfügbare Spalten**aus, und klicken Sie anschließend auf die Schaltfläche **>** .  
  
5.  Die Spalten **EnglishMonthName** und **CalendarYear** werden jetzt in der Liste **Schlüsselspalten** angezeigt.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Um die **NameColumn** -Eigenschaft des **EnglishMonthName** -Attributs festzulegen, klicken Sie in das Feld **NameColumn** des Eigenschaftenfensters und anschließend auf die Schaltfläche zum Durchsuchen (**...**).  
  
8.  In der **Spalte "Name"** Dialogfeld die **Quellspalte** Liste `MonthName`, und klicken Sie dann auf **OK**.  
  
9. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-quarter-attribute"></a>So definieren Sie zusammengesetzte KeyColumns für das "Calendar Quarter"-Attribut  
  
1.  Klicken Sie im Bereich **Attribute** auf das **Calendar Quarter** -Attribut.  
  
2.  Klicken Sie im Fenster **Eigenschaften** auf das Feld **KeyColumns** und anschließend auf die Schaltfläche zum Durchsuchen (**...**).  
  
3.  Wählen Sie im Dialogfeld **Schlüsselspalten** die Spalte **CalendarYear** in der Liste **Verfügbare Spalten** aus, und klicken Sie anschließend auf die Schaltfläche **>**.  
  
     Die Spalten **CalendarQuarter** und **CalendarYear** werden jetzt in der Liste **Schlüsselspalten** angezeigt.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Um die **NameColumn** -Eigenschaft des **Calendar Quarter** -Attributs festzulegen, klicken Sie in das Feld **NameColumn** des Eigenschaftenfensters und anschließend auf die Schaltfläche zum Durchsuchen (**...**).  
  
6.  In der **Spalte "Name"** Dialogfeld die **Quellspalte** Liste `CalendarQuarterDesc`, und klicken Sie dann auf **OK**.  
  
7.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-semester-attribute"></a>So definieren Sie zusammengesetzte KeyColumns für das "Calendar Semester"-Attribut  
  
1.  Klicken Sie im Bereich **Attribute** auf das **Calendar Semester** -Attribut.  
  
2.  Klicken Sie im Fenster **Eigenschaften** auf das Feld **KeyColumns** und anschließend auf die Schaltfläche zum Durchsuchen (**...**).  
  
3.  Wählen Sie im Dialogfeld **Schlüsselspalten** die Spalte **CalendarYear** in der Liste **Verfügbare Spalten**aus, und klicken Sie anschließend auf die Schaltfläche **>** .  
  
     Die Spalten **CalendarSemester** und **CalendarYear** werden jetzt in der Liste **Schlüsselspalten** angezeigt.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Um die **NameColumn** -Eigenschaft des **Calendar Semester** -Attributs festzulegen, klicken Sie in das Feld **NameColumn** des Eigenschaftenfensters und anschließend auf die Schaltfläche zum Durchsuchen (**...**).  
  
6.  In der **Spalte "Name"** Dialogfeld die **Quellspalte** Liste `CalendarSemesterDesc`, und klicken Sie dann auf **OK**.  
  
7.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="deploying-and-viewing-the-changes"></a>Bereitstellen und Anzeigen der Änderungen  
 Nach dem Ändern von Attributen und Hierarchien müssen Sie die Änderungen bereitstellen und die verknüpften Objekte neu verarbeiten, bevor Sie die Änderungen anzeigen können.  
  
#### <a name="to-deploy-and-view-the-changes"></a>So stellen Sie Änderungen bereit und zeigen sie an  
  
1.  Klicken Sie im Menü **Erstellen** von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf **Analysis Services Tutorial bereitstellen**.  
  
2.  Nach dem Erhalt der der **Bereitstellung erfolgreich abgeschlossen wurde** angezeigt wird, klicken Sie auf die **Browser** Registerkarte **Dimensions-Designer** für die `Date` -Dimension, und Klicken Sie dann auf die Schaltfläche Verbindung wiederherstellen, auf der Symbolleiste des Designers.  
  
3.  Wählen Sie aus der Liste **Hierarchie** **Calendar Quarter** aus. Überprüfen Sie die Elemente in der **Calendar Quarter** -Attributhierarchie.  
  
     Beachten Sie, dass die Namen der Elemente der Attributhierarchie **Calendar Quarter** eindeutiger und einfacher zu verwenden sind, da Sie eine benannte Berechnung erstellt haben, um sie als Namen zu verwenden. Elemente sind jetzt für jedes Quartal pro Jahr in der Hierarchie des **Calendar Quarter** -Attributs vorhanden. Die Elemente werden nicht in chronologischer Reihenfolge sortiert. Stattdessen sind sie nach Quartal und dann nach Jahr sortiert. In der nächsten Aufgabe in diesem Thema ändern Sie dieses Verhalten, um die Elemente dieser Attributhierarchie nach Jahr und dann nach Quartal zu sortieren.  
  
4.  Überprüfen Sie die Elemente der Attributhierarchien **English Month Name** - und **Calendar Semester** .  
  
     Beachten Sie, dass die Elemente dieser Hierarchien ebenfalls nicht in chronologischer Reihenfolge sortiert sind. Stattdessen sind sie nach Monat beziehungsweise Semester und dann nach Jahr sortiert. In der nächsten Aufgabe in diesem Thema ändern Sie dieses Verhalten, um die Sortierreihenfolge zu ändern.  
  
## <a name="changing-the-sort-order-by-modifying-composite-key-member-order"></a>Ändern der Sortierreihenfolge durch Ändern der Elementreihenfolge zusammengesetzter Schlüssel  
 In dieser Aufgabe ändern Sie die Sortierreihenfolge, indem Sie die Reihenfolge der Schlüssel, aus denen der zusammengesetzte Schlüssel besteht, ändern.  
  
#### <a name="to-modify-the-composite-key-member-order"></a>So ändern Sie die Elementreihenfolge zusammengesetzter Schlüssel  
  
1.  Öffnen der **Dimensionsstruktur** Registerkarte des Dimensions-Designer für die `Date` dimension, und wählen Sie dann **Calendar Semester** in die **Attribute** Bereich.  
  
2.  Überprüfen Sie im Eigenschaftenfenster den Wert für die **OrderBy** -Eigenschaft. Er wird auf **Schlüssel**festgelegt.  
  
     Die Elemente der **Calendar Semester** -Attributhierarchie werden nach ihren Schlüsselwerten sortiert. Mit einem zusammengesetzten Schlüssel basiert die Sortierung der Elementschlüssel zuerst auf dem Wert des ersten Elementschlüssels und dann auf dem Wert des zweiten Elementschlüssels. Mit anderen Worten: Die Elemente der **Calendar Semester** -Attributhierarchie werden zuerst nach Semester und dann nach Jahr sortiert.  
  
3.  Klicken Sie im Eigenschaftenfenster auf die Schaltfläche mit den Auslassungspunkten (**...**), um den **KeyColumns** -Eigenschaftswert zu ändern.  
  
4.  Überprüfen Sie in der Liste **Schlüsselspalten** des Dialogfelds **Schlüsselspalten** , ob **CalendarSemester** ausgewählt ist. Klicken Sie anschließend auf den Pfeil nach unten, um die Reihenfolge der Elemente dieses zusammengesetzten Schlüssels umzukehren. Klicken Sie auf **OK**.  
  
     Die Elemente der Attributhierarchie sind jetzt zuerst nach Jahr und dann nach Semester sortiert.  
  
5.  Wählen Sie im Bereich **Attribute** die Option **Calendar Quarter** aus, und klicken Sie anschließend im Eigenschaftenfenster auf die Schaltfläche mit den Auslassungspunkten (**...**) für die **KeyColumns** -Eigenschaft.  
  
6.  Überprüfen Sie in der Liste **Schlüsselspalten** des Dialogfelds **Schlüsselspalten** , ob **CalendarQuarter** ausgewählt ist. Klicken Sie anschließend auf den Pfeil nach unten, um die Reihenfolge der Elemente dieses zusammengesetzten Schlüssels umzukehren. Klicken Sie auf **OK**.  
  
     Die Elemente der Attributhierarchie sind jetzt zuerst nach Jahr und dann nach Quartal sortiert.  
  
7.  Wählen Sie im Bereich **Attribute** den Eintrag **English Month Name** aus, und klicken Sie anschließend im Fenster Eigenschaften auf die Schaltfläche mit den drei Auslassungspunkten (**...**) für die **KeyColumns** -Eigenschaft.  
  
8.  Überprüfen Sie in der Liste **Schlüsselspalten** des Dialogfelds **Schlüsselspalten** , ob **EnglishMonthName** ausgewählt ist. Klicken Sie anschließend auf den Pfeil nach unten, um die Reihenfolge der Elemente dieses zusammengesetzten Schlüssels umzukehren. Klicken Sie auf **OK**.  
  
     Die Elemente der Attributhierarchie sind jetzt zuerst nach Jahr und dann nach Monat sortiert.  
  
9. Klicken Sie im Menü **Erstellen** von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf **Analysis Services Tutorial bereitstellen**. Wenn die Bereitstellung erfolgreich abgeschlossen wurde, klicken Sie auf die **Browser** Registerkarte im Dimensions-Designer für die `Date` Dimension.  
  
10. Klicken Sie auf der Symbolleiste der Registerkarte **Browser** auf die Schaltfläche zum Wiederherstellen der Verbindung.  
  
11. Überprüfen Sie die Elemente der Attributhierarchien **Calendar Quarter** - und **Calendar Semester** .  
  
     Beachten Sie, dass die Elemente dieser Hierarchien jetzt in chronologischer Reihenfolge sortiert sind, also nach Jahr und dann nach Quartal beziehungsweise Semester.  
  
12. Überprüfen Sie die Elemente der Attributhierarchie **English Month Name** .  
  
     Beachten Sie, dass die Elemente der Attributhierarchie jetzt zuerst nach Jahr und dann alphabetisch nach Monat sortiert werden. Dies hängt mit der Tatsache zusammen, dass der Datentyp der EnglishCalendarMonth-Spalte in der Datenquellensicht eine Zeichenfolgenspalte ist, basierend auf dem Datentyp „nvarchar“ in der zugrunde liegenden relationalen Datenbank. Informationen darüber, wie die Monate innerhalb jedes Jahres chronologisch sortiert werden können, finden Sie unter [Sortieren von Attributelementen basierend auf einem sekundären Attribut](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md).  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Durchsuchen des bereitgestellten Cubes](lesson-3-5-browsing-the-deployed-cube.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
