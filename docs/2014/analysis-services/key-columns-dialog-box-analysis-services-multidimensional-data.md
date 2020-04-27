---
title: Schlüssel Spalten (Dialog Feld) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.dataitemCollection.f1
helpviewer_keywords:
- DataItem Collection dialog box
ms.assetid: 585f27f2-d5eb-4516-b29a-2084010b7d51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 26eb85c97c970f9fe1cfaf63ca9861c2be0b4695
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66079466"
---
# <a name="key-columns-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld Schlüsselspalten (Analysis Services – Mehrdimensionale Daten)
  Verwenden Sie das Dialogfeld **Schlüsselspalten** , um die **KeyColumns** -Eigenschaft eines Attributs zu ändern. Weitere Informationen finden Sie unter [Ändern der KeyColumn-Eigenschaft eines Attributs](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).  
  
 **So zeigen Sie das Dialogfeld Schlüsselspalten an**  
  
-   Wählen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ein Attribut aus, und klicken Sie dann im Fenster **Eigenschaften** in der**KeyColumns**-Eigenschaftszelle auf die Schaltfläche mit den drei Punkten ( **...** ).  
  
## <a name="options"></a>Optionen  
 **Quelltabelle**  
 Wählen Sie die Quelltabelle aus, für die Sie die Schlüsselspalten auswählen möchten. Sie können die Quelltabelle in der Datenquellensicht in einer Liste aller Tabellen auswählen.  
  
 **Verfügbare Spalten**  
 Wählen Sie die Spalten aus, die Sie als Schlüsselspalten verwenden möchten. Sie können die Spalten in einer Liste auswählen, die alle Spalten der angegebenen **Quelltabelle** enthält, die noch nicht als Schlüsselspalten ausgewählt wurden.  
  
 Sie fügen die ausgewählten Spalten der Liste **Schlüsselspalten** hinzu, indem Sie auf die Schaltfläche **>** klicken.  
  
 **Schlüsselspalten**  
 Definieren Sie die Reihenfolge der ausgewählten Schlüsselspalten. Die Reihenfolge der Schlüsselspalten ist wichtig für die Definition des richtigen zusammengesetzten Schlüssels. Um die Reihenfolge von Schlüsselspalten zu ändern, wählen Sie eine Spalte aus und klicken dann auf die Schaltfläche **Nach oben** oder **Nach unten** .  
  
 Um eine Spalte aus der Liste **Schlüsselspalten** zu entfernen, wählen Sie die Spalte aus, und klicken Sie anschließend auf die Schaltfläche **\<** klicken.  
  
 **Nach oben**  
 Klicken Sie auf diese Schaltfläche, um die in der Liste **Schlüsselspalten** ausgewählte Spalte um eine Position nach oben zu verschieben.  
  
> [!NOTE]  
>  Diese Option ist nur dann aktiviert, wenn die Liste mehrere Spalten umfasst und eine Spalte ausgewählt ist.  
  
 **Nach unten**  
 Klicken Sie auf diese Schaltfläche, um die in der Liste **Schlüsselspalten** ausgewählte Spalte um eine Position nach unten zu verschieben.  
  
> [!NOTE]  
>  Diese Option ist nur dann aktiviert, wenn die Liste mehrere Spalten umfasst und eine Spalte ausgewählt ist.  
  
 **>**  
 Klicken Sie auf diese Option, um am Ende der Liste **Schlüsselspalten**eine neue Spalte hinzuzufügen.  
  
 **<**  
 Klicken Sie auf diese Schaltfläche, um die ausgewählte Spalte aus den in der Liste **Schlüsselspalten**aufgeführten Spalten zu entfernen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
