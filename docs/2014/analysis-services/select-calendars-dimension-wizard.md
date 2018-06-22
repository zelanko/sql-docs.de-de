---
title: Kalender auswählen (Dimensions-Assistent) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dimensionwizard.serverSpecialCalendars.f1
ms.assetid: 6e28a020-2586-4b13-9333-b499fb1b33af
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6796c7c3064adc65982b1d5aaec005249e224cae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057887"
---
# <a name="select-calendars-dimension-wizard"></a>Kalender auswählen (Dimensions-Assistent)
  Auf der Seite **Kalender auswählen** können Sie für eine gegebene Zeitdimension zusätzliche Hierarchien zur Darstellung von Geschäfts-, Berichts-, Produktions- oder ISO 8601-Kalendern (International Organization for Standardization, Internationale Organisation für Normung) erstellen.  
  
> [!NOTE]  
>  Diese Seite wird nur angezeigt, wenn auf der Seite **Dimensionstyp auswählen** die Option **Serverzeitdimension** oder auf der Seite **Erstellungsmethode auswählen** die Option **Dimension ohne eine Datenquelle erstellen** und auf der Seite **Dimensionstyp auswählen** die Option **Zeitdimension** ausgewählt wurden.  
  
## <a name="options"></a>Tastatur  
 **Geschäftskalender**  
 Wählen Sie diese Option aus, um eine Zeithierarchie basierend auf einem Geschäftskalender zu erstellen.  
  
 **Starttag und-Monat**  
 Wählen Sie Tag und Monat für den Beginn des Geschäftskalenders aus.  
  
> [!NOTE]  
>  Diese Option ist nur bei Auswahl von **Geschäftskalender** verfügbar.  
  
 **Benennungskonvention für Geschäftskalender**  
 Wählen Sie eine Benennungskonvention für den Geschäftskalender aus. Wählen Sie entweder **Kalenderjahrname** oder **Kalenderjahrname +1**aus.  
  
> [!NOTE]  
>  Diese Option ist nur bei Auswahl von **Geschäftskalender** verfügbar.  
  
 **Berichtskalender (oder Marketingkalender)**  
 Wählen Sie diese Option aus, um eine Zeithierarchie basierend auf einem Berichtskalender zu erstellen.  
  
 **Startwoche und-Monat**  
 Wählen Sie Woche und Monat für den Beginn des Berichtskalenders aus.  
  
> [!NOTE]  
>  Diese Option ist nur bei Auswahl von **Berichtskalender (oder Marketingkalender)** verfügbar.  
  
 **: Woche nach Monat-Muster**  
 Wählen Sie das Muster Woche nach Monat für den Berichtskalender aus.  
  
> [!NOTE]  
>  Diese Option ist nur bei Auswahl von **Berichtskalender (oder Marketingkalender)** verfügbar.  
  
 In der folgenden Tabelle werden die für das Muster Woche nach Monat verfügbaren Optionen aufgeführt.  
  
|value|Description|  
|-----------|-----------------|  
|**Woche 445**|Der erste und zweite Monat im Quartal haben jeweils vier Wochen, während der dritte Monat im Quartal fünf Wochen hat.|  
|**Woche 454**|Der erste und dritte Monat im Quartal haben jeweils vier Wochen, während der zweite Monat im Quartal fünf Wochen hat.|  
|**Woche 544**|Der erste Monat im Quartal hat 5 Wochen, während der zweite und dritte Monat im Quartal jeweils vier Wochen haben.|  
  
 **Produktionskalender**  
 Wählen Sie diese Option aus, um eine Zeithierarchie basierend auf einem Produktionskalender zu erstellen.  
  
 **Startwoche und-Monat**  
 Wählen Sie Woche und Monat für den Beginn des Produktionskalenders aus.  
  
> [!NOTE]  
>  Diese Option ist nur bei Auswahl von **Produktionskalender** verfügbar.  
  
 **Quartal mit zusätzlichen Zeiträumen**  
 Wählen Sie das Quartal mit den zusätzlichen Zeiträumen aus, oder geben Sie ein entsprechendes Quartal ein.  
  
> [!NOTE]  
>  Diese Option ist nur bei Auswahl von **Produktionskalender** verfügbar.  
  
 **ISO 8601-Kalender**  
 Wählen Sie diese Option aus, um eine Hierarchie basierend auf einem ISO 8601-Kalender zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensions-Assistent F1-Hilfe](dimension-wizard-f1-help.md)   
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  