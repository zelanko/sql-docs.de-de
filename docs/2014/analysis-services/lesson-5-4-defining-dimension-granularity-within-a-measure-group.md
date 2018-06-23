---
title: Definieren von Dimensionsgranularität innerhalb einer Measuregruppe | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f079485-9eb4-405c-9a20-81258298b810
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: deeae89f59779000ac2dda9ca4da639666852bae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159067"
---
# <a name="defining-dimension-granularity-within-a-measure-group"></a>Definieren von Dimensionsgranularität innerhalb einer Measuregruppe
  Benutzer möchten die Möglichkeit bekommen, Faktendaten mit einer anderen Granularität oder Spezifizierung für andere Zwecke zu dimensionieren. Verkaufsdaten für Händler- oder Internetverkäufe können z. B. für jeden Tag aufgezeichnet werden, wogegen Sollvorgaben für den Verkauf möglicherweise nur auf Monats- oder Quartalsebene vorhanden sind. In diesen Szenarios möchten Benutzer eine Time-Dimension mit einer anderen oder detaillierteren Auflösung für jede dieser verschiedenen Faktentabellen verwenden. Sie könnten zwar eine neue Datenbankdimension als Time-Dimension mit dieser anderen Auflösung definieren, doch bietet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]eine einfachere Lösung.  
  
 Wenn eine Dimension in einer Measuregruppe verwendet wird, basiert die Auflösung der Daten in dieser Dimension in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]standardmäßig auf dem Schlüsselattribut der Dimension. Wenn beispielsweise eine Zeitdimension in einer Measuregruppe enthalten und die Standardauflösung der Zeitdimension täglich ist, ist die Standardauflösung der Dimension innerhalb der Measuregruppe täglich. Dies ist häufig angemessen, wie z. B. für die Measuregruppen **Internet Sales** und **Reseller Sales** in diesem Tutorial. Wenn allerdings solch eine Dimension in anderen Typen von Measuregruppen eingeschlossen wird (beispielsweise Vorgaben für den Verkauf oder Budget-Measuregruppe), ist eine monatliche oder vierteljährliche Auflösung angemessener.  
  
 Wenn Sie eine andere als die standardmäßige Auflösung für eine Cubedimension angeben möchten, ändern Sie das Granularitätsattribut für eine innerhalb einer bestimmten Measuregruppe verwendete Cubedimension auf der Registerkarte **Dimensionsverwendung** des Cube-Designers. Wenn Sie die Auflösung einer Dimension innerhalb einer bestimmten Measuregruppe zu einem anderen Attribut als dem Schlüsselattribut für diese Dimension ändern, müssen Sie sicherstellen, dass alle anderen Attribute in dieser Measuregruppe direkt oder indirekt mit dem neuen Granularitätsattribut verknüpft sind. Geben Sie dazu Attributbeziehungen zwischen allen anderen Attributen und dem Attribut an, das als Granularitätsattribut in der Measuregruppe angegeben ist. In diesem Fall definieren Sie zusätzliche Attributbeziehungen, anstatt Attributbeziehungen zu verschieben. Das als Granularitätsattribut angegebene Attribut wird effektiv zum Schlüsselattribut innerhalb der Measuregruppe für die verbleibenden Attribute in der Dimension. Wenn Sie Attributbeziehungen nicht entsprechend angeben, können von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Werte nicht ordnungsgemäß aggregiert werden. Darauf wird in den Aufgaben in diesem Thema genau eingegangen.  
  
 Weitere Informationen finden Sie unter [Dimensionsbeziehungen](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)und [Definieren einer regulären Beziehung und von Eigenschaften einer regulären Beziehung](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md).  
  
 In den Aufgaben in diesem Thema fügen Sie eine Sales Quota-Measuregruppe hinzu und definieren die Granularität der Date-Dimension in dieser Measuregruppe als monatlich. Sie definieren dann Attributbeziehungen zwischen dem Monatsattribut und anderen Dimensionsattributen, um sicherzustellen, dass Werte von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ordnungsgemäß aggregiert werden.  
  
