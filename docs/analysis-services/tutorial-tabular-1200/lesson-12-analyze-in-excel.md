---
title: 'Lektion 12: Analysieren in Excel | Microsoft-Dokumentation'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8a558dafb4619ef9c4d66884f1fea9fd98e0881c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65404102"
---
# <a name="lesson-12-analyze-in-excel"></a>Lektion 12: In Excel analysieren
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion verwenden Sie analysieren in Excel-Funktion in SSDT auf Microsoft Excel öffnen, automatisch eine datenquellenverbindung mit dem Modellarbeitsbereich zu erstellen und automatisch eine PivotTable zum Arbeitsblatt hinzuzufügen. Die Funktion In Excel analysieren stellt eine schnelle und einfache Methode dar, um die Wirksamkeit Ihres Modellentwurfs vor der Modellbereitstellung zu testen. Sie führen in dieser Lektion keine Datenanalyse aus. Der Zweck dieser Lektion ist es, Sie, den Modellautor, mit den Tools vertraut zu machen, die Sie zum Testen des Modellentwurfs verwenden können. Im Gegensatz zur Verwendung von analysieren in Excel-Funktion, die für Modellentwickler vorgesehen ist, verwenden Endbenutzer Clientanwendungen zur berichterstellung wie Excel oder Power BI eine Verbindung herstellen, und navigieren Sie Modelldaten bereitgestellt.  
  
Um diese Lektion abzuschließen, muss Excel auf dem gleichen Computer wie SSDT installiert sein. Weitere Informationen finden Sie unter [In Excel analysieren](../tabular-models/analyze-in-excel-ssas-tabular.md)installiert sein.  
  
Geschätzte Zeit zum Abschließen dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 11: Erstellen von Rollen](lesson-11-create-roles.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Durchsuchen mit der Standardperspektive und der Internet Sales-Perspektive  
In dieser ersten Aufgaben durchsuchen Sie Ihr Modell unter Verwendung der Standardperspektive, die alle Modellobjekte enthält, sowie mit der Internet Sales-Perspektive Sie vorher erstellt haben. Die Internet Sales-Perspektive enthält nicht das Customer-Tabellenobjekt.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>So durchsuchen Sie das Modell mit der Standardperspektive  
  
1.  Klicken Sie auf die **Modell** Menü > **in Excel analysieren**.  
  
2.  Klicken Sie im Dialogfeld **In Excel analysieren** auf **OK**.  
  
    Excel wird mit einer neuen Arbeitsmappe geöffnet. Es wird eine Datenquellenverbindung mit dem aktuellen Benutzerkonto erstellt, und zum Definieren von Anzeigefeldern wird die Standardperspektive verwendet. Das Arbeitsblatt wird automatisch eine PivotTable hinzugefügt.  
  
3.  In Excel in der **Feldliste "PivotTable"** , beachten Sie, dass die **DimDate** und **"factinternetsales"** Measuregruppen angezeigt werden, als auch die **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**,  **DimProductSubcategory**, und **"factinternetsales"** Tabellen mit der entsprechenden Spalten angezeigt werden.  
  
4.  Schließen Sie Excel, ohne die Arbeitsmappe zu speichern.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>So durchsuchen Sie das Modell mit der Internet Sales-Perspektive  
  
1.  Klicken Sie auf die **Modell** , und klicken Sie dann auf **in Excel analysieren**.  
  
2.  Lassen Sie im Dialogfeld **In Excel analysieren** die Option **Aktueller Windows-Benutzer** aktiviert, wählen Sie im Dropdownlistenfeld **Perspektive** den Eintrag **Internet Sales**aus, und klicken Sie anschließend auf **OK**. 
    
    ![as-tabular-lesson12-perspective](media/as-tabular-lesson12-perspective.png)
    
3.  In Excel in **PivotTable Fields**, beachten Sie, dass die DimCustomer-Tabelle aus der Feldliste ausgeschlossen ist.  
    
    ![as-tabular-lesson12-fields](media/as-tabular-lesson12-fields.png)
    
4.  Schließen Sie Excel, ohne die Arbeitsmappe zu speichern.  
  
## <a name="browse-by-using-roles"></a>Navigieren Sie mithilfe von Rollen  
Rollen sind wesentlicher Bestandteil sämtlicher tabellarischer Modelle. Ohne mindestens eine Rolle, zu der Benutzer als Mitglieder hinzugefügt werden, werden Benutzer nicht zugreifen darf und Analysieren von Daten, die mit Ihrem Modell. Die Funktion In Excel analysieren bietet eine Möglichkeit zum Testen der Rollen, die Sie definiert haben.  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>So durchsuchen Sie mit der Benutzerrolle Sales Manager  
  
1.  Klicken Sie in SSDT auf das **Modell** , und klicken Sie dann auf **in Excel analysieren**.  
  
2.  In der **in Excel analysieren** Dialogfeld **Geben Sie den Benutzernamen oder die Rolle für die Verbindung mit dem Modell**Option **Rolle**, und wählen Sie dann im Dropdown-Listenfeld **Vertriebsleiter**, und klicken Sie dann auf **OK**.  
  
    Excel wird mit einer neuen Arbeitsmappe geöffnet. Eine PivotTable wird automatisch erstellt. Die PivotTable-Feldliste enthält alle Datenfelder, die im neuen Modell verfügbar sind.  
      
3.  Schließen Sie Excel, ohne die Arbeitsmappe zu speichern.  
  
## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 13: Bereitstellen von](lesson-13-deploy.md).

  
  
  
