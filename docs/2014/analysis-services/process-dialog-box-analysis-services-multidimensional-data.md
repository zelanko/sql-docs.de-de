---
title: Verarbeiten (Dialog Feld) (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.processdialog.f1
ms.assetid: c065248c-9001-4f0c-928f-9c59eccb618b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 32411ff5b715e15fd52b832d8047d8382a603924
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070747"
---
# <a name="process-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Verarbeiten' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Verarbeiten** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekte verarbeiten. Das Dialogfeld **Verarbeiten** von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie folgendermaßen aufrufen:  
  
-   Klicken Sie in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Projektmappen-Explorer** mit der rechten Maustaste auf ein Projekt, einen Cube, eine Dimension oder eine Miningstruktur von **, und wählen Sie **Verarbeiten** aus.  
  
-   Wählen Sie auf der Symbolleiste auf jeder Seite von **Cube-Designer** und **Dimensions-Designer**oder auf den Seiten **Miningstruktur**und **Miningmodelle** von **Modell-Designer für Data Mining** die Option **Verarbeiten**aus.  
  
-   Klicken Sie auf der Seite **Miningmodelle** von **Modell-Designer für Data Mining** mit der rechten Maustaste auf ein Miningmodell, und wählen Sie **Miningstruktur und alle Modelle verarbeiten** oder **Modell verarbeiten** aus.  
  
 Das Dialogfeld **Verarbeiten** von **SQL Server Management Studio** können Sie folgendermaßen aufrufen:  
  
-   Klicken Sie in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Objekt-Explorer** mit der rechten Maustaste auf eine Datenbank, einen Cube, eine Measuregruppe, eine Partition, eine Dimension, eine Miningstruktur oder ein Miningmodell von **, und wählen Sie **Verarbeiten** aus.  
  
## <a name="options"></a>Tastatur  
 **Objektliste**  
 Wählen Sie die zu verarbeitenden [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Objekte und die anzuwendenden Verarbeitungsoptionen und -einstellungen aus. Das Raster enthält die folgenden Spalten:  
  
 **Objektnamen**  
 Zeigt den Namen des zu verarbeitenden Objekts an. Das Symbol links vom Namen gibt den Objekttyp an.  
  
 **Typ**  
 Zeigt den Typ des zu verarbeitenden Objekts an.  
  
 **Prozess Optionen**  
 Wählen Sie den auszuführenden Verarbeitungstyp für das ausgewählte Objekt aus. Weitere Informationen zu verfügbaren Verarbeitungsoptionen finden Sie unter Verarbeitung von mehr [dimensionalen Modell Objekten](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 **Einstellungen**  
 Zeigt den Link **Konfigurieren** an, wenn Sie für Cubes, Measuregruppen oder Partitionen unter **Verarbeitungsoptionen** die Option **Inkrementell verarbeiten** auswählen. Klicken Sie auf **Konfigurieren** , um das Dialogfeld **Inkrementelles Update** zu öffnen. Weitere Informationen zum Dialogfeld **Inkrementelles Update** finden Sie unter [Inkrementelles Update &#40;Dialogfeld, Analysis Services – Mehrdimensionale Daten&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Remove**  
 Klicken Sie auf diese Option, um die ausgewählten Elemente aus **Objektliste** zu entfernen.  
  
 **Auswirkungs Analyse**  
 Klicken Sie auf diese Option, um das Dialogfeld **Auswirkungsanalyse** zu öffnen und die Objekte anzuzeigen, die von dem Verarbeitungstask betroffen sind. Weitere Informationen zum Dialogfeld **Auswirkungsanalyse** finden Sie unter [Auswirkungsanalyse &#40;Dialogfeld, Analysis Services – Mehrdimensionale Daten&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>  Diese Option ist deaktiviert, wenn im Dialogfeld **Einstellungen ändern** die Option **Betroffene Objekte verarbeiten** ausgewählt ist.  
  
 **Einstellungen ändern**  
 Klicken Sie auf diese Option, um das Dialogfeld **Einstellungen ändern** zu öffnen und die Einstellungen zu ändern, die die Verarbeitung der ausgewählten Objekte bestimmen, einschließlich der Batchverarbeitungseinstellungen, Rückschreibeeinstellungen und Einstellungen für Dimensionsschlüsselfehler. Weitere Informationen zum Dialogfeld **Einstellungen ändern** finden Sie unter [Einstellungen ändern &#40;Dialogfeld, Analysis Services – Mehrdimensionale Daten&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Ausführen**  
 Klicken Sie auf diese Option, um die Objekte zu verarbeiten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Dialog Feld ' Verarbeitungs Status ' &#40;Analysis Services Mehrdimensionale Daten&#41;](process-progress-dialog-box-analysis-services-multidimensional-data.md)  
  
  