## <a name="adding-tables-and-defining-the-sales-quotas-measure-group"></a>Hinzufügen von Tabellen und Definieren der Sales Quota-Measuregruppe  
  
1.  Wechseln Sie zur **Adventure Works DW 2012** -Datenquellensicht.  
  
2.  Mit der rechten Maustaste an einer beliebigen Stelle der **Diagrammplaner** Bereich, klicken Sie auf **neues Diagramm**, und benennen Sie das Diagramm `Sales Quotas`.  
  
3.  Ziehen Sie die **Mitarbeiter**, **Vertriebsgebiet**, und `Date` Tabellen aus der **Tabellen** Bereich, um die **Diagramm** Bereich.  
  
4.  Fügen Sie die **FactSalesQuota** -Tabelle dem Bereich **Diagramm** hinzu, indem Sie mit der rechten Maustaste auf eine beliebige Stelle im Bereich **Diagramm** klicken und anschließend **Tabellen hinzufügen/entfernen**auswählen.  
  
     Beachten Sie, dass die **SalesTerritory** -Tabelle über die **Employee** -Tabelle mit der **FactSalesQuota** -Tabelle verknüpft ist.  
  
5.  Überprüfen Sie die Spalten in der **FactSalesQuota** -Tabelle, und sehen Sie sich anschließend die Daten in dieser Tabelle an.  
  
     Beachten Sie, dass die Auflösung der Daten innerhalb dieser Tabelle das Kalenderquartal ist, also die niedrigste Detailebene in der FactSalesQuota-Tabelle.  
  
6.  Ändern Sie im Datenquellensicht-Designers, der **FriendlyName** Eigenschaft von der **FactSalesQuota** Tabelle `SalesQuotas`.  
  
7.  Wechseln Sie zum [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube, und klicken Sie anschließend auf die Registerkarte **Cubestruktur** .  
  
8.  Mit der rechten Maustaste an einer beliebigen Stelle der **Measures** Bereich, klicken Sie auf **neue Measuregruppe**, klicken Sie auf `SalesQuotas` in der **neue Measuregruppe** Dialogfeld Feld, und klicken Sie dann auf **OK**.  
  
     Die `Sales Quotas` Measuregruppe angezeigt wird, der **Measures** Bereich. In der **Dimensionen** Bereich, beachten Sie, dass ein neues `Date` Cubedimension auch definiert, basierend auf den `Date` Datenbankdimension. Eine neue zeitbezogene Cubedimension wird definiert, weil für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unbekannt ist, welche der vorhandenen zeitbezogenen Cubedimensionen mit der **DateKey** -Spalte in der **FactSalesQuota** -Faktentabelle verknüpft werden sollen, die der Sales Quotas-Measuregruppe zugrunde liegen. Sie ändern dies später in einer anderen Aufgabe in diesem Thema.  
  
9. Erweitern Sie die `Sales Quotas` Measuregruppe.  
  
10. Wählen Sie im Bereich **Measures** den Eintrag **Sales Amount Quota**aus, und legen Sie anschließend im Eigenschaftenfenster den Wert für die **FormatString** -Eigenschaft auf **Currency** fest.  
  
11. Wählen Sie die **Sales Quotas Count** messen, und geben Sie `#,#` als Wert für die **"FormatString"** Eigenschaft im Eigenschaftenfenster angezeigt.  
  
12. Löschen der **Calendar Quarter** measure aus der `Sales Quotas` Measuregruppe.  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellte die dem Calendar Quarter-Measure zugrunde liegende Spalte als Spalte fest, die Measures enthält. Diese Spalte und die CalendarYear-Spalte enthalten allerdings die Werte, die Sie zum Verknüpfen der Sales Quotas-Measuregruppe mit der Date-Dimension später in diesem Thema verwenden werden.  
  
13. In der **Measures** Bereich mit der rechten Maustaste die `Sales Quotas` Measuregruppe, und klicken Sie dann auf **Neues Measure**.  
  
     Das Dialogfeld **Neues Measure** wird geöffnet, das die verfügbaren Quellenspalten für ein Measure mit dem Verwendungstyp **Summe**enthält.  
  
14. In der **Neues Measure** wählen Sie im Dialogfeld **Distinct Count** in der **Verwendung** , ob `SalesQuotas` ausgewählt ist, der **Quelltabelle** Liste **Spalte "employeekey"** in der **Quellspalte** aus, und klicken Sie dann auf **OK**.  
  
     Beachten Sie, dass das neue Measure in einer neuen Measuregruppe namens **Sales Quotas 1**erstellt wird. Distinct count Measures in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] werden in ihren eigenen Measuregruppen erstellt, um die Verarbeitungsleistung zu optimieren.  
  
