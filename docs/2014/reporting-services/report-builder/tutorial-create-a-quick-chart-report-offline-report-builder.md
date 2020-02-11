---
title: 'Tutorial: Schnelles Erstellen eines Diagrammberichts offline (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports, creating
- tutorials, getting started
- creating reports
ms.assetid: 6b1db67a-cf75-494c-b70c-09f1e6a8d414
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f345eaa2a51b5e6789f2a03968f8a1e68b12519a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107572"
---
# <a name="tutorial-create-a-quick-chart-report-offline-report-builder"></a>Lernprogramm: Erstellen eines Quick-Diagrammberichts offline (Berichts-Generator)
  In diesem Lernprogramm erstellen Sie ein Kreisdiagramm mithilfe eines Assistenten. Danach nehmen Sie eine kleine Änderung an diesem Diagramm vor, damit Sie eine Vorstellung von den Bearbeitungsmöglichkeiten erhalten. Dieses Lernprogramm kann auf zwei unterschiedliche Arten absolviert werden. Beide Methoden haben dasselbe Ergebnis: ein Kreis Diagramm wie das in der folgenden Abbildung:  
  
 !["Mein erstes Kreisdiagramm" in der Ansicht "Ausführen"](../media/rs-my1stpierunview.gif "Mein erstes Kreis Diagramm in der Ansicht "ausführen"")  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Sowohl bei Verwendung von XML-Daten als auch bei einer [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Abfrage benötigen Sie Zugriff auf [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Berichts-Generator. Sie können die eigenständige Version oder die ClickOnce-Version ausführen, die im Berichts-Manager oder auf einer SharePoint-Website verfügbar ist. Bei der ClickOnce-Version ist lediglich der erste Schritt anders, also das Öffnen des Berichts-Generators. Weitere Informationen finden Sie [unter Installieren, deinstallieren und Berichts-Generator-Unterstützung](../install-uninstall-and-report-builder-support.md).  
  
##  <a name="TwoWays"></a>Zwei Möglichkeiten für dieses Tutorial  
  
-   [Erstellen des Kreis Diagramms mit XML-Daten](#CreatePieChartXML)  
  
-   [Erstellen des Kreis Diagramms mit einer Transact-SQL-Abfrage, die Daten enthält](#CreatePieQueryData)  
  
### <a name="using-xml-data-for-this-tutorial"></a>Verwenden von XML-Daten für dieses Lernprogramm  
 Sie können XML-Daten verwenden, die Sie aus diesem Thema kopieren und in den Assistenten einfügen. Es muss keine Verbindung mit einem Berichtsserver oder einem Berichtsserver im integrierten SharePoint-Modus bestehen, und Sie müssen auf keine Instanz von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] zugreifen.  
  
 [Erstellen des Kreis Diagramms mit XML-Daten](#CreatePieChartXML)  
  
### <a name="using-a-transact-sql-query-that-contains-data-for-this-tutorial"></a>Verwenden einer Transact-SQL-Abfrage mit Daten für dieses Lernprogramm  
 Sie können aus diesem Thema eine Abfrage mit Daten kopieren und diese in den Assistenten einfügen. Sie benötigen den Namen einer Instanz von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] sowie Anmeldeinformationen für den schreibgeschützten Zugriff auf eine beliebige Datenbank. Von der Datasetabfrage im Lernprogramm werden zwar Literaldaten verwendet, die Abfrage muss jedoch durch eine Instanz von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] verarbeitet werden, um die für ein Berichtsdataset erforderlichen Metadaten zurückzugeben.  
  
 Der Vorteil der Verwendung der [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Abfrage besteht darin, dass in allen anderen Lernprogrammen für Berichts-Generator die gleiche Methode verwendet wird und Sie beim Ausführen der anderen Lernprogramme bereits mit der Vorgehensweise vertraut sind.  
  
 Für die [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Abfrage müssen noch einige andere Voraussetzungen erfüllt sein. Weitere Informationen finden Sie unter [Voraussetzungen für Lernprogramme &#40;Berichts-Generator&#41;](../report-builder-tutorials.md).  
  
 [Erstellen des Kreis Diagramms mit einer Transact-SQL-Abfrage, die Daten enthält](#CreatePieQueryData)  
  
## <a name="also-in-this-article"></a>Auch in diesem Artikel  
 [Nach dem Ausführen des Assistenten](#AfterWizard)  
  
 [Was kommt als nächstes](#WhatsNext)  
  
##  <a name="CreatePieChartXML"></a>Erstellen des Kreis Diagramms mit XML-Daten  
  
#### <a name="to-create-the-pie-chart-with-xml-data"></a>So erstellen Sie das Kreisdiagramm mit XML-Daten  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 2012 Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
     Das Dialogfeld " **Getting Started** " wird angezeigt.  
  
    > [!NOTE]  
    >  Wenn das Dialogfeld " **Getting Started** " nicht angezeigt wird, klicken Sie auf der Schaltfläche " **Berichts-Generator** " auf **neu**.  
  
2.  Vergewissern Sie sich im linken Bereich, dass der **Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Diagramm-Assistent**und anschließend auf **Erstellen**.  
  
4.  Klicken Sie auf der Seite **Dataset auswählen** auf **Dataset erstellen**und anschließend auf **Weiter**.  
  
5.  Klicken Sie auf der Seite **Verbindung mit einer Datenquelle auswählen** auf **Neu**.  
  
     Das Dialogfeld **Datenquelleneigenschaften** wird angezeigt.  
  
6.  Sie können jedes gewünschte Element als Datenquelle bezeichnen. Geben Sie im Feld **Name** den Namen **MyPieChart**ein.  
  
7.  Klicken Sie im Feld **Verbindungstyp auswählen** auf **XML.**  
  
8.  Klicken Sie auf der Registerkarte **Anmelde** Informationen auf **aktuellen Windows-Benutzer verwenden. Möglicherweise ist eine Kerberos-Delegierung erforderlich**, und klicken Sie dann auf **OK**.  
  
9. Klicken Sie auf der Seite **Verbindung mit einer Datenquelle auswählen** auf **MyPieChart**und anschließend auf **Weiter**.  
  
10. Kopieren Sie den folgenden Text, und fügen Sie ihn in das große Feld in der Mitte der Seite **Abfrage entwerfen ein** .  
  
    ```  
    <Query>  
    <ElementPath>Root /S  {@Sales (Integer)} /C {@FullName} </ElementPath>  
    <XmlData>  
    <Root>  
    <S Sales="150">  
      <C FullName="Jae Pak" />  
    </S>  
    <S Sales="350">  
      <C FullName="Jillian  Carson" />  
    </S>  
    <S Sales="250">  
      <C FullName="Linda C Mitchell" />  
    </S>  
    <S Sales="500">  
      <C FullName="Michael Blythe" />  
    </S>  
    <S Sales="450">  
      <C FullName="Ranjit Varkey" />  
    </S>  
    </Root>  
    </XmlData>  
    </Query>  
    ```  
  
11. (Optional) Klicken Sie auf die Schaltfläche „Ausführen“ ( **!** ), um die Daten anzuzeigen, auf denen das Diagramm basiert.  
  
12. Klicken Sie auf **Weiter**.  
  
13. Klicken Sie auf der Seite **Diagrammtyp auswählen** auf **Kreisdiagramm**. Danach klicken Sie auf **Weiter**.  
  
14. Doppelklicken Sie auf der Seite **Diagrammfelder anordnen** auf das Feld **Vertrieb** im Feld **Verfügbare Felder**.  
  
     Beachten Sie, dass der Wert automatisch in das Feld **Werte** verschoben wird, da es sich um einen numerischen Wert handelt.  
  
15. Ziehen Sie das Feld **FullName** aus dem Feld **Verfügbare Felder** in das Feld **Kategorien** (oder doppelklicken Sie auf das Feld, damit es in das Feld **Kategorien** verschoben wird). Klicken Sie anschließend auf **Weiter**.  
  
16. Auf der Seite Format **auswählen** ist **Ozean** standardmäßig ausgewählt. Klicken Sie auf die anderen Formate, um deren Darstellung anzuzeigen.  
  
17. Klicken Sie auf **Fertig stellen**.  
  
     Nun sehen Sie den neuen Kreisdiagrammbericht auf der Entwurfsoberfläche. Was Sie sehen, ist symbolisch. Anstelle der Namen der Vertriebsmitarbeiter enthält die Legende "Full Name 1", "Full Name 2" usw.; außerdem ist die Größe der Kreissegmente nicht exakt. Diese Darstellung soll nur eine Vorstellung vom Aussehen des Berichts vermitteln.  
  
18. Klicken Sie auf der Registerkarte **Home** des Menübands auf **Ausführen** , um das tatsächliche Kreisdiagramm anzuzeigen.  
  
 ![Pfeilsymbol mit dem Link "zurück zum Anfang](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") " [zurück zum Anfang](#TwoWays)  
  
##  <a name="CreatePieQueryData"></a>Erstellen des Kreis Diagramms mit [!INCLUDE[tsql](../../../includes/tsql-md.md)] einer Abfrage  
  
#### <a name="to-create-the-pie-chart-with-a-includetsqlincludestsql-mdmd-query-that-contains-data"></a>So erstellen Sie das Kreisdiagramm mit einer [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Abfrage, die Daten enthält  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 2012 Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
2.  Überprüfen Sie im Dialogfeld **neuer Bericht oder DataSet** , ob im linken Bereich **Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Diagramm-Assistent**und anschließend auf **Erstellen**.  
  
4.  Klicken Sie auf der Seite **Dataset auswählen** auf **Dataset erstellen**und anschließend auf **Weiter**.  
  
5.  Wählen Sie auf der Seite **Verbindung mit einer Datenquelle auswählen** eine vorhandene Datenquelle aus, oder navigieren Sie zum Berichtsserver, und wählen Sie eine Datenquelle aus. Klicken Sie anschließend auf **Weiter**. Möglicherweise müssen Benutzername und Kennwort eingegeben werden.  
  
    > [!NOTE]  
    >  Welche Datenquelle Sie auswählen, ist unwichtig, solange Sie über ausreichende Berechtigungen verfügen. Aus der Datenquelle werden keine Daten abgerufen. Weitere Informationen finden Sie unter [Voraussetzungen für Lernprogramme &#40;Berichts-Generator&#41;](../report-builder-tutorials.md).  
  
6.  Klicken Sie auf der Seite **Abfrage entwerfen** auf **Als Text bearbeiten**.  
  
7.  Fügen Sie die folgende Abfrage in den Abfragebereich ein:  
  
    ```  
    SELECT 150 AS Sales, 'Jae Pak' AS FullName   
    UNION SELECT 350 AS Sales, 'Jillian Carson' AS FullName   
    UNION SELECT 250 AS Sales, 'Linda C Mitchell' AS FullName   
    UNION SELECT 500 AS Sales, 'Michael Blythe' AS FullName   
    UNION SELECT 450 AS Sales, 'Ranjit Varkey' AS FullName   
    ```  
  
8.  (Optional) Klicken Sie auf die Schaltfläche „Ausführen“ ( **!** ), um die Daten anzuzeigen, auf denen das Diagramm basiert.  
  
9. Klicken Sie auf **Weiter**.  
  
10. Klicken Sie auf der Seite **Diagrammtyp auswählen** auf **Kreisdiagramm**. Danach klicken Sie auf **Weiter**.  
  
11. Doppelklicken Sie auf der Seite **Diagrammfelder anordnen** auf das Feld **Vertrieb** im Feld **Verfügbare Felder**.  
  
     Beachten Sie, dass der Wert automatisch in das Feld **Werte** verschoben wird, da er ein numerischer Wert ist.  
  
12. Ziehen Sie das Feld **FullName** aus dem Feld **Verfügbare Felder** in das Feld **Kategorien** (oder doppelklicken Sie auf das Feld, damit es in das Feld **Kategorien** verschoben wird). Klicken Sie anschließend auf **Weiter**.  
  
13. Auf der Seite Format **auswählen** ist Ozean standardmäßig ausgewählt. Klicken Sie auf die anderen Formate, um deren Darstellung anzuzeigen.  
  
14. Klicken Sie auf **Fertig stellen**.  
  
     Nun sehen Sie den neuen Kreisdiagrammbericht auf der Entwurfsoberfläche. Was Sie sehen, ist symbolisch. Anstelle der Namen der Vertriebsmitarbeiter enthält die Legende "Full Name 1", "Full Name 2" usw.; außerdem ist die Größe der Kreissegmente nicht exakt. Diese Darstellung soll nur eine Vorstellung vom Aussehen des Berichts vermitteln.  
  
15. Klicken Sie auf der Registerkarte **Home** des Menübands auf **Ausführen** , um das tatsächliche Kreisdiagramm anzuzeigen.  
  
 ![Pfeilsymbol mit dem Link "zurück zum Anfang](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") " [zurück zum Anfang](#TwoWays)  
  
##  <a name="AfterWizard"></a>Nach dem Ausführen des Assistenten  
 Nachdem Sie den Kreisdiagrammbericht erstellt haben, können Sie etwas experimentieren. Klicken Sie auf der Registerkarte **Ausführen** des Menübands auf **Entwurf**, um das Diagramm weiter ändern zu können.  
  
### <a name="make-the-chart-bigger"></a>Vergrößern des Diagramms  
 Das Kreisdiagramm muss unter Umständen vergrößert werden. Klicken Sie auf das Diagramm, um es auszuwählen. Klicken Sie dabei jedoch nicht auf ein Element des Diagramms. Ziehen Sie anschließend die rechte untere Ecke, um die Größe zu ändern.  
  
### <a name="add-a-report-title"></a>Hinzufügen eines Berichtstitels  
 Markieren Sie am oberen Rand des Diagramms den Text **Diagrammtitel** , und geben Sie anschließend einen Titel (beispielsweise **Sales Pie Chart**) ein.  
  
### <a name="add-percentages"></a>Hinzufügen von Prozentsätzen  
  
##### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>So zeigen Sie Prozentwerte als Bezeichnungen in einem Kreisdiagramm an  
  
1.  Klicken Sie mit der rechten Maustaste auf das Kreis Diagramm, und wählen Sie **Daten Bezeichnungen anzeigen**aus. Die Datenbezeichnungen sollten innerhalb jedes Segments des Kreisdiagramms angezeigt werden.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Bezeichnungen, und wählen Sie Reihen Bezeichnungs **Eigenschaften**. Das Dialogfeld **Reihenbezeichnungseigenschaften** wird angezeigt.  
  
3.  Geben `#PERCENT{P0}` Sie für die Option Bezeichnungs **Daten** ein.  
  
     Mit `{P0}` erhalten Sie den Prozentsatz ohne Dezimalstellen. Falls Sie nur `#PERCENT` eingeben, erhalten Ihre Zahlen zwei Dezimalstellen. 
  `#PERCENT` ist ein Schlüsselwort, das eine Berechnung oder eine Funktion für Sie ausführt. Dies ist nur ein Beispiel unter vielen.  
  
 Weitere Informationen zum Anpassen von Diagrammbezeichnungen und -legenden finden Sie unter [Anzeigen von Prozentwerten in einem Kreisdiagramm &#40;Berichts-Generator und SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) sowie unter [Ändern des Texts eines Legendenelements &#40;Berichts-Generator und SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md).  
  
 ![Pfeilsymbol mit dem Link "zurück zum Anfang](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") " [zurück zum Anfang](#TwoWays)  
  
##  <a name="WhatsNext"></a>Was kommt als nächstes?  
 Nachdem Sie nun Ihren ersten Bericht im Berichts-Generator erstellt haben, können Sie die anderen Lernprogramme ausführen und die ersten Berichte mit Ihren eigenen Daten erstellen. Um Berichts-Generator auszuführen, benötigen Sie die Berechtigung für den Zugriff auf Ihre Datenquellen, z. b. Datenbanken, mit einer *Verbindungs Zeichenfolge*, die Sie tatsächlich mit der Datenquelle verbindet. Der Systemadministrator hat diese Informationen und kann Ihnen bei der Einrichtung helfen.  
  
 Zum Absolvieren der anderen Lernprogramme benötigen Sie den Namen einer Instanz von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] sowie Anmeldeinformationen für den schreibgeschützten Zugriff auf eine beliebige Datenbank. Auch dabei können Sie sich an den Systemadministrator wenden.  
  
 Schließlich benötigen Sie die URL und die Berechtigungen, um die Berichte auf einem Berichtsserver oder einer SharePoint-Website zu speichern, die mit einem Berichtsserver integriert ist. Sie können jeden Bericht, den Sie erstellen, direkt auf Ihrem Computer ausführen. Berichte haben jedoch mehr Funktionalität, wenn sie vom Berichtsserver oder von einer SharePoint-Website aus ausgeführt werden. Sie benötigen Berechtigungen zum Ausführen Ihrer Berichte oder anderer Berichte auf dem Berichtsserver oder einer SharePoint-Website, auf der sie veröffentlicht werden. Wenden Sie sich an den Systemadministrator, um Zugriff zu erhalten.  
  
 Außerdem sollten Sie sich zunächst mit einigen Grundlagen und Begriffen vertraut machen. Weitere Informationen finden Sie unter [Konzepte der Berichterstellung &#40;Berichts-Generator und SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md). Außerdem sollten Sie das Erstellen Ihres ersten Berichts sorgfältig planen. Der Aufwand lohnt sich. Weitere Informationen finden Sie unter [Planning a Report &#40;Berichts-Generator&#41;](../report-design/planning-a-report-report-builder.md).  
  
 ![Pfeilsymbol mit dem Link "zurück zum Anfang](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") " [zurück zum Anfang](#TwoWays)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lernprogramme &#40;Berichts-Generator&#41;](../report-builder-tutorials.md)   
 [Berichts-Generator in SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  
