---
title: 'Tutorial: Kartenbericht (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8d831356-7efa-40cc-ae95-383b3eecf833
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3b456d165ef9c4f09bb040cefb63644efb51c112
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098863"
---
# <a name="tutorial-map-report-report-builder"></a>Lernprogramm: Kartenbericht (Berichts-Generator)
  In diesem Lernprogramm erfahren Sie mehr über die Kartenfunktionen, mit denen Sie Berichtsdaten vor einem geografischen Hintergrund anzeigen können.  
  
 Karten basieren auf räumlichen Daten, die in der Regel aus Punkten, Linien und Polygonen bestehen. Ein Polygon kann z. B. den Umriss eines Countys darstellen, eine Linie eine Straße und ein Punkt die Position eines Orts. Jeder räumliche Datentyp wird auf einer separaten Kartenebene als Satz von Kartenelementen angezeigt.  
  
 Geben Sie zum Verändern der Darstellung von Kartenelementen ein Feld mit Werten an, durch die die Kartenelemente mit analytischen Daten aus einem Dataset verglichen werden. Sie können auch Regeln definieren, durch die Farbe, Größe oder andere Eigenschaften basierend auf Datenbereichen verändert werden.  
  
 In diesem Lernprogramm erstellen Sie einen Kartenbericht, in dem Geschäftsstandorte in Countys des Bundesstaats New York angezeigt werden.  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Was Sie lernen werden  
 In diesem Lernprogramm lernen Sie Folgendes:  
  
