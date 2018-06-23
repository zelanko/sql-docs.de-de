---
title: PowerPivot-Datenaktualisierung | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ec63b777759c8fbfb9cb66e70d3d96a129402e15
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150898"
---
# <a name="powerpivot-data-refresh"></a>PowerPivot-Datenaktualisierung
  Nachdem Sie eine Arbeitsmappe mit PowerPivot-Daten erstellt haben, können Sie die Daten in regelmäßigen Abständen aktualisieren, indem Sie eine Abfrage oder einen Befehl wiederholt ausführen, um aktualisierte Informationen aus den Quellen abzurufen, die ursprünglich zum Erstellen der Arbeitsmappe verwendet wurden. Dieses Verfahren wird als `data refresh` bezeichnet. Sie können Daten bedarfsgesteuert in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] oder in einem geplanten Vorgang aktualisieren, der als [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Prozess auf einem Anwendungsserver in einer SharePoint-Farm ausgeführt wird. Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [PowerPivot-Datenaktualisierung mit SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [Konfigurieren des unbeaufsichtigten PowerPivot unbeaufsichtigte Datenaktualisierungskonto &#40;PowerPivot für SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [Konfigurieren von gespeicherten Anmeldeinformationen für die PowerPivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [Ansicht Datenaktualisierungsverlauf &#40;PowerPivot für SharePoint&#41;](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und Excel Services von SharePoint Server 2013 verwenden eine andere Architektur für die Datenaktualisierung bei PowerPivot-Datenmodellen. In der von SharePoint 2013 unterstützten Architektur wird Excel Services als Hauptkomponente zum Laden von PowerPivot-Datenmodellen genutzt. In der vorherigen Datenaktualisierungsarchitektur wurden Datenmodelle mithilfe eines Servers geladen, auf dem der PowerPivot-Systemdienst und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus ausgeführt wurden. Weitere Informationen finden Sie unter den folgenden Links:  
>   
>  -   [PowerPivot-Datenaktualisierung mit SharePoint 2013](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Aktualisieren von Arbeitsmappen und geplanter Datenaktualisierung &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  