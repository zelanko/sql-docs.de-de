---
title: Anzeigen räumlicher Daten im Objekt-Explorer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de527a4961ac3ba297929bc8fb9b808681c6c3ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206780"
---
# <a name="view-spatial-data-in-object-explorer"></a>Anzeigen räumlicher Daten im Objekt-Explorer
  Im Fenster **Räumliche Ergebnisse** des Abfrage-Editors werden visuelle Zuordnungstools bereitgestellt, mit denen Sie zusätzlich zu den im Fenster **Ergebnisse** im Rasterformat angezeigten Daten Ergebnisse für räumliche Daten anzeigen können. Zum Anzeigen räumlicher Daten im Fenster **Räumliche Ergebnisse** müssen die Abfrageergebnisse mindestens eine Spalte für räumliche Daten mit Geometrie- oder Geografiedaten enthalten.  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>So zeigen Sie räumliche Daten im Fenster "Räumliche Ergebnisse" an  
  
1.  Klicken Sie im Abfrage-Editor auf die Registerkarte **Räumliche Ergebnisse** .  
  
    > [!NOTE]  
    >  Dieses Fenster ist nicht verfügbar, wenn die Abfrageergebnisse keine räumlichen Daten enthalten oder Sie angeben, dass die Ergebnisse als Text zurückgegeben werden.  
  
2.  Wählen Sie die anzuzeigende Spalte in der Liste **Räumliche Spalte auswählen** aus. Wenn in der Tabelle nur eine räumliche Spalte enthalten ist, bildet diese Spalte die Standardoption in der Liste.  
  
3.  Wählen Sie in der Liste **Bezeichnungsspalte auswählen** die nicht räumliche Spalte aus, die Sie für Datenbezeichnungen verwenden möchten.  
  
4.  Wählen Sie in der Liste **Projektion auswählen** die Projektion aus, die Sie für Geografiedaten verwenden möchten. Die Standardprojektion ist Equirectangular. Andere verfügbare Projektionen sind Mercator, Robinson und Bonne.  
  
    > [!NOTE]  
    >  **Projektion auswählen** ist nicht verfügbar, wenn die räumliche Spalte Geometriedaten enthält.  
  
5.  Stellen Sie den Schieberegler **Zoom** ein, um zugeordnete Elemente visuell zu vergrößern. Bei polygonalen Formen ist die Bezeichnung nur sichtbar, wenn die Form groß genug ist, um den Bezeichnungstext aufzunehmen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fenster "Räumliche Ergebnisse"](spatial-results-window.md)   
 
  [Abfrage-Editor der Datenbank-Engine &amp;#40;SQL Server Management Studio&amp;#41;](database-engine-query-editor-sql-server-management-studio.md)   
 [Abfrage- und Text-Editoren &#40;SQL Server Management Studio&#41;](query-and-text-editors-sql-server-management-studio.md)  
  
  
