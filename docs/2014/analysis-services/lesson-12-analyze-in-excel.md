---
title: 'Lektion 13: Analysieren in Excel | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8175fee7c1bf1f6472c8e302cf13c418295b9380
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052080"
---
# <a name="lesson-13-analyze-in-excel"></a>Lektion 13: Analysieren in Excel
  In dieser Lektion verwenden Sie die Funktion In Excel analysieren in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], um Microsoft Excel zu öffnen, automatisch eine Datenquellenverbindung mit der Datenbank für Modellarbeitsbereiche herzustellen und dem Arbeitsblatt automatisch eine PivotTable hinzuzufügen. Die Funktion In Excel analysieren stellt eine schnelle und einfache Methode dar, um die Wirksamkeit Ihres Modellentwurfs vor der Modellbereitstellung zu testen. Sie führen in dieser Lektion keine Datenanalyse aus. Der Zweck dieser Lektion ist es, Sie, den Modellautor, mit den Tools vertraut zu machen, die Sie zum Testen des Modellentwurfs verwenden können. Die Funktion In Excel analysieren ist für Modellentwickler vorgesehen, während Endbenutzer zum Herstellen einer Verbindung mit bereitgestellten Modelldaten und zum Durchsuchen dieser Daten Clientberichtsanwendungen, z. B. Excel oder [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], verwenden.  
  
 Um diese Lektion abzuschließen, muss Excel auf dem gleichen Computer wie [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] installiert sein. Weitere Informationen finden Sie unter [Analysieren in Excel &#40;SSAS – tabellarisch&#41;](tabular-models/analyze-in-excel-ssas-tabular.md).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 11: Erstellen von Partitionen](lesson-10-create-partitions.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Durchsuchen mit der Standardperspektive und der Internet Sales-Perspektive  
 In diesen ersten Aufgaben durchsuchen Sie das Modell mit der Standardperspektive, die alle Modellobjekte enthält, und mit der Internet Sales-Perspektive, die Sie in "Lektion 8: Erstellen von Perspektiven" erstellt haben. Die Internet Sales-Perspektive enthält nicht das Customer-Tabellenobjekt.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>So durchsuchen Sie das Modell mit der Standardperspektive  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und dann auf **In Excel analysieren**.  
  
2.  Klicken Sie im Dialogfeld **In Excel analysieren** auf **OK**.  
  
     Excel wird mit einer neuen Arbeitsmappe geöffnet. Es wird eine Datenquellenverbindung mit dem aktuellen Benutzerkonto erstellt, und zum Definieren von Anzeigefeldern wird die Standardperspektive verwendet. Dem Arbeitsblatt wird automatisch eine PivotTable hinzugefügt.  
  
3.  In Excel in der **Feldliste "PivotTable"**, beachten Sie, dass die **Datum** und **Internetverkäufe** Measures angezeigt werden, als auch die **Kunden**,  **Datum**, **Geography**, **Produkt**, **Produktkategorie**, **Produktunterkategorie**, und **Internetverkäufe** Tabellen mit der entsprechenden Spalten angezeigt werden.  
  
4.  Schließen Sie Excel, ohne die Arbeitsmappe zu speichern.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>So durchsuchen Sie das Modell mit der Internet Sales-Perspektive  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und dann auf **In Excel analysieren**.  
  
2.  Lassen Sie im Dialogfeld **In Excel analysieren** die Option **Aktueller Windows-Benutzer** aktiviert, wählen Sie im Dropdownlistenfeld **Perspektive** den Eintrag **Internet Sales** aus, und klicken Sie anschließend auf **OK**. Excel wird geöffnet.  
  
3.  Beachten Sie, dass in Excel in der **PivotTable-Feldliste**die Tabelle Customer aus der Feldliste ausgeschlossen ist.  
  
## <a name="browse-using-roles"></a>Durchsuchen mit Rollen  
 Rollen sind wesentlicher Bestandteil sämtlicher tabellarischer Modelle. Benutzer können keine Daten mit Ihrem Modell aufrufen und analysieren, wenn sie nicht mindestens einer Rolle als Mitglieder hinzugefügt wurden. Die Funktion In Excel analysieren bietet eine Möglichkeit zum Testen der Rollen, die Sie definiert haben.  
  
#### <a name="to-browse-by-using-the-internet-sales-manager-user-role"></a>So durchsuchen Sie das Modell mit der Internet Sales Manager-Benutzerrolle  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und dann auf **In Excel analysieren**.  
  
2.  Wählen Sie im Dialogfeld **In Excel analysieren** in **Geben Sie den Benutzernamen oder die Benutzerrolle zum Herstellen einer Verbindung mit dem Modell an**die Option **Rolle**aus, wählen Sie im Dropdownlistenfeld **Internet Sales Manager**aus, und klicken Sie anschließend auf **OK**.  
  
     Excel wird mit einer neuen Arbeitsmappe geöffnet. Es wird automatisch eine PivotTable erstellt. Die PivotTable-Feldliste enthält alle Datenfelder, die im neuen Modell verfügbar sind.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 14: Bereitstellen](lesson-13-deploy.md).  
  
  
