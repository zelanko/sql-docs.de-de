---
title: 'Analysis Services-Tutorial – Lektion 12: Analysieren in Excel | Microsoft-Dokumentation'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: efd71653e723344e9175d9ab1529fafd610901df
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685428"
---
# <a name="analyze-in-excel"></a>In Excel analysieren

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion verwenden Sie die Funktion in Excel analysieren zu Microsoft Excel öffnen, automatisch eine Verbindung mit den Modellarbeitsbereich zu erstellen und automatisch eine PivotTable zum Arbeitsblatt hinzuzufügen. Die Funktion In Excel analysieren stellt eine schnelle und einfache Methode dar, um die Wirksamkeit Ihres Modellentwurfs vor der Modellbereitstellung zu testen. Sie führen in dieser Lektion keine Datenanalyse aus. Der Zweck dieser Lektion ist es, Sie, den Modellautor, mit den Tools vertraut zu machen, die Sie zum Testen des Modellentwurfs verwenden können.   
  
Um diese Lektion abschließen zu können, muss Excel auf dem gleichen Computer wie Visual Studio installiert sein.
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **5 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 11: Erstellen von Rollen](../tutorial-tabular-1400/as-lesson-11-create-roles.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Durchsuchen mit der Standardperspektive und der Internet Sales-Perspektive  

In dieser ersten Aufgaben durchsuchen Sie Ihr Modell unter Verwendung der Standardperspektive, die alle Modellobjekte enthält, sowie mit der Internet Sales-Perspektive Sie vorher erstellt haben. Die Internet Sales-Perspektive enthält nicht das Customer-Tabellenobjekt.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>So durchsuchen Sie das Modell mit der Standardperspektive  
  
1.  Klicken Sie auf die **Modell** Menü > **in Excel analysieren**.  
  
2.  Klicken Sie im Dialogfeld **In Excel analysieren** auf **OK**.  
  
    Excel wird mit einer neuen Arbeitsmappe geöffnet. Es wird eine Datenquellenverbindung mit dem aktuellen Benutzerkonto erstellt, und zum Definieren von Anzeigefeldern wird die Standardperspektive verwendet. Das Arbeitsblatt wird automatisch eine PivotTable hinzugefügt.  
  
3.  In Excel in der **Feldliste "PivotTable"**, beachten Sie, dass die **DimDate** und **"factinternetsales"** Measuregruppen angezeigt. Die **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, und **"factinternetsales"** Tabellen mit den entsprechenden Spalten auch angezeigt werden.  
  
4.  Schließen Sie Excel, ohne die Arbeitsmappe zu speichern.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>So durchsuchen Sie das Modell mit der Internet Sales-Perspektive  
  
1.  Klicken Sie auf die **Modell** , und klicken Sie dann auf **in Excel analysieren**.  
  
2.  Lassen Sie im Dialogfeld **In Excel analysieren** die Option **Aktueller Windows-Benutzer** aktiviert, wählen Sie im Dropdownlistenfeld **Perspektive** den Eintrag **Internet Sales**aus, und klicken Sie anschließend auf **OK**. 
    
    ![as-lesson12-perspective](../tutorial-tabular-1400/media/as-lesson12-perspective.png)
    
3.  In Excel in **PivotTable Fields**, beachten Sie, dass die DimCustomer-Tabelle aus der Feldliste ausgeschlossen ist.  
    
    ![as-lesson12-fields](../tutorial-tabular-1400/media/as-lesson12-fields.png)
    
4.  Schließen Sie Excel, ohne die Arbeitsmappe zu speichern.  
  
## <a name="browse-by-using-roles"></a>Navigieren Sie mithilfe von Rollen  

Rollen sind ein wichtiger Bestandteil sämtlicher tabellarischer Modelle. Ohne mindestens eine Rolle, zu der Benutzer als Mitglieder hinzugefügt werden, können keine Benutzer Zugriff auf und Analysieren von Daten, die mit Ihrem Modell. Die Funktion In Excel analysieren bietet eine Möglichkeit zum Testen der Rollen, die Sie definiert haben.  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>So durchsuchen Sie mit der Benutzerrolle Sales Manager  
  
1.  Klicken Sie in SSDT auf das **Modell** , und klicken Sie dann auf **in Excel analysieren**.  
  
2.  In **Geben Sie den Benutzernamen oder die Rolle für die Verbindung mit dem Modell**Option **Rolle**, und wählen Sie dann im Dropdown-Listenfeld **Vertriebsleiter**, und klicken Sie dann auf **OK**.  
  
    Excel wird mit einer neuen Arbeitsmappe geöffnet. Eine PivotTable wird automatisch erstellt. Die PivotTable-Feldliste enthält alle Datenfelder, im neuen Modell verfügbar sind.  
      
3.  Schließen Sie Excel, ohne die Arbeitsmappe zu speichern.  
  
## <a name="whats-next"></a>Wie geht es weiter?

Wechseln Sie zur nächsten Lektion: [Lektion 13: Bereitstellen von](../tutorial-tabular-1400/as-lesson-13-deploy.md).

  
  
  
