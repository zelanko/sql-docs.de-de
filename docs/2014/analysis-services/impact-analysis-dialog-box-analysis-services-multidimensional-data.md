---
title: Auswirkungs Analyse (Dialog Feld) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.impactanalysisdialog.f1
ms.assetid: 208268eb-4e14-44db-9c64-6f74b776adb6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92c7e91e090b8e82e2844cf1999328c6ef7a8684
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544272"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Auswirkungsanalyse' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Auswirkungsanalyse** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie abhängige Objekte identifizieren und optional verarbeiten, auf die sich das Verarbeiten der im Dialogfeld **Verarbeiten** aufgeführten Objekte auswirkt. Zum Anzeigen des Dialogfelds **Auswirkungsanalyse** klicken Sie im Dialogfeld **Verarbeiten** auf **Auswirkungsanalyse** .  
  
> [!NOTE]  
>  Ein Objekt wird mehrfach angezeigt, wenn es auf mehr als eine Weise betroffen ist.  
  
## <a name="options"></a>Optionen  
 **Objektliste**  
 Zeigt eine Liste abhängiger Objekte in einem Raster an. Das Raster enthält die folgenden Spalten:  
  
 **Objektnamen**  
 Zeigt den Namen des abhängigen Objekts an, das ggf. verarbeitet werden muss. Das Symbol links vom Namen gibt den Objekttyp an.  
  
 **Typ**  
 Zeigt den Typ des abhängigen Objekts an, das ggf. verarbeitet werden muss.  
  
 **Auswirkungstyp**  
 Zeigt die Auswirkung an, die das Verarbeiten der Objekte im Dialogfeld **Verarbeiten** auf das abhängige Objekt hat. Die folgende Tabelle führt die möglichen Auswirkungen der Verarbeitung auf und gibt an, ob eine Auswirkung zu einer Warnung oder einem Fehler führt.  
  
|Auswirkung|`Message`|  
|------------|-------------|  
|Objekt wird gelöscht (keine Verarbeitung)|Warnung|  
|Objekt wäre ungültig|Fehler|  
|Aggregation würde gelöscht|Warnung|  
|Flexible Aggregation würde gelöscht|Warnung|  
|Indizes werden gelöscht|Warnung|  
|Nicht untergeordnetes Objekt wird verarbeitet|Warnung|  
  
 **Objekt verarbeiten**  
 Wählen Sie die abhängigen Objekte aus, die Sie mit dem Verarbeitungsvorgang verarbeiten möchten Nicht ausgewählte abhängige Objekte müssen verarbeitet werden, nachdem der Verarbeitungsvorgang abgeschlossen ist. Andernfalls können sie nicht verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Verarbeiten (Dialog Feld) &#40;Analysis Services-mehrdimensionalen Daten&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