1.  [Erstellen einer Karte mit einer Polygonebene im Karten-Assistenten](#Map)  
  
2.  [Hinzufügen einer Kartenpunktebene, um Geschäftsstandorte anzuzeigen](#PointLayer)  
  
3.  [Hinzufügen einer Kartenlinienebene, um eine Route anzuzeigen](#LineLayer)  
  
4.  [Hinzufügen eines Bing Maps-Kachelhintergrunds](#TileLayer)  
  
5.  [Transparente Darstellung einer Ebene](#Transparent)  
  
6.  [Verändern der Countyfarbe basierend auf Umsätzen](#Vary)  
  
    1.  [Erstellen einer Beziehung zwischen räumlichen und analytischen Daten](#Relationship)  
  
    2.  [Festlegen von Farbregeln für Polygone](#ColorRules)  
  
    3.  [Formatieren der Daten in der Farbskala als Währung](#ColorScale)  
  
    4.  [Erstellen einer neuen Legende](#NewLegend)  
  
    5.  [Zuordnen der Legende und Farbregeln](#Associate)  
  
    6.  [Löschen der Farbe aus Countys ohne Daten](#NoData)  
  
7.  [Hinzufügen eines benutzerdefinierten Punkts](#CustomPoint)  
  
8.  [Zentrieren der Kartenansicht](#CenterView)  
  
9. [Hinzufügen eines Berichts Titels](#Title)  
  
10. [Speichern des Berichts](#Save)  
  
> [!NOTE]  
>  In diesem Lernprogramm werden die Schritte für den Assistenten in zwei Verfahren zusammengefasst: ein Verfahren zum Erstellen des Datasets und ein Verfahren zum Erstellen einer Tabelle. Im ersten Tutorial dieser Reihe erhalten Sie ausführliche Anweisungen zum Navigieren zu einem Berichtsserver, Auswählen einer Datenquelle, Erstellen eines Datasets und Ausführen des Assistenten: [Tutorial: Erstellen eines einfachen Tabellenberichts (Berichts-Generator)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Geschätzte Zeit zum Bearbeiten dieses Lernprogramms: 30 Minuten  
  
## <a name="requirements"></a>Anforderungen  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-map-with-a-polygon-layer-from-the-map-wizard"></a><a name="Map"></a>1. Erstellen einer Karte mit einer Polygon Ebene im Karten-Assistenten  
 Führen Sie dem Bericht eine Karte aus dem Kartenkatalog hinzu. Die Karte enthält eine Ebene, auf der die Countys im Bundesstaat New York angezeigt werden. Die Form jedes Countys ist ein Polygon, das auf eingebetteten räumlichen Daten in der Karte aus dem Kartenkatalog basiert.  
  
#### <a name="to-add-a-map-with-the-map-wizard-in-a-new-report"></a>So fügen Sie mit dem Karten-Assistenten eine Karte in einem neuen Bericht hinzu  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
     Das Dialogfeld Erste Schritte wird angezeigt.  
  
    > [!NOTE]  
    >  Wenn das Dialogfeld "Getting Started" nicht angezeigt wird, klicken Sie auf der Schaltfläche "Berichts-Generator" auf **neu**.  
  
2.  Vergewissern Sie sich im linken Bereich, dass der **Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Karten-Assistent**.  
  
4.  Klicken Sie auf **Erstellen**.  
  
5.  **Wählen Sie die Seite Quelle räumlicher Daten aus** , überprüfen Sie, ob **map Gallery** ausgewählt ist.  
  
6.  Erweitern Sie im Kartenkatalog unter **USA**den Eintrag **States by County** , und klicken Sie auf **New York**.  
  
     Im Bereich "Kartenvorschau" wird die Karte der Countys in New York angezeigt.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Übernehmen Sie auf der Seite **Optionen für räumliche Daten und Kartenansicht auswählen** die Standardwerte. Standardmäßig werden Kartenelemente aus einem Kartenkatalog automatisch in die Berichtsdefinition eingebettet.  
  
9. Klicken Sie auf **Weiter**.  
  
10. Überprüfen Sie, ob auf der Seite **Kartenvisualisierung auswählen** der Eintrag **Standardkarte** ausgewählt ist, und klicken Sie auf **Weiter**.  
  
11. Aktivieren Sie auf der Seite **Farbdesign und Datenvisualisierung auswählen** die Option **Bezeichnungen anzeigen** .  
  
12. Falls aktiviert, deaktivieren Sie die Option **Einfarbige Karte** .  
  
13. Klicken Sie in der Dropdown Liste **Datenfeld** auf #COUNTYNAME. Im Kartenvorschaubereich im Assistenten werden die folgenden Elemente angezeigt:  
  
    -   Ein Titel mit dem Text **Kartentitel**  
  
    -   Eine Karte der Countys in New York, in der jedes County mit einer anderen Farbe dargestellt und der Name des Countys angezeigt wird, sofern er über den Countybereich passt  
  
    -   Eine Legende, die einen Titel und eine Liste von Elementen von 1 bis 5 enthält.  
  
    -   Eine Farbskala, die die Werte von 0 bis 160 und keine Farbe enthält.  
  
    -   Eine Entfernungsskala, auf der Kilometer (km) und Meilen (mi) angezeigt werden  
  
14. Klicken Sie auf **Fertig stellen**.  
  
     Die Karte wird der Entwurfsoberfläche hinzugefügt.  
  
15. Klicken Sie auf die Karte, um Sie auszuwählen und den Bereich **Karten Ebenen**anzuzeigen. Im Bereich **Karten Ebenen** wird eine Polygon Ebene vom Ebenentyp **eingebettet**angezeigt. Jedes County ist ein eingebettetes Kartenelement auf dieser Ebene.  
  
    > [!NOTE]  
    >  Wenn Sie den Bereich **Karten Ebenen** nicht sehen, wird er möglicherweise außerhalb der aktuellen Ansicht angezeigt. Verwenden Sie die Bildlaufleiste am unteren Rand des Entwurfsansichtsfensters, um die Ansicht zu ändern. Deaktivieren Sie alternativ auf der Registerkarte **Ansicht** die Option **Eigenschaften** oder **Berichtsdaten** , um eine weitere Entwurfs Oberfläche bereitzustellen.  
  
16. Klicken Sie mit der rechten Maustaste auf den Karten Titel, und klicken Sie dann auf **Titel Eigenschaften**.  
  
17. Ersetzen Sie den Titeltext **durch Umsätze nach Geschäft**.  
  
18. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
19. Zeigen Sie eine Vorschau des Berichts an.  
  
 Im gerenderten Bericht werden der Berichtstitel, der Kartentitel, die Karte und die Entfernungsskala angezeigt. Die Countys befinden sich auf einer Polygonebene der Karte. Alle Countys werden als Polygone mit unterschiedlichen Farben aus einer Farbpalette dargestellt, die Farben sind jedoch keinen Daten zugeordnet. Auf der Entfernungsskala werden Entfernungen sowohl in Kilometern als auch in Meilen angezeigt.  
  
 Die Kartenlegende und die Farbskala werden noch nicht angezeigt, da den Countys noch keine analytischen Daten zugeordnet sind. Sie fügen später in diesem Lernprogramm analytische Daten hinzu.  
  
##  <a name="2-add-a-map-point-layer-to-display-store-locations"></a><a name="PointLayer"></a>2. Hinzufügen einer Karten Punkt Ebene, um Geschäftsstandorte anzuzeigen  
 Fügen Sie mithilfe des Kartenebenen-Assistenten eine Punktebene hinzu, die den Standort von Geschäften anzeigt.  
  
> [!NOTE]  
>  In diesem Lernprogramm sind die Datenwerte in der Abfrage enthalten, sodass keine externe Datenquelle benötigt wird. Die Abfrage ist daher relativ lang. In einer Geschäftsumgebung wären die Daten nicht in der Abfrage enthalten. Dieses Szenario dient nur zu Lernzwecken.  
  
#### <a name="to-add-a-point-layer-based-on-a-sql-server-spatial-query"></a>So fügen Sie eine Punktebene auf Grundlage eines SQL Server-Abfrage nach räumlichen Daten hinzu  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Doppelklicken Sie auf die Karte, um den Bereich **Kartenebenen** anzuzeigen. Klicken Sie auf der Symbolleiste auf die Schaltfläche **Assistent für neue Ebenen**![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard").  
  
3.  Wählen Sie auf der Seite **Quelle räumlicher Daten auswählen** den Eintrag **SQL Server-Abfrage nach räumlichen Daten**aus, und klicken Sie auf **Weiter**.  
  
4.  Klicken Sie auf der Seite **DataSet mit SQL Server räumlichen Daten auswählen** auf **neues Dataset mit SQL Server räumlichen Daten hinzufügen**, und klicken Sie dann auf **weiter**.  
  
5.  Wählen Sie auf der Seite **Verbindung mit einer SQL Server-Datenquelle für räumliche Daten auswählen** eine vorhandene Datenquelle aus, oder navigieren Sie zum Berichtsserver, und wählen Sie eine Datenquelle aus.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Klicken Sie auf der Seite Abfrage entwerfen auf **als Text bearbeiten**.  
  
8.  Fügen Sie den folgenden Text in den Abfragebereich ein:  
  
    ```  
    Select 114 as StoreKey, 'Contoso Albany Store' as StoreName, 1125 as SellingArea, 'Albany' as City, 'Albany' as County,   
     CAST(1000000 as money) as Sales, CAST('POINT(-73.7472924218681 42.6564617079878)' as geography) AS SpatialLocation  
    UNION ALL SELECT 115 AS StoreKey, 'Contoso New York No.1 Store' AS  StoreName, 500 as SellingArea, 'New York' AS City, 'New York City' as County,  
     CAST('2000000' as money) as Sales, CAST('POINT(-73.9922069374483 40.7549638237402)' as geography) AS SpatialLocation  
    UNION ALL Select 116 as StoreKey, 'Contoso Rochester No.1 Store' as StoreName, 462 as SellingArea, 'Rochester' as City,  'Monroe' as County,    
     CAST(3000000 as money) as Sales, CAST('POINT(-77.624041566786 43.1547066024338)' as geography)  AS SpatialLocation  
    UNION ALL Select 117 as StoreKey, 'Contoso New York No.2 Store' as StoreName, 700 as SellingArea, 'New York' as City,'New York City' as County,    
      CAST(4000000 as money) as Sales, CAST('POINT(-73.9712488 40.7830603)' as geography) AS SpatialLocation  
    UNION ALL Select 118 as StoreKey, 'Contoso Syracuse Store' as StoreName, 680 as SellingArea, 'Syracuse' as City, 'Onondaga' as County,  
     CAST(5000000 as money) as Sales, CAST('POINT(-76.1349120532546 43.0610223535974)' as geography) AS SpatialLocation  
    UNION ALL Select 120 as StoreKey, 'Contoso Plattsburgh Store' as StoreName, 560 as SellingArea, 'Plattsburgh' as City,  'Clinton' as County,  
     CAST(6000000 as money) as Sales, CAST('POINT(-73.4728622833178 44.7028831413324)' as geography) AS SpatialLocation  
    UNION ALL Select 121 as StoreKey, 'Contoso Brooklyn Store' as StoreName, 1125 as SellingArea, 'Brooklyn' as City, 'New York City' as County,  
     CAST(7000000 as money) as Sales, CAST('POINT (-73.9638533447143 40.6785123489351)' as geography) AS SpatialLocation  
    UNION ALL Select 122 as StoreKey, 'Contoso Oswego Store' as StoreName, 500 as SellingArea, 'Oswego' as City, 'Oswego' as County,    
     CAST(8000000 as money) as Sales, CAST('POINT(-76.4602850815536 43.4353224527794)' as geography) AS SpatialLocation  
    UNION ALL Select 123 as StoreKey, 'Contoso Ithaca Store' as StoreName, 460 as SellingArea, 'Ithaca' as City, 'Tompkins' as County,  
     CAST(9000000 as money) as Sales, CAST('POINT(-76.5001866085881 42.4310489934743)' as geography) AS SpatialLocation  
    UNION ALL Select 124 as StoreKey, 'Contoso Rochester No.2 Store' as StoreName, 700 as SellingArea, 'Rochester' as City, 'Monroe' as County,    
     CAST(100000 as money) as Sales, CAST('POINT(-77.6240415667866 43.1547066024338)' as geography) AS SpatialLocation  
    UNION ALL Select 125 as StoreKey, 'Contoso Queens Store' as StoreName, 700 as SellingArea,'Queens' as City, 'New York City' as County,  
     CAST(500000 as money) as Sales, CAST('POINT(-73.7930979029883 40.7152781765927)' as geography) AS SpatialLocation  
    UNION ALL Select 126 as StoreKey, 'Contoso Elmira Store' as StoreName, 680 as SellingArea, 'Elmira' as City, 'Chemung' as County,  
     CAST(800000 as money) as Sales, CAST('POINT(-76.7397414783301 42.0736492742663)' as geography) AS SpatialLocation  
    UNION ALL Select 127 as StoreKey, 'Contoso Poestenkill Store' as StoreName, 455 as SellingArea, 'Poestenkill' as City, 'Rensselaer' as County,    
    CAST(1500000 as money) as Sales, CAST('POINT(-73.5626737425063 42.6940551238618)' as geography) AS SpatialLocation  
    ```  
  
9. Klicken Sie auf der Symbolleiste des Abfrage-Designers auf **Ausführen** (**!**).  
  
     Das Resultset enthält sieben Spalten: "StoreKey", "StoreName", "SellingArea", "City", "County", "Sales" und "SpatialLocation". Diese Daten stellen einen Satz von Geschäften im Bundesstaat New York dar, in denen Verbrauchsgüter verkauft werden. Jede Zeile im Resultset enthält eine Geschäfts-ID, den Geschäftsnamen, die für die Produkte verfügbare Ausstellfläche, den Ort und das County, in dem sich das Geschäft befindet, den Jahresumsatz und die räumliche Position in Längen- und Breitengrad. Die Ausstellfläche liegt zwischen 455 Quadratfuß und 1125 Quadratfuß.  
  
10. Klicken Sie auf **Weiter**.  
  
     Das Berichtsdataset mit dem Namen "DataSet1" wird für Sie erstellt. Nachdem Sie den Assistenten abgeschlossen haben, können Sie die zugehörige Feldauflistung in den Berichtsdaten anzeigen.  
  
11. Überprüfen Sie auf der Seite **Optionen für räumliche Daten und Kartenansicht auswählen** , ob das **räumliche Feld** ist `SpatialLocation` und der **Ebenentyp** **Punkt**ist. Übernehmen Sie die anderen Standardwerte auf dieser Seite.  
  
     In der Kartensicht werden Kreise angezeigt, die den Standort jedes Geschäfts markieren.  
  
12. Klicken Sie auf **Weiter**.  
  
13. Geben Sie einen Kartentyp an, in dem nach analytischen Daten variierende Marker angezeigt werden. Klicken Sie auf der Seite Karten Visualisierung auswählen auf **analytische markerkarte**, und klicken Sie dann auf **weiter**.  
  
14. Klicken Sie auf der Seite **analytisches Dataset auswählen** auf DataSet1. Dieses Dataset enthält sowohl analytische Daten als auch räumliche Daten, die auf der neuen Punktebene angezeigt werden.  
  
15. Klicken Sie auf **Weiter**.  
  
16. Deaktivieren Sie auf der Seite **Farbdesign und Datenvisualisierung auswählen** die Option **Markerfarben zum Visualisieren von Daten verwenden** , und aktivieren Sie dann die Option **Markertypen zum Anzeigen von Daten verwenden**.  
  
17. Wählen Sie `[Sum(SellingArea)]` unter **Datenfeld**aus, um die Markertypen nach der Größe des Bereichs zu verändern, den ein Speicher für die Anzeige der Produkte reserviert.  
  
18. Klicken Sie auf **Fertig stellen**.  
  
     Die Kartenebene wird dem Bericht hinzugefügt. Auf der Legende werden Markertypen basierend auf den SellingArea-Werten angezeigt.  
  
     Doppelklicken Sie auf die Karte, um den Bereich **Kartenebenen** anzuzeigen. Im Bereich **Kartenebenen** wird eine neue Ebene PointLayer1 mit dem räumlichen Datenquellentyp **DataRegion**angezeigt.  
  
19. Fügen Sie einen Legendentitel hinzu. Klicken Sie mit der rechten Maustaste auf den Legenden Titel, und klicken Sie dann auf **Legenden Titel Eigenschaften**.  
  
20. Löschen Sie den Titel, und geben Sie **Anzeigebereich (quadratische Füße)** ein.  
  
21. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
22. Zeigen Sie die vom Assistenten festgelegten Standardwerte an. Klicken Sie im Bereich **Karten Ebenen**mit der rechten Maustaste auf die Punkt Ebene, und klicken Sie dann auf **Regel für Markertyp**.  
  
     Auf der Registerkarte **Allgemein** werden die Marker in der Reihenfolge aufgelistet, in der Sie in der Legende angezeigt werden. Auf der Registerkarte **Verteilung** beträgt die Anzahl der Unterbereiche 5. Auf der Registerkarte **Legende** wird der Legenden Text so festgelegt, dass der Start-und Endwert in jedem Bereich angezeigt wird.  
  
23. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
24. Zeigen Sie eine Vorschau des Berichts an.  
  
 Auf der Karte werden die Standorte von Geschäften im Bundesstaat New York angezeigt. Der Markertyp für jedes Geschäft basiert auf der Aufstellfläche. Fünf Bereiche wurden automatisch für die Aufstellfläche berechnet.  
  
##  <a name="3-add-a-map-line-layer-to-display-a-route"></a><a name="LineLayer"></a>3. Hinzufügen einer Karten Linien Ebene, um eine Route anzuzeigen  
 Fügen Sie mithilfe des Kartenebenen-Assistenten eine Kartenebene hinzu, die eine Route zwischen zwei Geschäften anzeigt. In diesem Lernprogramm wird der Weg für drei Geschäftsstandorte erstellt. In einer Geschäftsanwendung könnte es sich bei dem Weg um die beste Route zwischen Geschäften handeln.  
  
#### <a name="to-add-a-line-layer-to-map"></a>So fügen Sie der Karte eine Linienebene hinzu  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Doppelklicken Sie auf die Karte, um den Bereich **Kartenebenen** anzuzeigen. Klicken Sie auf der Symbolleiste auf **Assistent für neue Ebenen**.  
  
3.  Wählen Sie auf der Seite **Quelle räumlicher Daten auswählen** **SQL Server räumliche Abfrage** aus, und klicken Sie auf **weiter**.  
  
4.  Klicken Sie auf der Seite **Dataset mit räumlichen SQL Server-Daten auswählen** auf **Neues Dataset mit räumlichen SQL Server-Daten hinzufügen** anschließend auf **Weiter**.  
  
5.  Wählen Sie unter **Verbindung mit einer SQL Server räumliche Datenquelle auswählen**die Datenquelle DataSource1 aus, die Sie im ersten Verfahren erstellt haben.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Klicken Sie auf der Seite **Abfrage entwerfen** auf **als Text bearbeiten**. Der Abfrage-Designer wechselt in den textbasierten Modus.  
  
8.  Fügen Sie den folgenden Text in den Abfragebereich ein:  
  
    ```  
    SELECT N'Path' AS Name, CAST('LINESTRING(  
       -76.5001866085881 42.4310489934743,  
       -76.4602850815536 43.4353224527794,  
       -73.4728622833178 44.7028831413324)' AS geography) as Route  
    ```  
  
9. Klicken Sie auf **Weiter**.  
  
     Auf der Karte wird ein Weg angezeigt, der drei Geschäfte verbindet.  
  
10. Überprüfen Sie auf der Seite **Optionen für räumliche Daten und Kartenansicht auswählen** , ob für **Räumliches Feld** der Wert **Route** und für **Ebenentyp** der Wert **Linie**ausgewählt ist. Übernehmen Sie die anderen Standardwerte.  
  
     In der Kartensicht wird ein Weg von einem Geschäft im nördlichen Teil des Bundesstaats New York zu einem Geschäft im südlichen Teil des Bundesstaats New York angezeigt.  
  
11. Klicken Sie auf **Weiter**.  
  
12. Klicken Sie auf der Seite **Kartenvisualisierung auswählen** auf **Standardkarte (Linien)** und anschließend auf **Weiter**.  
  
13. Aktivieren Sie unter **Farbdesign und Datenvisualisierung auswählen**die Option **Einfarbige Karte**. Der Weg wird mit einer einzelnen Farbe angezeigt, die auf dem ausgewählten Design basiert.  
  
14. Klicken Sie auf **Fertig stellen**.  
  
 In der Karte wird eine neue Linien Ebene mit **DataSet**vom Typ räumlicher Datenquelle angezeigt. In diesem Beispiel stammen die räumlichen Daten aus einem Dataset, aber der Linie sind keine analytischen Daten zugeordnet.  
  
##  <a name="4-add-a-bing-maps-tile-background"></a><a name="TileLayer"></a>4. Hinzufügen eines Kachel Hintergrunds für die Kachel  
 Fügen Sie eine Kartenebene hinzu, die einen Bing Maps-Kachelhintergrund anzeigt.  
  
#### <a name="to-add-a-virtual-earth-tile-background"></a>So fügen Sie einen Virtual Earth-Kachelhintergrund hinzu  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Doppelklicken Sie auf die Karte, um den Bereich **Kartenebenen** anzuzeigen. Klicken Sie auf der Symbolleiste auf **Ebene hinzufügen**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer").  
  
3.  Klicken Sie in der Dropdownliste auf **Kachelebene**.  
  
     Die letzte Ebene im Bereich **Kartenebene** ist TileLayer1. Standardmäßig zeigt die Kachelebene das Straßenkartenformat an.  
  
    > [!NOTE]  
    >  Sie können auch im Assistenten auf der Seite **Optionen für räumliche Daten und Kartenansicht auswählen** eine Kachelebene hinzufügen. Wählen Sie dazu **Bing Maps-Hintergrund für diese Kartenansicht hinzufügen**aus. In einem gerenderten Bericht zeigt der Kachelhintergrund Bing Maps-Kacheln für den aktuellen Kartenviewport-Mittelpunkt und die aktuelle Zoomstufe an.  
  
4.  Klicken Sie in "TileLayer1" auf den Pfeil nach unten, und klicken Sie dann auf **Kachel Eigenschaften**.  
  
5.  Wählen Sie unter **Typ**die Option **Luftbild**aus. Das Luftbild enthält keinen Text.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="5-make-a-layer-transparent"></a><a name="Transparent"></a>5. eine Ebene transparent machen  
 Sie können die Reihenfolge von Ebenen und die Transparenz jeder Ebene anpassen, um die Elemente auf einer Ebene durch andere Ebenen durchscheinen zu lassen und den gewünschten Transparenzeffekt zu erzielen.  
  
#### <a name="to-set-the-transparency-of-a-layer"></a>So legen Sie die Transparenz einer Ebene fest  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Doppelklicken Sie auf die Karte, um den Bereich **Kartenebenen** anzuzeigen.  
  
3.  Klicken Sie in PolygonLayer1 auf den Pfeil nach unten, und klicken Sie dann auf **ebenendungen**. Das Dialogfeld **Polygonebeneneigenschaften von Karten** wird geöffnet.  
  
4.  Klicken Sie auf **Sichtbarkeit**.  
  
5.  Geben Sie unter **Transparenz (%)** den Typ **30**ein.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 Auf der Entwurfsoberfläche werden die Countys halbtransparent dargestellt.  
  
##  <a name="6-vary-county-color-based-on-sales"></a><a name="Vary"></a>6. verändern der Bezirks Farbe basierend auf den Verkäufen  
 Jedes County in der Polygonebene hat eine andere Farbe, da der Berichtsprozessor automatisch auf der Grundlage des Designs, das Sie auf der letzten Seite des Karten-Assistenten ausgewählt haben, einen Farbwert aus der Farbpalette zuweist.  
  
 In den folgenden Schritten geben Sie eine Farbregel an, um bestimmte Farben einem Bereich von Geschäftsumsätzen für jedes County zuzuordnen. Die Farben rot, gelb und grün geben relativ hohe, mittlere bzw. niedrige Umsätze an. Formatieren Sie die Farbskala, um Währungswerte anzuzeigen. Zeigen Sie die Jahresumsatzbereiche in einer neuen Legende an. Verwenden Sie für Countys ohne Geschäfte keine Farbe, um anzuzeigen, dass keine zugeordneten Daten vorliegen.  
  
###  <a name="6a-build-a-relationship-between-spatial-and-analytical-data"></a><a name="Relationship"></a>6a. Erstellen einer Beziehung zwischen räumlichen und analytischen Daten  
 Um die Countyformen auf der Grundlage analytischer Daten farblich zu unterscheiden, müssen Sie zuerst die analytischen Daten den räumlichen Daten zuordnen. In diesem Lernprogramm verwenden Sie zu diesem Zweck den Countynamen.  
  
##### <a name="to-build-a-relationship-between-spatial-data-and-analytical-data"></a>So erstellen Sie eine Beziehung zwischen räumlichen Daten und analytischen Daten  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Doppelklicken Sie auf die Karte, um den Bereich **Kartenebenen** anzuzeigen.  
  
3.  Klicken Sie in PolygonLayer1 auf den Pfeil nach unten, und klicken Sie dann auf **ebenendungen**. Das Dialogfeld **Polygonebeneneigenschaften von Karten** wird geöffnet.  
  
4.  Klicken Sie auf **Analytische Daten**.  
  
5.  Wählen Sie in der Dropdownliste den Eintrag "DataSet1" aus. Dieses Dataset wurde vom Assistenten erstellt, als Sie die Abfrage räumlicher Daten für die Countys angegeben haben.  
  
6.  Klicken Sie unter zu Übereinstimmungs **Felder auf** **Hinzufügen**. Eine neue Zeile wird hinzugefügt.  
  
7.  Klicken Sie in **aus räumlichem DataSet**in der Dropdown Liste auf zählname.  
  
8.  Klicken Sie unter **aus analytisches DataSet**in der Dropdown Liste auf [County].  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Zeigen Sie eine Vorschau des Berichts an.  
  
 Durch die Angabe eines Übereinstimmungsfelds aus der räumlichen Datenquelle und aus dem analytischen Dataset kann der Berichtsprozessor analytische Daten auf Grundlage der Kartenelemente gruppieren. Bei einem datengebundenen Kartenelement wird eine erfolgreiche Übereinstimmung für die von Ihnen angegebenen Werte erzielt.  
  
 Jedem County mit einem Geschäft ist eine Farbe zugeordnet, die auf der Farbpalette für das im Assistenten ausgewählte Format basiert.  
  
###  <a name="6b-specify-color-rules-for-polygons"></a><a name="ColorRules"></a>6B. Festlegen von Farbregeln für Polygone  
 Zum Erstellen einer Regel, die die Farbe jedes Countys basierend auf dem Geschäftsumsatz verändert, müssen Sie die Bereichswerte, die Anzahl anzuzeigender Einteilungen innerhalb dieses Bereichs und die zu verwendenden Farben angeben.  
  
##### <a name="to-specify-color-rules-for-all-polygons-that-have-associated-data"></a>So geben Sie Farbregeln für alle Polygone mit zugeordneten Daten an  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Klicken Sie in PolygonLayer1 auf den Pfeil nach unten, und klicken Sie dann auf **Polygon Farbregel**. Das Dialogfeld **Farbregeleigenschaften der Karte** wird geöffnet. Beachten Sie, dass die Farbregeloption **Daten mithilfe der Farbpalette anzeigen** ausgewählt ist. Diese Option wurde vom Assistenten festgelegt.  
  
3.  Aktivieren Sie **Daten mithilfe von Farbbereichen anzeigen**. Die Palettenoption wird durch die Optionen für Startfarbe, mittlere Farbe und Endfarbe ersetzt.  
  
4.  Definieren Sie Bereichswerte für die Umsätze pro County. Wählen Sie unter **Datenfeld**den Eintrag `[Sum(Sales)]`in der Dropdownliste aus.  
  
5.  Ändern Sie den Ausdruck wie folgt, um das Format zur Anzeige der Währung in Tausendern zu ändern: `=Sum(Fields!Sales.Value)/1000`  
  
6.  Ändern Sie **Startfarbe** in **Rot**.  
  
7.  Ändern Sie **Endfarbe** in **Grün**.  
  
     **Rot** stellt niedrige Umsatzwerte dar, **Gelb** stellt mittlere Umsatzwerte dar, und **Grün** stellt hohe Umsatzwerte dar. Der Berichtsprozessor berechnet einen Bereich von Farben auf der Grundlage dieser Werte und der Optionen, die Sie auf der Seite **Verteilung** auswählen.  
  
8.  Klicken Sie auf **Verteilung**.  
  
9. Überprüfen Sie, ob der Verteilungstyp **Optimal**lautet. Für den Ausdruck aus Schritt 5 werden die Werte durch die optimale Verteilung in Teilbereiche aufgeteilt, deren Elementanzahl und Umfang jeweils gleich sind.  
  
10. Übernehmen Sie die Standardwerte für andere Optionen auf dieser Seite. Wenn Sie den optimalen Verteilungstyp auswählen, wird die Anzahl der Teilbereiche bei der Berichtausführung berechnet.  
  
11. Klicken Sie auf **Legende**.  
  
12. Überprüfen Sie, ob unter **Farbskalaoptionen**der Wert **In Farbskala anzeigen** ausgewählt ist.  
  
13. Wählen Sie unter **In dieser Legende anzeigen**in der Dropdownliste die Leerzeile aus. Zurzeit zeigen Sie die Farbbereiche nur in der Farbskala an.  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 Auf der Farbskala werden fünf Farben angezeigt: rot, orange, gelb, gelbgrün und grün. Jede Farbe stellt einen Umsatzbereich dar, der automatisch auf Grundlage der Umsätze nach County berechnet wird.  
  
###  <a name="6c-format-the-data-in-the-color-scale-as-currency"></a><a name="ColorScale"></a>6C. Formatieren der Daten in der Farbskala als Währung  
 Für Daten wird standardmäßig ein allgemeines Format verwendet. Sie können benutzerdefinierte Formate anwenden.  
  
##### <a name="to-set-the-format-for-the-color-scale"></a>So legen Sie das Format für die Farbskala fest  
  
1.  Klicken Sie mit der rechten Maustaste auf die Farbskala, und klicken Sie dann auf **Farbskala Eigenschaften**.  
  
2.  Klicken Sie auf **Number**.  
  
3.  Klicken Sie unter **Kategorie**auf **Währung**.  
  
4.  Geben Sie unter **Dezimalstellen**den Wert **0**ein. Dieses Währungsformat enthält keine Dezimalstellen.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Zeigen Sie eine Vorschau des Berichts an.  
  
 Die Farbskala zeigt für jeden Bereich den Jahresumsatz im Währungsformat an.  
  
###  <a name="6d-create-a-new-legend"></a><a name="NewLegend"></a>6d. Erstellen einer neuen Legende  
 Standardmäßig werden alle Regeln in der ersten Legende angezeigt. Sie können Legenden hinzufügen, um die Anzeige für eine Karte zu verbessern.  
  
 Das Ändern der Standardanzeige umfasst zwei Schritte: Erstellen Sie eine neue Legende, und ordnen Sie dann die Regelergebnisse für eine Kartenebene der neuen Legende zu.  
  
##### <a name="to-create-a-new-legend"></a>So erstellen Sie eine neue Legende  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Klicken Sie mit der rechten Maustaste außerhalb des Viewports auf die Karte, und klicken Sie dann auf **Legende hinzufügen**. Der Karte wird eine neue Legende an einer Standardposition hinzugefügt.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Legende, und klicken Sie dann auf **Legenden Eigenschaften**.  
  
4.  Klicken Sie unter **Positions Optionen**auf den Speicherort, der angibt, wo die Legende relativ zum Viewport angezeigt werden soll. Die Karte auf der Entwurfsoberfläche wird so geändert, dass sie den Effekt der Auswahl anzeigt.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Klicken Sie auf **Titel** in der Legende, um den Legenden Titel auszuwählen.  
  
7.  Klicken Sie erneut auf **Titel** , um den Insert-Modus für den Text einzugeben. Ersetzen Sie **Title** by **Sales (Tausender)**, und klicken Sie dann außerhalb des Texts.  
  
 Die Legende wird erweitert, um den Titel anzuzeigen.  
  
###  <a name="6e-associate-legend-and-color-rules"></a><a name="Associate"></a>6E. Zuordnen der Legende und Farbregeln  
 In jeder Legende können ein oder mehrere Sätze von Regelergebnissen angezeigt werden.  
  
##### <a name="to-associate-a-legend-with-color-rules"></a>So ordnen Sie einer Legende Farbregeln zu  
  
1.  Doppelklicken Sie auf die Karte, um den Bereich **Kartenebenen** anzuzeigen.  
  
2.  Klicken Sie in PolygonLayer1 auf den Pfeil nach unten, und klicken Sie dann auf **Polygon Farbregel**. Das Dialogfeld **Farbregeleigenschaften der Karte** wird geöffnet.  
  
3.  Klicken Sie auf **Legende**.  
  
4.  Deaktivieren Sie unter **Farbskalaoptionen die Option** **in Farbskala anzeigen**.  
  
5.  Wählen Sie in **Legenden Optionen**in der Dropdown Liste legend2 aus aus. Die Legendentextoption wird angezeigt. Standardmäßig wird Legendentext mit einer allgemeinen [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Formatzeichenfolge formatiert. Die 0 in N0 steht für keine Dezimalstellen.  
  
6.  Verwenden Sie in **Legenden Text**das folgende Format, um eine Währung ohne Dezimalziffern anzugeben:`#FROMVALUE {C0} - #TOVALUE {C0}`  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Auf der Entwurfsoberfläche werden die Farbbereiche mit als Währung formatierten Beispieldaten in der Legende angezeigt.  
  
8.  Zeigen Sie eine Vorschau des Berichts an.  
  
 Die Countys mit zugeordneten Geschäften und Umsätzen werden entsprechend den Farbregeln angezeigt. Countys ohne Umsätze ist keine Farbe zugeordnet.  
  
###  <a name="6f-change-color-for-counties-with-no-data"></a><a name="NoData"></a>6f. Ändern der Farbe für Countys ohne Daten  
 Sie können die Standardanzeigeoptionen für alle Kartenelemente auf einer Ebene festlegen. Farbregeln haben Vorrang vor diesen Anzeigeoptionen.  
  
##### <a name="to-set-the-display-properties-for-all-elements-on-a-layer"></a>So legen Sie die Anzeigeeigenschaften für alle Elemente auf einer Ebene fest  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Doppelklicken Sie auf die Karte, um den Bereich **Kartenebenen** anzuzeigen.  
  
3.  Klicken Sie in „PolygonLayer1“ auf den Pfeil nach unten und anschließend auf **Polygoneigenschaften**. Das Dialogfeld **Polygoneigenschaften von Karten** wird geöffnet. Bevor regelbasierte Anzeigeoptionen angewendet werden, gelten in diesem Dialogfeld festgelegte Anzeigeoptionen für alle Polygone auf der Ebene.  
  
4.  Klicken Sie auf **Ausfüllen**.  
  
5.  Überprüfen Sie, ob der Füllstil vollständig ist **.** festgelegt ist. Farbverläufe und Muster gelten für alle Farben.  
  
6.  Klicken Sie unter **Farbe**auf den Pfeil nach unten, und klicken Sie dann auf **hellstahlblau**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Zeigen Sie eine Vorschau des Berichts an.  
  
 Countys ohne zugeordnete Daten werden blau dargestellt. Nur Countys, denen analytische Daten zugeordnet sind, werden durch **grüne** Farben **aus den von** Ihnen angegebenen Farb Regeln angezeigt.  
  
##  <a name="7-add-a-custom-point"></a><a name="CustomPoint"></a>7. Hinzufügen eines benutzerdefinierten Punkts  
 Geben Sie einen Punkt an, und verwenden Sie den Markertyp " **PushPin** ", um einen neuen Speicher darzustellen, der noch nicht erstellt wurde.  
  
#### <a name="to-add-a-custom-point"></a>So fügen Sie einen benutzerdefinierten Punkt hinzu  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Doppelklicken Sie auf die Karte, um den Bereich **Kartenebenen** anzuzeigen. Klicken Sie auf der Symbolleiste auf **Ebene hinzufügen**, und klicken Sie dann auf **Punkt Ebene**.  
  
     Der Karte wird eine neue Punktebene hinzugefügt. Standardmäßig verfügt die Punktebene über den räumlichen Datentyp **Eingebettet**.  
  
3.  Klicken Sie in PointLayer2 auf den Pfeil nach unten, und klicken Sie dann auf **Punkt hinzufügen**.  
  
4.  Bewegen Sie den Zeiger über den Kartenviewport. Der Cursor verändert sich zu einem Fadenkreuz.  
  
5.  Klicken Sie auf den Ort auf der Karte, an dem Sie einen Punkt hinzufügen möchten. In diesem Lernprogramm klicken Sie auf eine Position in einem County neben dem Start der Route. Der Ebene wird an der Position, an der Sie geklickt haben, ein mit einem Kreis markierter Punkt hinzugefügt. Standardmäßig ist der Punkt ausgewählt.  
  
6.  Klicken Sie mit der rechten Maustaste auf den hinzugefügten Punkt, und klicken Sie anschließend auf **Eigenschaften für eingebettete Punkte**.  
  
7.  Wählen Sie die Option **Punkt Optionen für diese Ebene überschreiben aus**. Im Dialogfeld werden weitere Seiten angezeigt. Hier festgelegte Werte haben Vorrang vor Anzeigeoptionen für die Ebene oder für Farbregeln.  
  
8.  Klicken Sie auf **Marker**.  
  
9. Wählen Sie unter **Markertyp**die Option **Star**aus.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Zeigen Sie eine Vorschau des Berichts an.  
  
 Der neue Punkt, den Sie hinzugefügt haben, wird als **Stern**angezeigt.  
  
#### <a name="to-add-a-label-for-the-custom-point"></a>So fügen Sie eine Bezeichnung für den benutzerdefinierten Punkt hinzu  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Klicken Sie mit der rechten Maustaste auf den soeben hinzugefügten Punkt, und klicken Sie dann auf **Eigenschaften von eingebetteten Punkten**  
  
3.  Klicken Sie auf **Bezeichnungen**.  
  
4.  Geben Sie unter Bezeichnungs **Text**den **Wert New Store**ein.  
  
5.  Klicken Sie unter **Platzierung**auf **Oben**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Zeigen Sie eine Vorschau des Berichts an.  
  
 Die Bezeichnung wird über dem Geschäftsstandort angezeigt.  
  
##  <a name="center-the-map-view"></a><a name="CenterView"></a>Zentrieren der Kartenansicht  
 Ändern Sie den Mittelpunkt und die Zoomstufe des Kartenviewports.  
  
#### <a name="to-change-the-viewport"></a>So ändern Sie den Viewport  
  
1.  Klicken Sie mit der rechten Maustaste auf den Kartenviewport, und klicken Sie dann auf **Viewporteigenschaften**.  
  
2.  Klicken Sie auf **zentrieren und Zoomen**.  
  
3.  Vergewissern Sie sich, dass die Option **einen Ansichts Mittelpunkt und eine Zoomstufe festlegen** ausgewählt ist.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Klicken Sie mit der linken Maustaste auf den Kartenviewport, und ziehen Sie den Mittelpunkt des Viewports an die gewünschte Position.  
  
6.  Ändern Sie die Zoomstufe des Viewports mithilfe des Mausrads.  
  
7.  Zeigen Sie eine Vorschau des Berichts an.  
  
 In der Entwurfsansicht basieren die Karte auf der Anzeigeoberfläche und die Ansicht auf Beispieldaten. Im gerenderten Bericht wird die Kartenansicht in der angegebenen Ansicht zentriert.  
  
##  <a name="add-a-report-title"></a><a name="Title"></a>Hinzufügen eines Berichts Titels  
  
#### <a name="to-add-a-report-title"></a>So fügen Sie einen Berichtstitel hinzu  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf **Zum Hinzufügen eines Titels klicken**.  
  
2.  Geben Sie **Umsätze in den Geschäften in New York** ein, und klicken Sie anschließend auf den Bereich außerhalb des Textfelds.  
  
 Dieser Titel wird am Anfang des Berichts angezeigt. Elemente über dem Berichtshauptteil entsprechen einer Berichtskopfzeile, wenn keine Seitenkopfzeile definiert ist.  
  
##  <a name="save-the-report"></a><a name="Save"></a>Speichern des Berichts  
  
#### <a name="to-save-the-report"></a>So speichern Sie den Bericht  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Klicken Sie auf die Schaltfläche Berichts-Generator und anschließend auf **Speichern unter**.  
  
3.  Geben Sie im Feld **Name**den Namen **Umsätze der Geschäfte in New York**ein.  
  
 Klicken Sie auf **Speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Damit ist die exemplarische Vorgehensweise für das Hinzufügen einer Karte zum Bericht abgeschlossen.  
  
 Weitere Informationen finden Sie unter [Maps &#40;Berichts-Generator und SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) und im Blogeintrag [kartographic-Anpassung räumlicher Daten für SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=152771) auf Blogs.msdn.com.  
  
 Weitere Tutorials finden Sie unter [Tutorials &#40;Berichts-Generator&#41;](report-builder-tutorials.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)   
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)   
 [Karten-Assistent und Karten Ebenen-Assistent &#40;Berichts-Generator und SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)   
 [Unterschiedliche Polygon-, Linien- und Punktanzeigen bei der Verwendung von Regeln und analytischen Daten &#40;Berichts-Generator und SSRS&#41;](report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
