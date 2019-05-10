---
title: Definieren einer Faktenbeziehung | Microsoft-Dokumentation
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2d82ca352c574d02a5b0631df5c9448df12a5acc
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404002"
---
# <a name="lesson-5-2---defining-a-fact-relationship"></a>Lektion 5-2: Definieren einer Faktenbeziehung
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Von Benutzern wird manchmal der Wunsch geäußert, Measures nach Datenelementen dimensionieren zu können, die sich in der Faktentabelle befinden, oder die Faktentabelle nach bestimmten zusätzlichen verknüpften Informationen durchsuchen zu können, beispielsweise Rechnungsnummern oder Auftragsbestätigungsnummern, die mit bestimmten Verkaufsfakten verknüpft sind. Wenn Sie eine Dimension basierend auf einem solchen Faktentabellenelement definieren, wird diese Dimension als *Faktendimension*bezeichnet. Eine Faktendimension wird auch als degenerierte Dimension bezeichnet. Faktendimensionen sind für das Gruppieren verknüpfter Faktentabellenzeilen nützlich, beispielsweise aller Zeilen, die sich auf eine bestimmte Rechnungsnummer beziehen. Obwohl Sie diese Informationen in einer separaten Dimensionstabelle in der relationalen Datenbank speichern können, stellt das Erstellen einer separaten Dimensionstabelle für die Informationen keinen Vorteil dar, weil die Dimensionstabelle genauso schnell wachsen würde wie die Faktentabelle und nur zu doppelt vorhandenen Daten und unnötiger Komplexität führen würde.  
  
Innerhalb von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]können Sie bestimmen, ob die Faktendimensionsdaten in einer MOLAP-Dimensionsstruktur für verbesserte Abfrageleistung dupliziert werden sollen, oder ob die Faktendimension als ROLAP-Dimension definiert werden soll, um Speicherplatz auf Kosten der Abfrageleistung zu sparen. Wenn Sie eine Dimension mit dem MOLAP-Speichermodus speichern, werden alle Dimensionselemente in der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht nur in den Partitionen der Measuregruppe, sondern auch in einer hochkomprimierten MOLAP-Struktur gespeichert. Wenn Sie eine Dimension mit dem ROLAP-Speichermodus speichern, nur die Dimensionsdefinition befindet sich in der MOLAP-Struktur-die Dimensionselemente selbst aus der zugrunde liegenden relationalen Faktentabelle zur Abfragezeit abgefragt werden. Sie treffen Ihre Entscheidung bezüglich des entsprechenden Speichermodus aufgrund der Häufigkeit, mit der die Faktendimension abgefragt wird, der Anzahl von Zeilen, die von einer typischen Abfrage zurückgegeben wird, der Leistung der Abfrage und der Verarbeitungskosten. Das Definieren einer Dimension als ROLAP setzt nicht voraus, dass alle Cubes, die die Dimension verwenden, ebenfalls mit dem ROLAP-Speichermodus gespeichert werden. Der Speichermodus kann für jede Dimension unabhängig konfiguriert werden.  
  
Wenn Sie eine Faktendimension definieren, können Sie die Beziehung zwischen der Faktendimension und der Measuregruppe als eine Faktenbeziehung definieren. Die folgenden Einschränkungen gelten für Faktenbeziehungen:  
  
-   Das Granularitätsattribut muss die Schlüsselspalte für die Dimension sein, wodurch eine 1:1-Beziehung zwischen der Dimension und den Fakten in der Faktentabelle erstellt wird.  
  
-   Eine Dimension darf nur mit einer einzigen Measuregruppe eine Faktenbeziehung aufweisen.  
  
> [!NOTE]  
> Faktendimensionen müssen nach jedem Update der Measuregruppe, auf die die Faktenbeziehung verweist, inkrementell aktualisiert werden.  
  
Weitere Informationen finden Sie unter [Dimensionsbeziehungen](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)und [Definieren von Faktenbeziehungen und Faktenbeziehungseigenschaften](../multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).  
  
