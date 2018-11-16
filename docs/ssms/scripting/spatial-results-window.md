---
title: Fenster "Räumliche Ergebnisse" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 422114f2a753327f34b105c4c6893b7c3f8d3c2b
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51643227"
---
# <a name="spatial-results-window"></a>Fenster "Räumliche Ergebnisse"
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Im Fenster **Räumliche Ergebnisse** werden visuelle Zuordnungstools zum Anzeigen räumlicher Daten bereitgestellt. Zum Anzeigen von Ergebnissen für räumliche Daten müssen die Abfrageergebnisse eine räumliche Spalte mit Geometrie- oder Geografiedaten enthalten.  
  
> [!NOTE]  
>  Das Fenster **Räumliche Ergebnisse** ist nur verfügbar, wenn die Ergebnisse im Fenster **Ergebnisse** in ein Raster zurückgegeben werden. Wenn Sie angeben, dass die Ergebnisse als Text zurückgegeben werden, ist dieses Fenster nicht verfügbar.  
  
## <a name="options"></a>Tastatur  
 **Räumliche Spalte auswählen**  
 Geben Sie die räumliche Spalte an, die Sie in den Abfrageergebnissen in den räumlichen Spalten anzeigen möchten. Es kann nur jeweils eine Spalte ausgewählt werden.  
  
 **Bezeichnungsspalte auswählen**  
 Geben Sie die nicht räumliche Spalte in den Spalten an, die in den Abfrageergebnissen zurückgegeben wurden, um die räumlichen Daten zu beschriften. Es kann nur jeweils eine Spalte ausgewählt werden.  
  
 Diese Option ist nicht verfügbar, wenn in einer Abfrage nur Instanzen zurückgegeben werden.  
  
 **Projektion auswählen**  
 Sie können Geografiedaten in einer von vier Projektionen anzeigen: Equirectangular, Mercator, Robinson oder Bonne.  
  
 Diese Option ist für Geometriedaten nicht verfügbar.  
  
 **Zoom**  
 Stellen Sie die Zuordnungsanzeige auf einer exponentiellen Skala ein.  
  
 **Gitternetzlinien anzeigen**  
 Sie können Koordinatengitternetzlinien aktivieren oder deaktivieren.  
  
 Bei polygonen Formen wird die Bezeichnung nur angezeigt, wenn die Form groß genug ist, um den Bezeichnungstext aufzunehmen. Um Bezeichnungen für kleine Formen anzuzeigen, passen Sie den Zoom an.  
  
> [!NOTE]  
>  Punktinstanzen können nicht bezeichnet werden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Anzeigen räumlicher Daten im Objekt-Explorer](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Abfrage-Editor der Datenbank-Engine &amp;amp;#40;SQL Server Management Studio&amp;amp;#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Abfrage- und Text-Editoren &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
