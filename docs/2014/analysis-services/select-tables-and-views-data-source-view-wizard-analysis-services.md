---
title: Tabellen und Sichten auswählen (Datenquellen Sicht-Assistent) (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.selecttablesandviews.f1
ms.assetid: ea7d1232-f213-46e9-90d9-0fd616ca003d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f4b940d5cb3c91cc8257ef1a3e6828286bc1c240
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66069251"
---
# <a name="select-tables-and-views-data-source-view-wizard-analysis-services"></a>Tabellen und Sichten auswählen (Datenquellensicht-Assistent) (Analysis Services)
  Mithilfe der Seite **Tabellen und Sichten auswählen** können Sie die Tabellen und Sichten aus der Datenquelle auswählen, die Sie in die Datenquellensicht aufnehmen möchten.  
  
## <a name="options"></a>Optionen  
 **Available objects**  
 Führt die Tabellen und Sichten im Datenquellenschema auf. Wenn mehr als ein Schema aufgeführt ist, erhält der Name jedes Objekts den Schemanamen als Präfix. Bei nur einem aufgeführten Schema wird der Name des Schemas nicht als Präfix für die Objektnamen verwendet.  
  
 Zum erneuten Ordnen der Liste in aufsteigender oder absteigender Reihenfolge klicken Sie entweder auf **Name** oder auf **Typ**.  
  
 **Included objects**  
 Führt die in die Datenquellensicht einzuschließenden Tabellen und Sichten auf.  
  
 Zum erneuten Ordnen der Liste in aufsteigender oder absteigender Reihenfolge klicken Sie entweder auf **Name** oder auf **Typ**.  
  
 **Filter**  
 Filtert die unter **Verfügbare Objekte**aufgeführten Objekte. Geben Sie eine Zeichenfolge ein, und klicken Sie dann auf **Filtern** , um nur die Namen anzuzeigen, die die angegebene Zeichenfolge enthalten. Zum Auffinden einer genauen Zeichenfolge schließen Sie die Zeichenfolge in doppelte Anführungszeichen ein. Der Filter unterscheidet nicht zwischen Groß- und Kleinschreibung.  
  
 Sie können die in der folgenden Tabelle aufgeführten Platzhalterzeichen an beliebiger Stelle in der Filterzeichenfolge verwenden.  
  
|Platzhalter|Wert|  
|------------------------|-----------|  
|**\***|Beliebige Zeichenfolge|  
|**%**|Beliebige Zeichenfolge|  
|**?**|Ein einzelnes Zeichen|  
|**"** *Zeichenfolge* **"**|Eine Literalzeichenfolge. Dieses Platzhalterzeichen entspricht jeder Teilzeichenfolge innerhalb des Objektnamens.|  
  
 **Systemobjekte anzeigen**  
 Zeigt unter **Verfügbare Objekte**Systemobjekte an. Diese Option steht nur zur Verfügung, wenn der Datenquellenanbieter Systemobjekte verfügbar macht. Durch das Entfernen eines Systemobjekts aus der Liste **Eingeschlossene Objekte** wird diese Option automatisch ausgewählt.  
  
 **Add related tables**  
 Fügt alle Tabellen hinzu, die mit den unter **Eingeschlossene Objekte**aufgeführten verknüpft sind. Mit dieser Option können keine Sichten hinzugefügt werden. Das Hinzufügen partitionierter Tabellen ist mithilfe dieser Option jedoch möglich. Wenn Sie auf der Seite **Namensübereinstimmung** des Assistenten Kriterien für die Namensübereinstimmung auswählen, schließt diese Option auch logisch verknüpfte Tabellen entsprechend der von Ihnen ausgewählten Kriterien ein. Tabellen werden auch eingeschlossen, wenn sie mit den neu hinzugefügten verknüpften Tabellen verknüpft sind und wenn sie eine identische Struktur wie die ursprüngliche Tabelle haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellen Sicht-Assistent (F1-Hilfe &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md)   
 [Datenquellsichten in mehrdimensionalen Modellen](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
