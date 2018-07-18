---
title: Binden das Dialogfeld Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 52a860a5228494eef64955c6f3ee4d0c577d9a87
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299130"
---
# <a name="object-binding-dialog-box"></a>Objektbindung (Dialogfeld)
  Mithilfe des Dialogfelds **Objektbindung** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie Bindungen zwischen der Eigenschaft eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekts und einer Tabelle oder Spalte in einer Datenquellensicht definieren. Sie können das Dialogfeld **Objektbindung** anzeigen, indem Sie im Fenster **Eigenschaften** von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] aus der Dropdownliste den Wert **(Neu)** für folgende Eigenschaften eines [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]-Objekts wählen:  
  
-   NameColumn  
  
-   ValueColumn  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   UnaryOperatorColumn  
  
## <a name="options"></a>Tastatur  
 **Typ der datenbankbindung**  
 Wählen Sie die Bindung aus, die für das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt verwendet werden soll. Folgende Bindungstypen können verwendet werden:  
  
 Spaltenbindung  
 Bindet das Objekt innerhalb einer Datenquellensicht an eine vorhandene Tabelle und Spalte.  
  
 Spalte generieren  
 Zeigt an, dass eine neue Spalte in der Datenquellensicht definiert wird, der dann eine Spaltenbindung zugeordnet wird.  
  
> [!NOTE]  
>  Wenn diese Option ausgewählt ist, müssen Sie **Schemagenerierungs-Assistent** ausführen, bevor Sie das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt bereitstellen.  
  
 Zeilenbindung  
 Bindet das Objekt an eine Zeile in einer Faktentabelle und wird verwendet, um die Zählung von Measures anhand der Anzahl der in der Faktentabelle verarbeiteten Zeilen zu vereinfachen.  
  
 **Quelltabelle**  
 Zeigt eine Liste von Tabellen in der Datenquellensicht an, die dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt zugeordnet sind.  
  
 **Quellspalte**  
 Zeigt eine Liste von Spalten in der unter **Quelltabelle**ausgewählten Tabelle an.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
