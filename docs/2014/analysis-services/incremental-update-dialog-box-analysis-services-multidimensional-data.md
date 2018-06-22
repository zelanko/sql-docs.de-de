---
title: Inkrementelles Update (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 51fb9898eb2d43fd56cbefb6f08120669dcd6f0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147787"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Inkrementelles Update' (Analysis Services – Mehrdimensionale Daten)
  In **und** können Sie im Dialogfeld [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] Inkrementelles Update [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] die Einstellungen definieren, die beim inkrementellen Update von Measuregruppen und Partitionen verwendet werden sollen. Klicken Sie im Dialogfeld **Verarbeiten** im Raster **Objektliste** in der **Settings** -Spalte auf **Konfigurieren** , um das Dialogfeld **Inkrementelles Update** anzuzeigen.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Measuregruppe**|Wählen Sie die Measuregruppe aus, die inkrementell aktualisiert werden soll.<br /><br /> Hinweis: Diese Option ist nur beim inkrementellen Aktualisieren von Cubes aktiviert. Wenn eine Measuregruppe oder eine Partition inkrementell aktualisiert wird, ist die Option deaktiviert.|  
|**Partition**|Wählen Sie die zu aktualisierende Partition aus.<br /><br /> Hinweis: Diese Option ist nur beim inkrementellen Aktualisieren von Cubes aktiviert. Wenn eine Measuregruppe oder eine Partition inkrementell aktualisiert wird, ist die Option deaktiviert.|  
|**Tabelle**|Klicken Sie hier, um das Objekt von einer Tabelle aus zu aktualisieren.|  
|**Datenquelle oder Datenquellensicht**|Wählen Sie die Datenquelle oder die Datenquellensicht aus, in der sich die Quelltabelle befindet.<br /><br /> Hinweis: Diese Option ist nur aktiviert, wenn **Tabelle** ausgewählt wird.|  
|**Tabellenschema und-Name**|Wählen Sie die Quelltabelle aus, aus der die Daten für das inkrementelle Update des Cubes, der Measuregruppe oder der Partition abgerufen werden sollen.<br /><br /> Hinweis: Diese Option ist nur aktiviert, wenn **Tabelle** ausgewählt wird.|  
|**Dataseteigenschaften**|Klicken Sie hier, um das Objekt von einer Abfrage aus zu aktualisieren.|  
|**Data Source**|Wählen Sie die Datenquelle aus, in der sich die Tabellen für die Abfrage befinden.<br /><br /> Hinweis: Diese Option ist nur aktiviert, wenn **Abfrage** ausgewählt wird.|  
|**Text der Abfrage**|Geben Sie den Abfragetext ein, der verwendet werden soll, um die Daten für das inkrementelle Update des Cubes, der Measuregruppe oder der Partition abzurufen.<br /><br /> Hinweis: Diese Option ist nur aktiviert, wenn **Abfrage** ausgewählt wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Verarbeiten Sie das Dialogfeld &#40;Analysis Services – mehrdimensionale Daten&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  