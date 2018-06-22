---
title: 'Die folgenden Funktionen werden von Excel Services nicht unterstützt und möglicherweise nicht angezeigt oder möglicherweise nur teilweise angezeigt: Kommentare, Formen oder andere Objekte | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 4
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: de9ce6b0d7123cf2156483e6357cef25609ba4fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061501"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a>Die folgenden Funktionen werden von Excel Services nicht unterstützt und möglicherweise nur teilweise oder überhaupt nicht angezeigt: Kommentare, Formen oder andere Objekte
  Dieser Fehler tritt auf, wenn Sie einer PowerPivot-Arbeitsmappe Slicer aus einer PowerPivot-Feldliste hinzufügen.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für|PowerPivot für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Das Shape-Objekt, mit dem die Positionierung und Formatierung von Slicern gesteuert wird, die einer Arbeitsmappe aus der PowerPivot-Feldliste hinzugefügt wurden, kann von Excel Web Access nicht gerendert werden.|  
|Meldungstext|Die folgenden Funktionen werden von Excel Services nicht unterstützt und möglicherweise nur teilweise oder überhaupt nicht angezeigt:<br /><br /> Kommentare, Formen oder andere Objekte<br /><br /> Einige Funktionen z. B. externe Datenabfragen, zeigen zwischengespeicherte Daten an, die nur in Microsoft Excel aktualisiert werden können.|  
  
## <a name="explanation"></a>Erklärung  
 Excel Web Access zeigt diesen Fehler, wenn Sie eine PowerPivot-Arbeitsmappe in einem Browser öffnen und auf die **Details** Schaltfläche für die Nachricht **nicht unterstützte Funktionen diese Arbeitsmappe kann nicht wie vorgesehen angezeigt**.  
  
 Dieser Fehler tritt auf, weil die PowerPivot-Arbeitsmappe Slicer enthält, deren Layout über ein ausgeblendetes Shape-Objekt in Excel gesteuert wird. Das Shape-Objekt steuert die Formatierung und Positionierung der Slicer in horizontalen und vertikalen Platzierungen.  
  
 Shape-Objekte können von Excel Services nicht gerendert werden, dies ist jedoch kein Problem, weil es sich um ein ausgeblendetes Objekt handelt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Dieser Fehler kann ignoriert werden. Klicken Sie auf **OK** , um die Fehlermeldung zu schließen und die Verwendung von Arbeitsmappe und Slicern ohne Probleme fortzusetzen.  
  
  