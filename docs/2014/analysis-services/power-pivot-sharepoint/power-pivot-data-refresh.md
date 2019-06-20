---
title: PowerPivot-Datenaktualisierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4ab42604fabaa188a74858038e35a8b90a105df8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66071220"
---
# <a name="powerpivot-data-refresh"></a>PowerPivot-Datenaktualisierung
  Nachdem Sie eine Arbeitsmappe mit PowerPivot-Daten erstellt haben, können Sie die Daten in regelmäßigen Abständen aktualisieren, indem Sie eine Abfrage oder einen Befehl wiederholt ausführen, um aktualisierte Informationen aus den Quellen abzurufen, die ursprünglich zum Erstellen der Arbeitsmappe verwendet wurden. Dieses Verfahren wird als `data refresh` bezeichnet. Sie können Daten bedarfsgesteuert in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] oder in einem geplanten Vorgang aktualisieren, der als [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Prozess auf einem Anwendungsserver in einer SharePoint-Farm ausgeführt wird. Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [PowerPivot-Datenaktualisierung mit SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [Konfigurieren des unbeaufsichtigten PowerPivot unbeaufsichtigte Datenaktualisierungskonto &#40;PowerPivot für SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [Konfigurieren gespeicherter Anmeldeinformationen für die PowerPivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [Verlauf der Datenaktualisierung Ansicht &#40;PowerPivot für SharePoint&#41;](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und Excel Services von SharePoint Server 2013 verwenden eine andere Architektur für die Datenaktualisierung bei PowerPivot-Datenmodellen. In der von SharePoint 2013 unterstützten Architektur wird Excel Services als Hauptkomponente zum Laden von PowerPivot-Datenmodellen genutzt. In der vorherigen Datenaktualisierungsarchitektur wurden Datenmodelle mithilfe eines Servers geladen, auf dem der PowerPivot-Systemdienst und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus ausgeführt wurden. Weitere Informationen finden Sie unter den folgenden Links:  
> 
>  -   [PowerPivot-Datenaktualisierung mit SharePoint 2013](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Aktualisieren von Arbeitsmappen und planmäßige Datenaktualisierungen &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