15. Ändern Sie den Wert für die **Namen** -Eigenschaft für die **Employee Key Distinct Count** measure `Sales Person Count`, und geben Sie dann `#,#` als Wert für die **"FormatString"** Eigenschaft.  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a>Durchsuchen der Measures in der Sales Quota-Measuregruppe nach Datum  
  
1.  Klicken Sie im Menü **Erstellen** auf **Analysis Services Tutorial bereitstellen**.  
  
2.  Klicken Sie nach erfolgreichem Abschluss der Bereitstellung im Cube-Designer für den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube auf die Registerkarte **Browser** und anschließend auf die Schaltfläche **Verbindung wiederherstellen**.  
  
3.  Klicken Sie auf die Excel-Verknüpfung und anschließend auf **Aktivieren**.  
  
4.  Erweitern Sie in der PivotTable-Feldliste die `Sales Quotas` Measuregruppe, und ziehen Sie dann die **Sales Amount Quota** measure in den Bereich Werte.  
  
5.  Erweitern Sie die **Sales Territory** -Dimension, und ziehen Sie die benutzerdefinierte **Sales Territories** -Hierarchie in Zeilenbezeichnungen.  
  
     Beachten Sie, dass die Sales Territory-Cubedimension weder direkt noch indirekt mit der Fact Sales Quota-Tabelle verknüpft ist, wie im folgenden Bild zu sehen.  
  
     ![Sales Territory-Cubedimension](../../2014/tutorials/media/l5-granularity-2.gif "Sales Territory-Cubedimension")  
  
     In den nächsten Schritten in diesem Thema definieren Sie eine Bezugdimensionsbeziehung zwischen dieser Dimension und dieser Faktentabelle.  
  
6.  Verschieben Sie die **Sales Territories** -Benutzerhierarchie aus dem Bereich Zeilenbezeichnungen in den Bereich Spaltenbezeichnungen.  
  
7.  Wählen Sie in der PivotTable-Feldliste die benutzerdefinierte **Sales Territories** -Hierarchie aus, und klicken Sie anschließend auf der rechten Seite auf den nach unten weisenden Pfeil.  
  
     ![Sales Territories-Hierarchie in der Feldliste](../../2014/tutorials/media/l5-granularity-1a.png "Sales Territories-Hierarchie in der Feldliste")  
  
8.  Klicken Sie im Filter auf das Kontrollkästchen **Alles auswählen**, um die Auswahl aller Optionen aufzuheben, und wählen Sie anschließend nur „North America“ aus.  
  
     ![Filterbereich für die Auswahl von North America](../../2014/tutorials/media/l5-granularity-1b.png "Filterbereich für Nordamerika auswählen")  
  
9. Erweitern Sie in der PivotTable-Feldliste `Date`.  
  
10. Ziehen Sie die **Date.Fiscal Date** -Benutzerhierarchie in Zeilenbezeichnungen.  
  
