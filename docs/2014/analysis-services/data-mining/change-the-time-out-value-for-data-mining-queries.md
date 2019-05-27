---
title: Ändern des Timeoutwerts für Datamining-Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time-out
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 640d07115e2a071bb5d57e87955c11670f4c38b0
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66085892"
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a>Ändern des Timeoutwerts für Data Mining-Abfragen
  Wenn Sie ein Prognosegütediagramm erstellen oder eine Vorhersageabfrage ausführen, kann es viel Zeit in Anspruch nehmen, alle für die Vorhersage erforderlichen Daten zu generieren. Um ein Timeout der Abfrage zu verhindern, können Sie den Wert ändern, der festlegt, wie lange der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server auf den Abschluss einer Abfrage wartet.  
  
 Der Standardwert ist 15. Wenn Ihre Modelle komplex sind oder die Datenquelle umfangreich ist, reicht dies unter Umständen nicht aus. Bei Bedarf können Sie den Wert heraufsetzen, um genügend Zeit für die Verarbeitung bereitzustellen. Beispiel: wenn Sie **Abfragetimeout** auf 600 setzen, kann die Abfrage bis zu 10 Minuten lang ausgeführt werden.  
  
 Weitere Informationen zu Vorhersageabfragen finden Sie unter [Data Mining-Abfragetasks und Anweisungen](data-mining-query-tasks-and-how-tos.md).  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a>Konfigurieren des Timeoutwerts für Data Mining-Abfragen  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Bereich **Optionen** **Business Intelligence-Designer**.  
  
3.  Klicken Sie auf das Textfeld **Abfragetimeout** , und geben Sie einen Wert für die Anzahl der Sekunden ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Abfragetasks und Anweisungen](data-mining-query-tasks-and-how-tos.md)   
 [Data Mining-Abfragen](data-mining-queries.md)  
  
  
