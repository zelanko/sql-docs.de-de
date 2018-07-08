---
title: 'Lektion 1: Erstellen eines Berichtsserverprojekts (Reporting Services) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
caps.latest.revision: 51
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 8599cb6c4390b0e204bde2b02a36729cf3b48dcc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148721"
---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a>Lektion 1: Erstellen eines Berichtsserverprojekts (Reporting Services)
  Zum Erstellen eines Berichts in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Sie müssen zuerst ein Berichtsserverprojekt, in dem Sie Ihre Berichtsdefinitionsdatei (.rdl) und Speichern jeder andere Ressourcendateien, die Sie für Ihren Bericht benötigen, erstellen. Anschließend erstellen Sie die tatsächliche Berichtsdefinitionsdatei, und Sie definieren eine Datenquelle für Ihren Bericht, ein Dataset sowie das Berichtslayout. Beim Ausführen des Berichts werden die tatsächlichen Daten abgerufen und mit dem Layout kombiniert. Anschließend werden die Daten auf dem Bildschirm gerendert. Dort können Sie sie exportieren, drucken und speichern.  
  
 In dieser Lektion wird erläutert, wie Sie ein Berichtsserverprojekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] erstellen. In einem Berichtsserverprojekt werden Berichte erstellt, die auf einem Berichtsserver ausgeführt werden.  
  
### <a name="to-create-a-report-server-project"></a>So erstellen Sie ein Berichtsserverprojekt  
  
1.  Klicken Sie auf **starten**, zeigen Sie auf **Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], und klicken Sie dann auf **SQL Server Data Tools**. Wenn dies zum ersten Mal wird Sie geöffnet haben [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], klicken Sie auf **Business Intelligence-Einstellungen** für die standardumgebungseinstellungen.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Klicken Sie in der Liste **Installierte Vorlagen** auf **Business Intelligence**.  
  
4.  Klicken Sie auf **-Berichtsserverprojekt**.  
  
5.  Geben Sie im Feld **Name**den Namen **Tutorial**ein.  
  
6.  Klicken Sie auf **OK** , um das Projekt zu erstellen.  
  
     Das Projekt für das Lernprogramm wird im Projektmappen-Explorer angezeigt.  
  
### <a name="to-create-a-new-report-definition-file"></a>So erstellen Sie eine neue Berichtsdefinitionsdatei  
  
1.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Berichte**, zeigen Sie auf **hinzufügen**, und klicken Sie auf **neues Element**.  
  
    > [!NOTE]  
    >  Wird das Fenster **Projektmappen-Explorer** nicht angezeigt, klicken Sie im Menü **Ansicht** auf **Projektmappen-Explorer**.  
  
2.  In der **neues Element hinzufügen** Dialogfeld **Vorlagen**, klicken Sie auf **Bericht**.  
  
3.  Geben Sie in **Name** **Sales Orders.rdl** ein, und klicken Sie auf **Hinzufügen**.  
  
     Der Berichts-Designer wird geöffnet, und in der Entwurfsansicht wird die neue RDL-Datei angezeigt.  
  
 Der Berichts-Designer ist eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Komponente, die in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ausgeführt wird. Er weist zwei Ansichten auf: **Entwurf** und **Vorschau**. Klicken Sie auf die einzelnen Registerkarten, um zwischen den Ansichten zu wechseln.  
  
 Die Daten werden im **Berichtsdatenbereich** definiert. In der Ansicht **Entwurf** wird das Berichtslayout definiert. Sie können den Bericht ausführen, und in der Ansicht **Vorschau** können Sie eine Vorschau des Berichts anzeigen.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben das Berichtsprojekt Tutorial erfolgreich erstellt und dem Berichtsprojekt eine Berichtsdefinitionsdatei (*.rdl) hinzugefügt. Als Nächstes geben Sie eine Datenquelle an, die für den Bericht verwendet werden soll. Weitere Informationen finden Sie unter [Lektion 2: Angeben von Verbindungsinformationen (Reporting Services)](lesson-2-specifying-connection-information-reporting-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen ein einfachen Tabellenberichts &#40;SSRS-Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