11. Klicken Sie auf der PivotTable auf den nach unten weisenden Pfeil neben Zeilenbezeichnungen. Löschen Sie alle Jahre außer **FY 2008**.  
  
     Beachten Sie, dass nur die **Juli 2007** Mitglied der **Monat** -Ebene angezeigt wird, statt die **Juli 2007**, **August 2007**, und **September 2007** Mitglied **Monat** Ebene, und dass nur die **1. Juli 2007** Mitglied der `Date` -Ebene angezeigt wird anstelle aller 31 Tage. Dieses Verhalten tritt auf, weil die Auflösung der Daten in der Faktentabelle auf der Quartalsebene und die Auflösung der der `Date` Dimension ist der täglichen Ebene. Sie ändern dieses Verhalten später in der nächsten Aufgabe in diesem Thema.  
  
     Beachten Sie auch, dass der Wert von **Sales Amount Quota** für die Monats- und Tagesebenen derselbe Wert wie für die Quartalsebene ist, nämlich $13,733,000.00. Dies liegt daran, dass sich die unterste Ebene der Daten in der Sales Quotas-Measuregruppe auf der Quartalsebene befindet. Sie ändern dieses Verhalten in Lektion 6.  
  
     Die folgende Abbildung zeigt die Werte für **Sales Amount Quota**.  
  
     ![Werte für Sales Betrag Kontingent](../../2014/tutorials/media/l5-granularity-3.png "Werte für Sales Betrag Kontingent")  
  
## <a name="defining-dimension-usage-properties-for-the-sales-quotas-measure-group"></a>Definieren der Dimensionsverwendungseigenschaft für die Sales Quotas-Measuregruppe  
  
1.  Öffnen Sie den Dimensions-Designer für die **Employee** -Dimension, klicken Sie mit der rechten Maustaste im Bereich **Datenquellensicht** auf **SalesTerritoryKey** und anschließend auf **Neues Attribut aus Spalte**.  
  
2.  Wählen Sie im Bereich **Attribute** den Eintrag **SalesTerritoryKey**aus, und legen Sie im Fenster Eigenschaften die **AttributeHierarchyVisible** -Eigenschaft auf **False** , die **AttributeHierarchyOptimizedState** -Eigenschaft auf **NotOptimized**und die **AttributeHierarchyOrdered** -Eigenschaft auf **False**fest.  
  
     Dieses Attribut ist erforderlich, um die Verknüpfung der **Vertriebsgebiet** -Dimension in den `Sales Quotas` und **Sales Quotas 1** Measuregruppen als referenzierte Dimension.  
  
3.  Im Cube-Designer für die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube, klicken Sie auf die **Dimensionsverwendung** Registerkarte, und überprüfen Sie dann die Dimensionsverwendung innerhalb der `Sales Quotas` und **Sales Quotas 1** Measuregruppen.  
  
     Beachten Sie, dass die **Mitarbeiter** und `Date` Cubedimensionen verknüpft sind, um die **Sales Quotasand Sales Quotas 1** Measuregruppen durch reguläre Beziehungen. Beachten Sie außerdem, dass die **Sales Territory** -Cubedimension mit keiner dieser Measuregruppen verknüpft ist.  
  
4.  Klicken Sie auf die Zelle am Schnittpunkt der **Vertriebsgebiet** Dimension und die `Sales Quotas` Measuregruppe, und klicken Sie dann auf die Schaltfläche zum Durchsuchen (**...** ). Das Dialogfeld **Beziehung definieren** wird geöffnet.  
  
5.  Wählen Sie in der Liste **Beziehungstyp auswählen** die Option **Referenziert**.  
  
6.  Wählen Sie in der **Zwischendimension** -Liste die Option **Employee**aus.  
  
7.  Wählen Sie in der Liste **Bezugsdimensionsattribut** das Attribut **Sales Territory Region**aus.  
  
8.  Wählen Sie in der Liste **Zwischendimensionsattribut** das Attribut **Sales Territory Key**aus. (Die Schlüsselspalte für das Sales Territory Region-Attribut ist die SalesTerritoryKey-Spalte.)  
  
9. Überprüfen Sie, ob das Kontrollkästchen **Materialisieren** aktiviert ist.  
  
10. Klicken Sie auf **OK**.  
  
