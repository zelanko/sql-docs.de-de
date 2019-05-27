---
title: Binden das Dialogfeld Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cc86a5712dae9c231fa6e03d86a82d7dc172a75
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66072187"
---
# <a name="object-binding-dialog-box"></a>Objektbindung (Dialogfeld)
  Mithilfe des Dialogfelds **Objektbindung** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie Bindungen zwischen der Eigenschaft eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekts und einer Tabelle oder Spalte in einer Datenquellensicht definieren. Sie können das Dialogfeld **Objektbindung** anzeigen, indem Sie im Fenster **Eigenschaften** von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] aus der Dropdownliste den Wert **(Neu)** für folgende Eigenschaften eines [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]-Objekts wählen:  
  
-   NameColumn  
  
-   ValueColumn  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   UnaryOperatorColumn  
  
## <a name="options"></a>Optionen  
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
  
  
