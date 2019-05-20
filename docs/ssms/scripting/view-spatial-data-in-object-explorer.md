---
title: Anzeigen räumlicher Daten im Objekt-Explorer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6437815a0251d3369d05ec479790752dd2aaf88e
ms.sourcegitcommit: c29150492383f48ef484fa02a483cde1cbc68aca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65821739"
---
# <a name="view-spatial-data-in-object-explorer"></a>Anzeigen räumlicher Daten im Objekt-Explorer
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Fenster "Räumliche Ergebnisse"](../../relational-databases/scripting/spatial-results-window.md)   
 [Abfrage-Editor der Datenbank-Engine &amp;amp;#40;SQL Server Management Studio&amp;amp;#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Abfrage- und Text-Editoren &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
