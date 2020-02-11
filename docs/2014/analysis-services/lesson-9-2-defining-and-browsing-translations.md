---
title: Definieren und Durchsuchen von Übersetzungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e60be99-3768-499c-a22c-a4ec37e61887
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f9a254f685f83e97b14c78c7d6c4c21e2737b636
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "69493780"
---
# <a name="defining-and-browsing-translations"></a>Definieren und Durchsuchen von Übersetzungen
  Eine Übersetzung ist eine Darstellung der Namen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekten in einer bestimmten Sprache. Objekte schließen Measuregruppen, Measures, Dimensionen, Attribute, Hierarchien, KPIs, Aktionen und berechnete Elemente ein. Übersetzungen bieten Serverunterstützung für Clientanwendungen, die mehrere Sprachen unterstützen können. Bei Verwendung eines solchen Clients übergibt der Client den Gebietsschemabezeichner (Locale Identifier, LCID) an die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], die mithilfe des Gebietsschemabezeichners bestimmt, welche Übersetzungen beim Bereitstellen von Metadaten für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekte verwendet werden sollen. Enthält ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt keine Übersetzung für diese Sprache oder keine Übersetzung für ein angegebenes Objekt, wird die Standardsprache zur Rückgabe der Objektmetadaten an den Client verwendet. Wenn z. B. ein Anwender des Produkts im geschäftlichen Bereich in Frankreich von einer Arbeitsstation mit einer französischen Gebietsschemaeinstellung auf einen Cube zugreift, sieht er die Elementbeschriftungen und die Werte der Elementeigenschaften auf Französisch, sofern eine französische Übersetzung vorhanden ist. Wenn jedoch ein Anwender des Produkts im geschäftlichen Bereich in Deutschland von einer Arbeitsstation mit einer deutschen Gebietsschemaeinstellung auf denselben Cube zugreift, sieht er die Elementbeschriftungen und die Werte der Elementeigenschaften auf Deutsch. Weitere Informationen finden Sie unter [Dimensions Übersetzungen](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md), [Cubeübersetzungen](multidimensional-models-olap-logical-cube-objects/cube-translations.md), [Übersetzungen &#40;Analysis Services&#41;](translations-analysis-services.md).  
  
 Im Rahmen der Tasks in diesem Thema definieren Sie Metadatenübersetzungen für eine begrenzte Gruppe von Dimensionsobjekten in den Date-Dimensions- und Cubeobjekten im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube. Sie durchsuchen dann diese Dimensions- und Cubeobjekte, um die Metadatenübersetzungen zu überprüfen.  
  
## <a name="specifying-translations-for-the-date-dimension-metadata"></a>Angeben von Übersetzungen für die Date-Dimensionsmetadaten  
  
1.  Öffnen Sie den Dimensions-Designer für die **Date** -Dimension, und klicken Sie anschließend auf die Registerkarte **Übersetzungen** .  
  
     Die Metadaten werden in der Standardsprache für jedes Dimensionsobjekt angezeigt. Die Standardsprache im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube ist Englisch.  
  
2.  Klicken Sie auf der Symbolleiste der Registerkarte **Übersetzungen** auf **Neue Übersetzung** .  
  
     Im Dialogfeld **Sprache auswählen** wird eine Liste mit Sprachen angezeigt.  
  
3.  Klicken Sie auf **Spanisch (Spanien)** und anschließend auf **OK**.  
  
     Es wird eine neue Spalte angezeigt, in der Sie die spanischen Übersetzungen der zu übersetzenden Metadatenobjekte definieren können. In diesem Lernprogramm wird nur eine begrenzte Anzahl von Objekten zur Veranschaulichung des Prozesses übersetzt.  
  
4.  Klicken Sie auf der Symbolleiste der Registerkarte **Übersetzungen** auf **Neue Übersetzung** , klicken Sie im Dialogfeld **Sprache auswählen** auf **Französisch (Frankreich)** , und klicken Sie anschließend auf **OK**.  
  
     Es wird eine weitere Sprachspalte angezeigt, in der Sie französische Übersetzungen definieren können.  
  
5.  Geben `Fecha` Sie in der Zeile für das **Caption** -Objekt für die **Date** -Dimension in die Übersetzungs Spalte für **Spanisch (Spanien)** und `Temps` in die Übersetzungs Spalte **Französisch (Frankreich)** ein.  
  
6.  Geben `Mes del Año` Sie in der Zeile für das **Caption** -Objekt für das **Month Name** -Attribut in die Übersetzungs Spalte für **Spanisch (Spanien)** und `Mois d'Année` in die Übersetzungs Spalte **Französisch (Frankreich)** ein.  
  
     Beachten Sie, dass beim Eingeben dieser Übersetzungen Auslassungs Zeichen (**...**) angezeigt werden. Durch Klicken auf dieses Auslassungszeichen können Sie eine Spalte in der zugrunde liegenden Tabelle angeben, die Übersetzungen für jedes Mitglied der Attributhierarchie bereitstellt.  
  
7.  Klicken Sie auf die Auslassungs Punkte (**...**) für die **Spanisch (Spanien)** -Übersetzung für das **Month Name** -Attribut.  
  
     Das Dialogfeld **Attributdatenübersetzung** wird angezeigt.  
  
8.  Wählen Sie in der Liste **Übersetzungsspalten** die Option **SpanishMonthName**wie in der folgenden Abbildung dargestellt aus.  
  
     ![Attributdaten Übersetzung (Dialogfeld)](../../2014/tutorials/media/l9-translations-4.gif "Attributdatenübersetzung (Dialogfeld)")  
  
9. Klicken Sie auf **OK**, und klicken Sie dann auf die Auslassungs Punkte (**...**) für die **Französisch (Frankreich)** -Übersetzung für das **Month Name** -Attribut.  
  
10. Wählen Sie in der Liste **Übersetzungsspalten** die Option **FrenchMonthName**aus, und klicken Sie anschließend auf **OK**.  
  
     Die Schritte in dieser Prozedur veranschaulichen den Prozess der Definition von Metadatenübersetzungen für Dimensionsobjekte und -elemente.  
  
## <a name="specifying-translations-for-the-analysis-services-tutorial-cube-metadata"></a>Angeben von Übersetzungen für die Metadaten des Analysis Services Tutorial-Cubes  
  
1.  Wechseln Sie zum Cube-Designer für den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube und anschließend zur Registerkarte **Übersetzungen** .  
  
     Die Metadaten werden in der Standardsprache für jedes Cubeobjekt angezeigt, wie in der folgenden Abbildung dargestellt. Die Standardsprache im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube ist Englisch.  
  
     ![Standardsprache auf der Registerkarte "Übersetzungen"](../../2014/tutorials/media/l9-translations-5.gif "Standardsprache auf der Registerkarte "Übersetzungen"")  
  
2.  Klicken Sie auf der Symbolleiste der Registerkarte **Übersetzungen** auf **Neue Übersetzung** .  
  
     Im Dialogfeld **Sprache auswählen** wird eine Liste mit Sprachen angezeigt.  
  
3.  Wählen Sie **Spanisch (Spanien)** aus, und klicken Sie anschließend auf **OK**.  
  
     Es wird eine neue Spalte angezeigt, in der Sie die spanischen Übersetzungen der zu übersetzenden Metadatenobjekte definieren können. In diesem Lernprogramm wird nur eine begrenzte Anzahl von Objekten zur Veranschaulichung des Prozesses übersetzt.  
  
4.  Klicken Sie auf der Symbolleiste der Registerkarte **Übersetzungen** auf **Neue Übersetzung** , klicken Sie im Dialogfeld **Sprache auswählen** auf **Französisch (Frankreich)** , und klicken Sie anschließend auf **OK**.  
  
     Es wird eine weitere Sprachspalte angezeigt, in der Sie französische Übersetzungen definieren können.  
  
5.  Geben `Fecha` Sie in der Zeile für das **Caption** -Objekt für die **Date** -Dimension in die Übersetzungs Spalte für **Spanisch (Spanien)** und `Temps` in die Übersetzungs Spalte **Französisch (Frankreich)** ein.  
  
6.  Geben `Ventas del lnternet` Sie in der Zeile für das **Beschriftungs** Objekt für die **Internet Sales** -Measure-Gruppe in die Übersetzungs Spalte für **Spanisch (Spanien)** und `Ventes D'Internet` in die Übersetzungs Spalte **Französisch (Frankreich)** ein.  
  
7.  Geben `Cantidad de las Ventas del Internet` Sie in der Zeile für das **Caption** -Objekt für das Internet Sales-Sales Amount-Measure in die Übersetzungs Spalte für **Spanisch (Spanien)** und `Quantité de Ventes d'Internet` in die Übersetzungs Spalte **Französisch (Frankreich)** ein.  
  
     Die Schritte in dieser Prozedur veranschaulichen den Prozess der Definition von Metadatenübersetzungen für Cubeobjekte.  
  
## <a name="browsing-the-cube-by-using-translations"></a>Durchsuchen des Cubes mithilfe von Übersetzungen  
  
1.  Klicken Sie im Menü **Erstellen** auf **Analysis Services Tutorial bereitstellen**.  
  
2.  Wechseln Sie nach erfolgreichem Abschluss der Bereitstellung zur Registerkarte **Browser** , und klicken Sie anschließend auf **Verbindung wiederherstellen**.  
  
3.  Entfernen Sie alle Hierarchien und Measures aus dem Bereich **Daten** , und wählen Sie in der Liste [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Perspektiven **das** -Tutorial aus.  
  
4.  Erweitern Sie im Metadatenbereich zuerst **Measures** und anschließend **Internet Sales**.  
  
     Das **Internet Sales-Sales Amount** -Measure wird in dieser Measuregruppe auf Englisch angezeigt.  
  
5.  Wählen Sie auf der Symbolleiste in der Liste **Sprache** die Option **Spanisch (Spanien)** aus.  
  
     Die Elemente im Metadatenbereich werden erneut aufgefüllt. Nach dem erneuten Auffüllen der Elemente im Metadatenbereich wird das Internet Sales-Sales Amount-Measure nicht mehr im Internet Sales-Anzeigeordner angezeigt. Stattdessen wird es in einem Spanisch in einem neuen Anzeige Ordner mit `Ventas del lnternet`dem Namen angezeigt, wie in der folgenden Abbildung dargestellt.  
  
     ![Neu aufgefüllter Metadatenbereich](../../2014/tutorials/media/l9-translations-6.gif "Neu aufgefüllter Metadatenbereich")  
  
6.  Klicken Sie im Metadatenbereich mit der `Cantidad de las Ventas del Internet` rechten Maustaste, und wählen Sie dann **zu Abfrage hinzufügen**aus.  
  
7.  Erweitern `Fecha`Sie im Metadatenbereich den Eintrag **Fecha. Calendar Date**, klicken Sie mit der rechten Maustaste auf **Fecha. Calendar Date**, und wählen Sie dann **zu Filter hinzufügen**aus.  
  
8.  Wählen Sie im Bereich **Filter** den Eintrag **CY 2007** als Filterausdruck aus.  
  
9. Klicken Sie im Metadatenbereich mit der rechten Maustaste auf **Mes del Ano** , und wählen Sie **Zu Abfrage hinzufügen**aus.  
  
     Die Monatsnamen werden, wie in der folgenden Abbildung zu sehen, in Spanisch angezeigt.  
  
     ![Monatsnamen auf Spanisch im Datenbereich](../../2014/tutorials/media/l9-translations-7.gif "Monatsnamen auf Spanisch im Datenbereich")  
  
10. Wählen Sie auf der Symbolleiste in der Liste **Sprache** die Option **Französisch (Frankreich)** aus.  
  
     Die Monatsnamen werden jetzt ebenso wie der Measurename in französischer Sprache angezeigt.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 10: Definieren von Administratorrollen](lesson-10-defining-administrative-roles.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions Übersetzungen](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Cubeübersetzungen](multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Übersetzungen &#40;Analysis Services&#41;](translations-analysis-services.md)  
  
  