In den Aufgaben dieses Themas fügen Sie eine neue Cubedimension basierend auf der **CustomerPONumber** -Spalte in der **FactInternetSales** -Faktentabelle hinzu. Anschließend definieren Sie die Beziehung zwischen dieser neuen Cubedimension und der **Internet Sales** -Measuregruppe als Faktenbeziehung.  
  
## <a name="defining-the-internet-sales-orders-fact-dimension"></a>Definieren der Internet Sales Orders-Faktendimension  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Dimensionen**und anschließend auf **Neue Dimension**.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Dimensions-Assistenten** auf **Weiter**.  
  
3.  Überprüfen Sie, ob die Option **Vorhandene Tabelle verwenden** auf der Seite **Erstellungsmethode auswählen** ausgewählt ist, und klicken Sie anschließend auf **Weiter**.  
  
4.  Überprüfen Sie auf der Seite **Quellinformationen angeben** , ob die **Adventure Works DW 2012** -Datenquellensicht ausgewählt ist.  
  
5.  Wählen Sie in der Liste **Haupttabelle** den Eintrag **InternetSales**aus.  
  
6.  Überprüfen Sie in der Liste **Schlüsselspalten** , ob **SalesOrderNumber** und **SalesOrderLineNumber** aufgelistet werden.  
  
7.  Wählen Sie in der Liste **Namensspalte** den Eintrag **SalesOrderLineNumber**aus.  
  
8.  Klicken Sie auf **Weiter**.  
  
9. Deaktivieren Sie auf der Seite **Verknüpfte Tabellen auswählen** die Kontrollkästchen neben allen Tabellen, und klicken Sie anschließend auf **Weiter**.  
  
10. Klicken Sie auf der Seite **Dimensionsattribute auswählen** zweimal auf das Kontrollkästchen im Header, um alle Kontrollkästchen zu deaktivieren. Das **Sales Order Number** -Attribut bleibt ausgewählt, da es das Schlüsselattribut ist.  
  
11. Wählen Sie das **Customer PO Number** -Attribut aus, und klicken Sie anschließend auf **Weiter**.  
  
12. Ändern Sie auf der Seite **Assistenten abschließen** den Namen in **Internet Sales Order Details** , und klicken Sie anschließend auf **Fertig stellen** , um den Assistenten zu beenden.  
  
13. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
14. Wählen Sie im Bereich **Attributes** des Dimensions-Designers für die Dimension **Internet Sales Order Details** die Option **Sales Order Number**aus, und ändern Sie anschließend die **Name** -Eigenschaft im Fenster Eigenschaften in **Item Description**.  
  
15. In der **NameColumn** Eigenschaft Zelle, klicken Sie auf die Schaltfläche zum Durchsuchen **(...)** . Wählen Sie im Dialogfeld **Namensspalte** den Eintrag **Produkt** in der **Quelltabelle** -Liste aus, wählen Sie **EnglishProductName** für die **Quellspalte**aus, und klicken Sie anschließend auf **OK**.  
  
16. Fügen Sie das **Sales Order Number** -Attribut zur Dimension hinzu, indem Sie die **SalesOrderNumber** -Spalte aus der **InternetSales** -Tabelle in den Bereich **Datenquellensicht** zum Bereich **Attribute** ziehen.  
  
17. Ändern Sie die **Name** -Eigenschaft des neuen **Sales Order Number** -Attributs zu **Order Number**, und ändern Sie die **OrderBy** -Eigenschaft zu **Key**.  
  
18. Erstellen Sie im Bereich **Hierarchien** eine **Internet Sales Orders** -Benutzerhierarchie, die die Ebenen **Order Number** und **Item Description** in dieser Reihenfolge enthält.  
  
19. Wählen Sie im Bereich **Attribute** **Internet Sales Order Details**aus, und überprüfen Sie anschließend den Wert für die **StorageMode** -Eigenschaft im Eigenschaftenfenster.  
  
    Beachten Sie, dass die Dimension standardmäßig als MOLAP-Dimension gespeichert wird. Obwohl durch das Ändern des Speichermodus zu ROLAP Verarbeitungszeit und Speicherplatz gespart werden würde, geschähe dies auf Kosten der Abfrageleistung. Für die Zwecke dieses Lernprogramms verwenden Sie als Speichermodus MOLAP.  
  