11. Klicken Sie auf die Zelle am Schnittpunkt der **Sales Territory** -Dimension und der **Sales Quotas 1** -Measuregruppe und anschließend auf die Schaltfläche zum Durchsuchen (**…**). Das Dialogfeld **Beziehung definieren** wird geöffnet.  
  
12. Wählen Sie in der Liste **Beziehungstyp auswählen** die Option **Referenziert**.  
  
13. Wählen Sie in der **Zwischendimension** -Liste die Option **Employee**aus.  
  
14. Wählen Sie in der Liste **Bezugsdimensionsattribut** das Attribut **Sales Territory Region**aus.  
  
15. Wählen Sie in der Liste **Zwischendimensionsattribut** das Attribut **Sales Territory Key**aus. (Die Schlüsselspalte für das Sales Territory Region-Attribut ist die SalesTerritoryKey-Spalte.)  
  
16. Überprüfen Sie, ob das Kontrollkästchen **Materialisieren** aktiviert ist.  
  
17. Klicken Sie auf **OK**.  
  
18. Löschen der `Date` Cubedimension.  
  
     Anstatt vier zeitbezogene Cubedimensionen, verwenden Sie die **Bestelldatum** Cubedimension in der `Sales Quotas` Measuregruppe als das Datum für die sales dimensioniert werden verkaufsvorgaben. Sie verwenden diese Cubedimension auch als die primäre Datendimension im Cube.  
  
19. In der **Dimensionen** auflisten, benennen Sie die **Bestelldatum** Cubedimension in `Date`.  
  
     Umbenennen der **Bestelldatum** Cubedimension in `Date` erleichtert es dem Benutzer um seine Rolle als primäre Datendimension in diesem Cube zu verstehen.  
  
20. Klicken Sie auf die Schaltfläche zum Durchsuchen (**...** ) in der Zelle am Schnittpunkt der `Sales Quotas` Measuregruppe und der `Date` Dimension.  
  
21. Wählen Sie im Dialogfeld **Beziehung definieren** in der Liste **Beziehungstyp auswählen** den Eintrag **Regulär** aus.  
  
22. Wählen Sie in der **Granularitätsattribut** -Liste **Calendar Quarter**aus.  
  
     Beachten Sie, dass eine Warnung angezeigt wird, die Sie darauf hinweist, dass, weil Sie ein Nicht-Schlüssel-Attribut als Granularitätsattribut ausgewählt haben, Sie sicherstellen müssen, dass alle anderen Attribute direkt oder indirekt mit dem Granularitätsattribut verknüpft sein müssen, indem Sie als Elementeigenschaften angegeben werden.  
  
23. Verknüpfen Sie im Bereich **Beziehung** des Dialogfelds **Beziehung definieren** die Dimensionsspalten **CalendarYear** und **CalendarQuarter** aus der der Date-Cubedimension zugrunde liegenden Tabelle mit den Spalten **CalendarYear** und **CalendarQuarter** in der der Sales Quota-Measuregruppe zugrunde liegenden Tabelle, und klicken Sie anschließend auf **OK**.  
  
    > [!NOTE]  
    >  Calendar Quarter ist als Granularitätsattribut für die Date-Cubedimension in der Sales Quotas-Measuregruppe definiert, das Date-Attribut ist jedoch weiterhin das Granularitätsattribut für die Measuregruppen Internet Sales und Reseller Sales.  
  
24. Wiederholen Sie die vorhergehenden vier Schritte für die **Sales Quotas 1** -Measuregruppe.  
  
## <a name="defining-attribute-relationships-between-the-calendar-quarter-attribute-and-the-other-dimension-attributes-in-the-date-dimension"></a>Definieren von Attributbeziehungen zwischen dem Calendar Quarter-Attribut und den anderen Dimensionsattributen in der Date-Dimension  
  
