---
title: Auswirkungen auf die Analysis (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 0c08690cd2f5b77471392cab3aad1587b4cb0f9a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66080750"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Auswirkungsanalyse' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Auswirkungsanalyse** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie abhängige Objekte identifizieren und optional verarbeiten, auf die sich das Verarbeiten der im Dialogfeld **Verarbeiten** aufgeführten Objekte auswirkt. Zum Anzeigen des Dialogfelds **Auswirkungsanalyse** klicken Sie im Dialogfeld **Verarbeiten** auf **Auswirkungsanalyse** .  
  
> [!NOTE]  
>  Ein Objekt wird mehrfach angezeigt, wenn es auf mehr als eine Weise betroffen ist.  
  
## <a name="options"></a>Optionen  
 **Objektliste**  
 Zeigt eine Liste abhängiger Objekte in einem Raster an. Das Raster enthält die folgenden Spalten:  
  
 **Objektname**  
 Zeigt den Namen des abhängigen Objekts an, das ggf. verarbeitet werden muss. Das Symbol links vom Namen gibt den Objekttyp an.  
  
 **Typ**  
 Zeigt den Typ des abhängigen Objekts an, das ggf. verarbeitet werden muss.  
  
 **Auswirkungstyp**  
 Zeigt die Auswirkung an, die das Verarbeiten der Objekte im Dialogfeld **Verarbeiten** auf das abhängige Objekt hat. Die folgende Tabelle führt die möglichen Auswirkungen der Verarbeitung auf und gibt an, ob eine Auswirkung zu einer Warnung oder einem Fehler führt.  
  
|Auswirkung|MessageBox|  
|------------|-------------|  
|Objekt wird gelöscht (keine Verarbeitung)|Warnung|  
|Objekt wäre ungültig|Fehler|  
|Aggregation würde gelöscht|Warnung|  
|Flexible Aggregation würde gelöscht|Warnung|  
|Indizes werden gelöscht|Warnung|  
|Nicht untergeordnetes Objekt wird verarbeitet|Warnung|  
  
 **Objekt verarbeiten**  
 Wählen Sie die abhängigen Objekte aus, die Sie mit dem Verarbeitungsvorgang verarbeiten möchten Nicht ausgewählte abhängige Objekte müssen verarbeitet werden, nachdem der Verarbeitungsvorgang abgeschlossen ist. Andernfalls können sie nicht verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Verarbeiten Sie das Dialogfeld &#40;Analysis Services – mehrdimensionale Daten&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
