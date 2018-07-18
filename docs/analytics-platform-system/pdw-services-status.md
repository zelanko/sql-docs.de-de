---
title: PDW-Status - Dienste Analytics Platform System | Microsoft-Dokumentation
description: Parallel Data Warehouse (PDW)-Dienststatus für Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 6892bfcca05e0f85039dddee65a54b485a7ed433
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909890"
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>Parallel Data Warehouse-Dienststatus für Analytics Platform System
Die Parallel Data Warehouse **Dienststatus** Seite in das Microsoft Analytics Platform System Configuration-Manager zeigt den aktuellen Status aller SQL Server-PDW-Dienste und bietet die Möglichkeit, die PDW-Dienste beenden und starten. Dies ist die einzige unterstützte Methode zum Starten und beenden die PDW-Dienste. Beachten Sie, dass einzelne Komponenten oder Dienste unabhängig voneinander nicht gestartet werden können.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>So starten oder Beenden der Anwendung,-Dienste  
  
1.  Um die Anwendung Dienste zu starten, klicken Sie auf **starten Appliance**.  
  
2.  Um die Anwendung Dienste zu beenden, klicken Sie auf **beenden Appliance**.  
  
Es ist nicht erforderlich, klicken Sie auf **übernehmen** beim Starten und beenden die Anwendung Dienste mit **starten Appliance** und **Gerät beenden**.  
  
![DWConfig-Anwendung-PDW-Dienste](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> Beenden die PDW-Region beendet wird, wird damit auch den PDW-Agent (Sqldwagent) auf den Knoten. Der PDW-Agent erfordert der PDW-steuerknoten Überwachung der Integrität melden.  
  
## <a name="see-also"></a>Siehe auch  
[Schalten Sie ein- oder ausschalten die APS-Appliance &#40;Analytics Platform System&#41;](power-the-aps-appliance-on-or-off.md)  
  
