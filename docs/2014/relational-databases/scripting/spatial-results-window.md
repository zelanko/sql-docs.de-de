---
title: Fenster "Räumliche Ergebnisse"
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c554959fedba58f743f1dd37d3c97554d0f00d3
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243253"
---
# <a name="spatial-results-window"></a>Fenster "Räumliche Ergebnisse"
  Im Fenster **Räumliche Ergebnisse** werden visuelle Zustellungs Tools zum Anzeigen räumlicher Daten bereitstellt. Zum Anzeigen von Ergebnissen für räumliche Daten müssen die Abfrageergebnisse eine räumliche Spalte mit Geometrie- oder Geografiedaten enthalten.  
  
> [!NOTE]  
>  Das Fenster **Räumliche Ergebnisse** ist nur verfügbar, wenn die Ergebnisse im Fenster **Ergebnisse** in ein Raster zurückgegeben werden. Wenn Sie angeben, dass die Ergebnisse als Text zurückgegeben werden, ist dieses Fenster nicht verfügbar.  
  
## <a name="options"></a>Optionen  
 **Räumliche Spalte auswählen**  
 Geben Sie die räumliche Spalte an, die Sie in den Abfrageergebnissen in den räumlichen Spalten anzeigen möchten. Es kann nur jeweils eine Spalte ausgewählt werden.  
  
 **Bezeichnungs Spalte auswählen**  
 Geben Sie die nicht räumliche Spalte in den Spalten an, die in den Abfrageergebnissen zurückgegeben wurden, um die räumlichen Daten zu beschriften. Es kann nur jeweils eine Spalte ausgewählt werden.  
  
 Diese Option ist nicht verfügbar, wenn in einer Abfrage nur Instanzen zurückgegeben werden.  
  
 **Projektion auswählen**  
 Sie können Geografiedaten in einer von vier Projektionen anzeigen: Equirectangular, Mercator, Robinson oder Bonne.  
  
 Diese Option ist für Geometriedaten nicht verfügbar.  
  
 **Skala**  
 Stellen Sie die Zuordnungsanzeige auf einer exponentiellen Skala ein.  
  
 **Rasterlinien anzeigen**  
 Sie können Koordinatengitternetzlinien aktivieren oder deaktivieren.  
  
 Bei polygonen Formen wird die Bezeichnung nur angezeigt, wenn die Form groß genug ist, um den Bezeichnungstext aufzunehmen. Um Bezeichnungen für kleine Formen anzuzeigen, passen Sie den Zoom an.  
  
> [!NOTE]  
>  Punktinstanzen können nicht bezeichnet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Räumliche Daten in Objekt-Explorer anzeigen](view-spatial-data-in-object-explorer.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)   
 [Datenbank-Engine Abfrage-Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md)   
 [Abfrage-und Text-Editoren &#40;SQL Server Management Studio&#41;](query-and-text-editors-sql-server-management-studio.md)  
  
  
