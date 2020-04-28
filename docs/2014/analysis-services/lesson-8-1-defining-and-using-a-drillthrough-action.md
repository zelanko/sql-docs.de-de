---
title: Definieren und Verwenden von Drillthrough-Aktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3765f865-2b93-44be-b290-28e3815d5ecb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cbc9ad315792fc4198988a53713f978ff119d2ee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "69493825"
---
# <a name="defining-and-using-a-drillthrough-action"></a>Definieren und Verwenden einer Drillthroughaktion
  Das Dimensionieren von Faktendaten mit einer Faktendimension, ohne die von der Abfrage zurückgegebenen Daten richtig zu filtern, kann bei Abfragen zu einer verminderten Leistung führen. Um dies zu vermeiden, können Sie eine Drillthroughaktion definieren, mit der die Gesamtanzahl der Zeilen, die zurückgegeben werden, reduziert wird. Dadurch wird die Abfrageleistung erheblich verbessert.  
  
 Im Rahmen der Tasks in diesem Thema definieren Sie eine Drillthroughaktion, die Bestelldetailinformationen für Verkäufe an Kunden über das Internet zurückgibt.  
  
## <a name="defining-the-drillthrough-action-properties"></a>Definieren der Eigenschaften einer Drillthroughaktion  
  
1.  Klicken Sie im Cube-Designer für den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube auf die Registerkarte **Aktionen** .  
  
     Die Registerkarte **Aktionen** umfasst mehrere Bereiche. Auf der linken Seite der Registerkarte werden die Bereiche **Aktionsplaner** und **Berechnungstools** angezeigt. Rechts neben diesen beiden Bereichen befindet sich der **Anzeigebereich** , der die Details der im Bereich **Aktionsplaner** ausgewählten Aktion enthält.  
  
     In der folgenden Abbildung ist die Registerkarte **Aktionen** des Cube-Designers dargestellt.  
  
     ![Aktionen (Registerkarte) des Cube-Designers](../../2014/tutorials/media/l8-action1.gif "Aktionen (Registerkarte) des Cube-Designers")  
  
2.  Klicken Sie auf der Symbolleiste der Registerkarte **Aktionen** auf **Neue Drillthroughaktion** .  
  
     Es wird eine leere Aktionsvorlage im Anzeigebereich angezeigt.  
  
     ![Leere Aktionsvorlage im Anzeigebereich](../../2014/tutorials/media/l8-action2.gif "Leere Aktionsvorlage im Anzeigebereich")  
  
3.  Ändern Sie **Name** `Internet Sales Details Drillthrough Action`im Feld Name den Namen dieser Aktion in.  
  
4.  Wählen Sie in der Liste **Measuregruppenelemente** die Option **Internet Sales**aus.  
  
5.  Wählen Sie im Feld **Drillthroughspalten** in der Liste **Dimensionen** die Option **Internet Sales Order Details** aus.  
  
6.  Aktivieren Sie in der Liste **Rückgabespalten** die Kontrollkästchen für **Elementbeschreibung** und **Bestellnummer** , und klicken Sie anschließend auf **OK**. In der folgenden Abbildung ist die Aktionsvorlage zu sehen, wie sie zum jetzigen Zeitpunkt in dieser Prozedur aussehen sollte.  
  
     ![Drillthroughspalten (Feld)](../../2014/tutorials/media/l8-action3.gif "Drillthroughspalten (Feld)")  
  
7.  Erweitern Sie das Feld **Weitere Eigenschaften** , wie in der folgenden Abbildung dargestellt.  
  
     ![Weitere Eigenschaften (Feld)](../../2014/tutorials/media/l8-action4.gif "Weitere Eigenschaften (Feld)")  
  
8.  Geben `10`Sie im Feld **Maximale Zeilen** Anzahl ein.  
  
9. Geben `Drillthrough to Order Details...`Sie im Feld **Beschriftung** den Text ein.  
  
     Durch diese Einstellungen wird die Anzahl der zurückgegebenen Zeilen beschränkt und die Beschriftung angegeben, die im Clientanwendungsmenü angezeigt wird. In der folgenden Abbildung werden diese Einstellungen im Feld **Weitere Eigenschaften** dargestellt.  
  
     ![Weitere Eigenschaften (Feld)](../../2014/tutorials/media/l8-action5.gif "Weitere Eigenschaften (Feld)")  
  
## <a name="using-the-drillthrough-action"></a>Verwenden der Drillthroughaktion  
  
1.  Klicken Sie im Menü **Erstellen** auf **Analysis Services Tutorial bereitstellen**.  
  
2.  Klicken Sie nach erfolgreichem Abschluss der Bereitstellung im Cube-Designer für den **Tutorial-Cube auf die Registerkarte** Browser [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und anschließend auf die Schaltfläche **Verbindung wiederherstellen** .  
  
3.  Starten Sie Excel.  
  
4.  Fügen Sie dem Bereich „Werte“ das **Internet Sales-Sales Amount** -Measure hinzu.  
  
5.  Fügen Sie dem Bereich **Berichtsfilter** die benutzerdefinierte **Customer Geography** -Hierarchie aus dem Ordner **Location** in der **Customer** -Dimension hinzu.  
  
6.  Fügen Sie in der PivotTable in **Customer Geography**einen Filter hinzu, durch den ein einzelner Kunde ausgewählt wird. Erweitern Sie die Optionen **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**, aktivieren Sie das Kontrollkästchen für **Adam Powell**, und klicken Sie anschließend auf **OK**.  
  
     Im Bereich Daten werden die gesamten Produktverkäufe von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] an Adam Powell angezeigt.  
  
