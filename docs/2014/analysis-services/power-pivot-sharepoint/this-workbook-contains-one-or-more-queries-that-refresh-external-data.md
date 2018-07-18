---
title: Diese Arbeitsmappe enthält eine oder mehrere Abfragen, die externe Daten aktualisieren. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 29190b58267181a028b2a4f13343f0e8400effb3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295660"
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>Diese Arbeitsmappe enthält eine oder mehrere Abfragen, die externe Daten aktualisieren.
  Für Excel-Arbeitsmappen, die PowerPivot-Daten enthalten, zeigt Excel Services diese Warnung an, wenn Verbindungsinformationen erkannt werden, und fordert Sie auf, Abfragen für diese Arbeitsmappe zu aktivieren oder deaktivieren.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|PowerPivot für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Excel Services ist so konfiguriert, dass bei Datenaktualisierungen Warnungen ausgegeben werden.|  
|Meldungstext|Diese Arbeitsmappe enthält eine oder mehrere Abfragen, die externe Daten aktualisieren. Ein böswilliger Benutzer kann eine Abfrage entwerfen, um auf vertrauliche Informationen zuzugreifen und sie an andere Benutzer zu verteilen oder andere schädliche Aktionen auszuführen.<br /><br /> Wenn Sie der Quelle dieser Arbeitsmappe vertrauen, klicken Sie auf Ja, um Abfragen für externe Daten in dieser Arbeitsmappe zu aktivieren. Wenn Sie sich nicht sicher sind, klicken Sie auf Nein, damit Änderungen nicht für die Arbeitsmappe übernommen werden.<br /><br /> Möchten Sie Abfragen für externe Daten in dieser Arbeitsmappe aktivieren?|  
  
## <a name="explanation"></a>Erklärung  
 PowerPivot-Arbeitsmappen enthalten eingebettete Datenverbindungszeichenfolgen, die von Excel verwendet werden, um mit einem externen PowerPivot-Server zu kommunizieren, der die Daten lädt und berechnet. Wenn Warnungen bei Datenaktualisierungen aktiviert sind, erkennt Excel Services diese Verbindungszeichenfolge und warnt den Benutzer entsprechend.  
  
 Abfragen müssen aktiviert sein, um PowerPivot-Daten in der Arbeitsmappe zu filtern und sie in Slicer aufzuteilen. Stellen Sie sicher, dass Sie Abfragen nur für jene PowerPivot-Arbeitsmappen aktivieren, denen Sie vertrauen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Klicken Sie auf **Ja** , um Abfragen zu aktivieren.  
  
 Sie können auch die Konfigurationseinstellungen ändern, damit keine Warnungen bei Aktualisierungen mehr angezeigt werden:  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie auf **Excel Services-Anwendung**.  
  
3.  Klicken Sie auf **Vertrauenswürdiger Dateispeicherort**.  
  
4.  Klicken Sie auf **http://** oder den Speicherort, den Sie konfigurieren möchten.  
  
5.  Deaktivieren Sie in „Externe Daten“ das Kontrollkästchen **Beim Aktualisieren warnen**.  
  
6.  Klicken Sie auf **OK**.  
  
 Alternativ können Sie einen neuen vertrauenswürdigen Speicherort für Websites erstellen, die PowerPivot-Arbeitsmappen enthalten, und dann die Konfigurationseinstellungen nur für diese Website ändern. Weitere Informationen finden Sie unter [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