20. Um die neu erstellte Dimension als Cubedimension zum [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Cube hinzuzufügen, wechseln Sie zum **Cube-Designer**. Klicken Sie mit der rechten Maustaste in den Bereich **Dimensionen** der Registerkarte **Cubestruktur** , und wählen Sie die Option **Cubedimension hinzufügen**aus.  
  
21. Wählen Sie im Dialogfeld **Cubedimension hinzufügen**die Option **Internet Sales Order Details** aus, und klicken Sie anschließend auf **OK**.  
  
## <a name="defining-a-fact-relationship-for-the-fact-dimension"></a>Definieren einer Faktenbeziehung für die Fact-Dimension  
  
1.  Klicken Sie im Cube-Designer für den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Cube auf die Registerkarte **Dimensionsverwendung** .  
  
    Beachten Sie, dass die **Internet Sales Order Details** -Cubedimension automatisch mit einer Faktenbeziehung konfiguriert wird, wie durch das eindeutige Symbol angezeigt wird.  
  
2.  Klicken Sie auf die Schaltfläche zum Durchsuchen (**...** ) in der **Item Description** -Zelle am Schnittpunkt der der **Internetverkäufe** Measuregruppe und der **Internet Sales Order Details** dimension, zu Überprüfen Sie die faktenbeziehungseigenschaften aus.  
  
    Das Dialogfeld **Beziehung definieren** wird geöffnet. Beachten Sie, dass Sie keine der Eigenschaften konfigurieren können.  
  
    Die folgende Abbildung zeigt die Faktenbeziehungseigenschaften im Dialogfeld **Beziehung definieren** .  
  
    ![Das Dialogfeld Beziehung definieren](../media/l5-factrelationship-2.gif "Dialogfeld Beziehung definieren")  
  
3.  Klicken Sie auf **Abbrechen**.  
  
## <a name="browsing-the-cube-by-using-the-fact-dimension"></a>Durchsuchen des Cubes mithilfe der Fact-Dimension  
  
1.  Klicken Sie im Menü **Erstellen** auf **Analysis Services Tutorial bereitstellen** , um die Änderungen an der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitzustellen und die Datenbank zu verarbeiten.  
  
2.  Klicken Sie nach erfolgreichem Abschluss der Bereitstellung im Cube-Designer für den **Tutorial-Cube auf die Registerkarte** Browser [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und anschließend auf **Verbindung wiederherstellen** .  
  
3.  Entfernen Sie alle Measures und Hierarchien aus dem Datenbereich, und fügen Sie anschließend das **Internet Sales-Sales Amount** -Measure zum Datenbereich hinzu.  
  
4.  Erweitern Sie im Metadatenbereich **Customer**, **Location**, **Customer Geography**, **Members**, **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**, klicken Sie mit der rechten Maustaste auf **Adam Powell**, und klicken Sie anschließend auf **Zu Filter hinzufügen**.  
  
    Das Filtern zum Begrenzen der Kaufaufträge für einen einzigen Kunden ermöglicht dem Benutzer einen Drilldown zum zugrunde liegenden Detail in einer großen Faktentabelle ohne signifikante Einbußen bei der Abfrageleistung.  
  
5.  Fügen Sie die benutzerdefinierte **Internet Sales Orders** -Hierarchie aus der **Internet Sales Order Details** -Dimension dem Zeilenbereich des Datenbereichs hinzu.  
  
    Beachten Sie, dass die Verkaufsauftragsnummern und die korrespondierenden Internetverkaufssummen für Adam Powell im Datenbereich angezeigt werden.  
  
    Die folgende Abbildung zeigt das Ergebnis der vorherigen Schritte.  
  
    ![Dimensionieren von Internet Sales-Sales Amount](../media/l5-factrelationship-3.gif "dimensionieren von Internet Sales-Sales Amount")  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
[Definieren einer m:n-Beziehung](lesson-5-3-defining-a-many-to-many-relationship.md)  
  
## <a name="see-also"></a>Siehe auch  
[Dimensionsbeziehungen](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
[Definieren von Faktenbeziehungen und Faktenbeziehungseigenschaften](../multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)  
  
  
  