7.  Klicken Sie mit der rechten Maustaste auf den Umsatz, zeigen Sie auf **Zusätzliche Aktionen**, und klicken Sie anschließend auf **Drillthrough to Order Details**.  
  
     Die Details der an Adam Powell gelieferten Bestellungen werden im **Datenstichproben-Viewer**angezeigt, wie in der folgenden Abbildung zu sehen ist. Einige zusätzliche Details wären jedoch hilfreich, wie z. B. Bestelldatum, Fälligkeitsdatum und Lieferdatum. Sie fügen diese zusätzlichen Details in der nächsten Prozedur hinzu.  
  
     ![An Adam Powell versendete Bestellungen](../../2014/tutorials/media/l8-action6.gif "An Adam Powell versendete Bestellungen")  
  
8.  Schließen von Excel/  
  
## <a name="modifying-the-drillthrough-action"></a>Ändern der Drillthroughaktion  
  
1.  Öffnen Sie den Dimensions-Designer für die **Internet Sales Order Details** -Dimension.  
  
     Für diese Dimension wurden nur drei Attribute definiert.  
  
2.  Klicken Sie im Bereich **Datenquellensicht** mit der rechten Maustaste auf einen leeren Bereich und anschließend auf **Alle Tabellen anzeigen**.  
  
3.  Zeigen Sie im Menü **Format** auf **AutoLayout** , und klicken Sie anschließend auf **Diagramm**.  
  
4.  Suchen Sie die Tabelle **InternetSales (dbo.FactInternetSales)** , indem Sie mit der rechten Maustaste in einem offenen Bereich des Bereichs **Datenquellensicht** klicken. Klicken Sie auf **Tabelle suchen** und auf **InternetSales,** und anschließend auf **OK**.  
  
5.  Erstellen Sie neue Attribute anhand der folgenden Spalten:  
  
    -   OrderDateKey  
  
    -   DueDateKey  
  
    -   ShipDateKey  
  
6.  Ändern Sie die **Name** -Eigenschaft für das **Order Date Key** -Attribut in `Order Date` , und klicken Sie dann auf die Schaltfläche zum Durchsuchen für die **Name Column** -Eigenschaft, und wählen Sie im Dialogfeld **Namensspalte** den Wert **Date** als Quell Tabelle und SimpleDate als Quell Spalte aus. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Ändern Sie **die Name** -Eigenschaft für das **Due Date Key** `Due Date`-Attribut in, und ändern Sie dann mithilfe derselben Methode wie das **Order Date Key** -Attribut die **Name Column** -Eigenschaft für dieses Attribut in **Date. SimpleDate (WChar)**.  
  
8.  Ändern Sie die **Name** -Eigenschaft für das **Ship Date Key** -Attribut in `Ship Date`, und ändern Sie dann die **Name Column** -Eigenschaft für dieses Attribut in **Date. SimpleDate (WChar)**.  
  
9. Wechseln Sie zur Registerkarte **Aktionen** des Cube-Designers für den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube.  
  
10. Fügen Sie im Feld **Drillthroughspalten** der Liste **Rückgabespalten** die folgenden Spalten durch Aktivieren der entsprechenden Kontrollkästchen hinzu, und klicken Sie anschließend auf **OK**:  
  
    -   Order Date  
  
    -   Due Date  
  
    -   Ship Date  
  
     In der folgenden Abbildung sind diese Spalten markiert.  
  
     ![Drillthroughspalten (Feld)](../../2014/tutorials/media/l8-action7.gif "Drillthroughspalten (Feld)")  
  
## <a name="reviewing-the-modified-drillthrough-action"></a>Überprüfen der geänderten Drillthroughaktion  
  
1.  Klicken Sie im Menü **Erstellen** auf **Analysis Services Tutorial bereitstellen**.  
  
2.  Wechseln Sie nach erfolgreichem Abschluss der Bereitstellung im Cube-Designer für den **Tutorial-Cube zur Registerkarte** Browser [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , und klicken Sie anschließend auf die Schaltfläche **Verbindung wiederherstellen** .  
  
3.  Starten Sie Excel.  
  
4.  Erstellen Sie die PivotTable mit **Internet Sales-Sales Amount** im Bereich „Werte“ und **Customer Geography** im Berichtsfilter neu.  
  
     Fügen Sie einen Filter hinzu, durch den **Adam Powell**aus **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**, ausgewählt wird.  
  
5.  Klicken Sie auf die Datenzelle **Internet Sales-Sales Amount** , zeigen Sie auf **Zusätzliche Aktionen**, und klicken Sie anschließend auf **Drillthrough to Order Details**.  
  
     Die Details dieser an Adam Powell gelieferten Bestellungen werden in einem temporären Arbeitsblatt angezeigt. Dies umfasst Artikelbeschreibung, Bestellnummer, Bestelldatum, Fälligkeitsdatum und Versanddatum, wie in der folgenden Abbildung dargestellt.  
  
     ![An Adam Powell versendete Bestellungen](../../2014/tutorials/media/l8-action8.gif "An Adam Powell versendete Bestellungen")  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 9: Definieren von Perspektiven und Übersetzungen](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktionen &#40;Analysis Services Mehrdimensionale Daten&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)   
 [Aktionen in mehrdimensionalen Modellen](multidimensional-models/actions-in-multidimensional-models.md)   
 [Dimensions Beziehungen](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Definieren einer Fakten Beziehung](lesson-5-2-defining-a-fact-relationship.md)   
 [Definieren von Faktenbeziehungen und Faktenbeziehungseigenschaften](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)  
  
  
