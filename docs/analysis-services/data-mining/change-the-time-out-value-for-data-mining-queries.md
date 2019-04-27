---
title: Ändern des Timeoutwerts für Datamining-Abfragen | Microsoft-Dokumentation
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c67744ea3862185b59d1a0af3e1bb144eba57e23
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62670992"
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a>Ändern des Timeoutwerts für Data Mining-Abfragen
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Wenn Sie ein Prognosegütediagramm erstellen oder eine Vorhersageabfrage ausführen, kann es viel Zeit in Anspruch nehmen, alle für die Vorhersage erforderlichen Daten zu generieren. Um ein Timeout der Abfrage zu verhindern, können Sie den Wert ändern, der festlegt, wie lange der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server auf den Abschluss einer Abfrage wartet.  
  
 Der Standardwert ist 15. Wenn Ihre Modelle komplex sind oder die Datenquelle umfangreich ist, reicht dies unter Umständen nicht aus. Bei Bedarf können Sie den Wert heraufsetzen, um genügend Zeit für die Verarbeitung bereitzustellen. Beispiel: wenn Sie **Abfragetimeout** auf 600 setzen, kann die Abfrage bis zu 10 Minuten lang ausgeführt werden.  
  
 Weitere Informationen zu Vorhersageabfragen finden Sie unter [Data Mining-Abfragetasks und Anweisungen](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md).  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a>Konfigurieren des Timeoutwerts für Data Mining-Abfragen  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Bereich **Optionen** **Business Intelligence-Designer**.  
  
3.  Klicken Sie auf das Textfeld **Abfragetimeout** , und geben Sie einen Wert für die Anzahl der Sekunden ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Abfragetasks und Anweisungen](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [Data Mining-Abfragen](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
