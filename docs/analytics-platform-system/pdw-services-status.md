---
title: PDW-Dienststatus
description: Status der parallel Data Warehouse (PDW)-Dienste für Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 2789c8b74420a56a32d08a0339d4ee6d3cc112d1
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400855"
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>Status der parallelen Data Warehouse Dienste für Analytics Platform System
Die Seite paralleler Data Warehouse **Services-Status** im Microsoft Analytics Platform System Configuration Manager zeigt den aktuellen Status aller SQL Server PDW Dienste an und bietet die Möglichkeit, die PDW-Dienste zu starten und zu starten. Dies ist die einzige unterstützte Methode, um die PDW-Dienste zu starten und zu beenden. Beachten Sie, dass einzelne Komponenten oder Dienste nicht unabhängig gestartet werden können.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>So starten oder verhindern Sie die Geräte Dienste  
  
1.  Um die Geräte Dienste zu starten, klicken Sie auf **Appliance starten**.  
  
2.  Um die Geräte Dienste anzuhalten, klicken Sie auf **Appliance Abbrechen**.  
  
Wenn Sie die Geräte Dienste starten und beenden, müssen Sie nicht auf **anwenden** klicken, um die Geräte Dienste zu **starten** und zu **Beenden**.  
  
![DWConfig-Anwendung, PDW-Dienste](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> Durch das Beenden der PDW-Region wird auch der PDW-Agent (sqldwagent) auf den Knoten beendet. Der PDW-Agent erfordert, dass der PDW-Steuerungs Knoten die Integritäts Überwachung meldet.  
  
## <a name="see-also"></a>Weitere Informationen  
[Schalten Sie das APS-Gerät &#40;Analytics-Platt Form System ein oder aus&#41;](power-the-aps-appliance-on-or-off.md)  
  
