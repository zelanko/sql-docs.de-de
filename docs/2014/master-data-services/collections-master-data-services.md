---
title: Auflistungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services]
- collections [Master Data Services], about collections
ms.assetid: 5aa1d1e0-b4e5-4897-8e74-01dcf418df73
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0dbf84d6fd3253a3b4d945693090fdad00d077ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65483545"
---
# <a name="collections-master-data-services"></a>Auflistungen (Master Data Services)
  Eine Auflistung ist eine Gruppe von Blatt- und konsolidierten Elementen einer einzelnen Entität. Verwenden Sie Auflistungen, wenn Sie keine vollständige Hierarchie benötigen und unterschiedliche Gruppierungen der Elemente zu Berichts- oder Analysezwecken anzeigen möchten oder wenn Sie eine Taxonomie erstellen möchten.  
  
## <a name="what-collections-contain"></a>Inhalte von Auflistungen  
 Es gibt bei Auflistungen keine Beschränkung hinsichtlich der Anzahl oder des Typs der Elemente, die eingebunden werden können, solange sich die Elemente in derselben Entität befinden. Eine Auflistung kann konsolidierte Elemente und Blattelemente aus mehreren verbindlichen bzw. nicht verbindlichen expliziten Hierarchien enthalten.  
  
 Wenn Sie eine Auflistung erstellen, erstellen Sie keine hierarchische Struktur; Sie erstellen eine flache Liste von Elementen. Wenn Sie einen Knoten aus einer Hierarchie auswählen und ihn der Auflistung hinzufügen, ist das konsolidierte Element, das Sie ausgewählt haben, das einzige der Auflistung hinzugefügte Element.  
  
 Außerdem kann eine Auflistung weitere Auflistungen enthalten. Zum Erstellen von Taxonomien können Sie Auflistungen verwenden, die wiederum aus Auflistungen bestehen.  
  
 Wenn Sie eine Auflistung erstellen, sind Sie automatisch als Besitzer aufgeführt. Wenn Sie Administrator sind, können Sie nach Bedarf andere Attribute für die Auflistung erstellen.  
  
> [!NOTE]  
>  Bevor Sie eine Auflistung erstellen können, muss die Entität für explizite Hierarchien aktiviert werden. Weitere Informationen finden Sie unter [Aktivieren einer Entität für explizite Hierarchien und Auflistungen &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).  
  
## <a name="subscription-views-for-collections"></a>Abonnementsichten für Auflistungen  
 Es gibt zwei Typen von Abonnementsichten, die Auflistungen anzeigen. Das Format **Sammlungsattribute** zeigt eine Liste von Sammlungen und allen zu den jeweiligen Sammlungen gehörenden Attributen an (z.B. Beschreibung oder Besitzer). Das **Sammlungen** -Format zeigt alle Elemente in allen Auflistungen sowie jede Elementgewichtung und Sortierreihenfolge an. Weitere Informationen finden Sie unter [Exportieren von Daten &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md).  
  
 Wenn Sie Gewichtungswerte für bestimmte Elemente in einer Auflistung festlegten, sind diese Werte in verwandten Abonnementsichten verfügbar.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Aktivieren Sie eine Entität für explizite Hierarchien und Auflistungen.|[Aktivieren einer Entität für explizite Hierarchien und Auflistungen &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|Erstellen Sie eine neue Sammlung.|[Erstellen einer Sammlung &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-collection-master-data-services.md)|  
|Fügen Sie Elemente einer vorhandenen Auflistung hinzu.|[Hinzufügen von Elementen zu einer Sammlung &#40;Master Data Services&#41;](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Exportieren von Daten &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)  
  
  
