---
title: Anzeigen räumlicher Daten im Objekt-Explorer
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5ac09bdbc05f406d8d7925af1c9a45346913151
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75242945"
---
# <a name="view-spatial-data-in-object-explorer"></a>Anzeigen räumlicher Daten im Objekt-Explorer
  Das Fenster **Räumliche Ergebnisse** im Abfrage-Editor bietet visuelle Zustellungs Tools zum Anzeigen von räumlichen Daten Ergebnissen zusätzlich zu den Daten, die im Fenster **Ergebnisse** im Raster Format angezeigt werden. Zum Anzeigen räumlicher Daten im Fenster **Räumliche Ergebnisse** müssen die Abfrageergebnisse mindestens eine Spalte für räumliche Daten mit Geometrie- oder Geografiedaten enthalten.  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>So zeigen Sie räumliche Daten im Fenster "Räumliche Ergebnisse" an  
  
1.  Klicken Sie im Abfrage-Editor auf die Registerkarte **Räumliche Ergebnisse** .  
  
    > [!NOTE]  
    >  Dieses Fenster ist nicht verfügbar, wenn die Abfrageergebnisse keine räumlichen Daten enthalten oder Sie angeben, dass die Ergebnisse als Text zurückgegeben werden.  
  
2.  Wählen Sie die anzuzeigende Spalte in der Liste **Räumliche Spalte auswählen** aus. Wenn in der Tabelle nur eine räumliche Spalte enthalten ist, bildet diese Spalte die Standardoption in der Liste.  
  
3.  Wählen Sie in der Liste **Bezeichnungsspalte auswählen** die nicht räumliche Spalte aus, die Sie für Datenbezeichnungen verwenden möchten.  
  
4.  Wählen Sie in der Liste **Projektion auswählen** die Projektion aus, die Sie für Geografiedaten verwenden möchten. Die Standardprojektion ist Equirectangular. Andere verfügbare Projektionen sind Mercator, Robinson und Bonne.  
  
    > [!NOTE]  
    >  **Wählen Sie Projektion** ist nicht verfügbar, wenn die räumliche Spalte Geometriedaten enthält.  
  
5.  Stellen Sie den Schieberegler **Zoom** ein, um zugeordnete Elemente visuell zu vergrößern. Bei polygonalen Formen ist die Bezeichnung nur sichtbar, wenn die Form groß genug ist, um den Bezeichnungstext aufzunehmen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fenster "Räumliche Ergebnisse"](spatial-results-window.md)   
 [Datenbank-Engine Abfrage-Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md)   
 [Abfrage-und Text-Editoren &#40;SQL Server Management Studio&#41;](query-and-text-editors-sql-server-management-studio.md)  
  
  