1.  Wechseln Sie zur **Dimensions-Designer** für die `Date` dimension, und klicken Sie dann auf die **Attributbeziehungen** Registerkarte.  
  
     Beachten Sie, dass, obwohl **Kalenderjahr** verknüpft ist **Calendar Quarter** über die **Calendar Semester** Attributs, des Geschäftskalenders Attribute nur für eine verknüpft sind eine andere; mit nicht verknüpft sind die **Calendar Quarter** Attribut, und daher nicht aggregiert, ordnungsgemäß in den `Sales Quotas` Measuregruppe.  
  
2.  Klicken Sie im Diagramm mit der rechten Maustaste auf das Attribut **Calendar Quarter** , und wählen Sie **Neue Attributbeziehung**aus.  
  
3.  Im Dialogfeld **Attributbeziehung erstellen** lautet das **Quellattribut** **Calendar Quarter**. Legen Sie den Wert **Verknüpftes Attribut** auf **Fiscal Quarter**fest.  
  
4.  Klicken Sie auf **OK**.  
  
     Beachten Sie, das eine Warnmeldung angezeigt wird, besagt, dass die `Date` Dimension enthält eine oder mehrere redundante attributbeziehungen, die verhindern, dass möglicherweise Daten aggregiert werden, wenn ein nichtschlüsselattribut als Granularitätsattribut ein verwendet wird.  
  
5.  Löschen Sie die Attributbeziehung zwischen dem **Month Name** -Attribut und dem **Fiscal Quarter** -Attribut.  
  
6.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a>Durchsuchen der Measures in der Sales Quota-Measuregruppe nach Datum  
  
1.  Klicken Sie im Menü **Erstellen** auf **Analysis Services Tutorial bereitstellen**.  
  
2.  Klicken Sie nach erfolgreichem Abschluss der Bereitstellung im Cube-Designer für den **Tutorial-Cube auf die Registerkarte** Browser [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und anschließend auf **Verbindung wiederherstellen**.  
  
3.  Klicken Sie auf die Excel-Verknüpfung und anschließend auf **Aktivieren**.  
  
4.  Ziehen Sie das **Sales Amount Quota** -Measure in den Bereich Werte.  
  
5.  Ziehen Sie die **Sales Territories** -Benutzerhierarchie in das Feld „Spaltenbezeichnungen“, und filtern Sie anschließend nach **North America**.  
  
6.  Ziehen Sie die **Date.FiscalDate** -Benutzerhierarchie in das Feld **Zeilenbezeichnungen** , klicken Sie anschließend in der PivotTable auf den nach unten weisenden Pfeil neben **Zeilenbezeichnungen**, und deaktivieren Sie alle Kontrollkästchen bis auf FY 2008, um nur das Geschäftsjahr 2008 anzuzeigen.  
  
7.  Klicken Sie auf OK.  
  
8.  Erweitern Sie **FY 2008**, **H1 FY 2008**und anschließend **Q1 FY 2008**.  
  
     Die folgende Abbildung zeigt eine PivotTable für den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube, für den die Sales Quota-Measuregruppe ordnungsgemäß dimensioniert ist.  
  
     Beachten Sie, dass alle Elemente der Geschäftsquartalsebene über den gleichen Wert verfügen wie die Quartalsebene. Wenn beispielsweise **Q1 FY 2008** verwendet wird, entspricht die Vorgabe von $9,180,000.00 für **Q1 FY 2008** auch dem Wert der einzelnen Elemente. Zu diesem Verhalten kommt es, weil die Auflösung der Daten in der Faktentabelle auf der Quartalsebene und die Auflösung der Date-Dimension auch auf der Quartalsebene liegt. In Lektion 6 lernen Sie, wie die Quartalssumme proportional zu jedem Monat zugeordnet wird.  
  
     ![Sales Quota-Measuregruppe ordnungsgemäß dimensioniert](../../2014/tutorials/media/l5-granularity-7.gif "Sales Quota-Measuregruppe ordnungsgemäß dimensioniert")  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 6: Definieren von Berechnungen] ((Lektion 6 definieren calculations.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionsbeziehungen](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Definieren einer regulären Beziehung und reguläre Beziehungseigenschaften](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md)   
 [Verwenden von Diagrammen im Datenquellensicht-Designers &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  