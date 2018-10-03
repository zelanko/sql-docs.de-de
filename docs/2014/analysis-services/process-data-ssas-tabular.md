---
title: Verarbeiten von Daten (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c3f47ddcfab5df43104d3998822fdaf8bd504946
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048430"
---
# <a name="process-data-ssas-tabular"></a>Verarbeiten von Daten (SSAS – tabellarisch)
  Wenn Sie Daten im Modus mit Zwischenspeicherung in ein Tabellenmodell importieren, zeichnen Sie eine Momentaufnahme der Daten zum Zeitpunkt des Imports auf. In einigen Fällen ändern sich diese Daten möglicherweise nie und müssen im Modell nicht aktualisiert werden. Es ist jedoch wahrscheinlicher, dass sich die Daten, aus denen Daten importiert werden, regelmäßig ändern. Damit das Modell jedoch immer die neuesten Daten aus den Datenquellen widerspiegelt, ist es erforderlich, die Daten zu verarbeiten (zu aktualisieren) und berechnete Daten neu zu berechnen. Um die Daten im Modell zu aktualisieren, führen Sie eine Verarbeitungsaktion für alle Tabellen, eine einzelne Tabelle, eine Partition oder eine Datenquellenverbindung aus.  
  
 Beim Erstellen des Modellprojekts müssen alle Verarbeitungsaktionen manuell in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]initiiert werden. Nachdem ein Modell bereitgestellt wurde, können Verarbeitungsvorgänge mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ausgeführt oder mit einem Skript geplant werden. Die hier beschriebenen Tasks beziehen sich auf Verarbeitungsaktionen, die Sie während der Modellerstellung in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ausführen können. Weitere Informationen zu Verarbeitungsaktionen für ein bereitgestelltes Modell finden Sie unter [Verarbeiten von Datenbank, Tabelle oder Partition](tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Thema|Description|  
|-----------|-----------------|  
|[Manuelles verarbeiten Daten &#40;SSAS – tabellarisch&#41;](manually-process-data-ssas-tabular.md)|Beschreibt, wie Arbeitsbereichsdaten eines Modells manuell verarbeitet werden.|  
|[Problembehandlung von Verarbeitungsdaten &#40;SSAS – tabellarisch&#41;](troubleshoot-process-data-ssas-tabular.md)|Beschreibt die Problembehandlung für Verarbeitungsvorgänge.|  
  
  
