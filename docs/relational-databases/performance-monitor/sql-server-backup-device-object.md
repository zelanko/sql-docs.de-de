---
title: SQL Server, Sicherungsmedium-Objekt | Microsoft-Dokumentation
description: Hier lernen Sie das „Sicherungsmedium“-Objekt kennen, das Leistungsindikatoren bereitstellt, mit denen die für Sicherungs- und Wiederherstellungsvorgänge verwendeten Microsoft SQL Server-Sicherungsmedien überwacht werden können.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 383e1cd4ccca7a466817ac5ca226785fa56560ce
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505897"
---
# <a name="sql-server-backup-device-object"></a>SQL Server, Sicherungsmedium-Objekt
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Das **Sicherungsmedium** -Objekt stellt Leistungsindikatoren bereit, die mit denen für Sicherungs- und Wiederherstellungsvorgänge verwendeten Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungsmedien überwacht werden können. Überwachen Sie Sicherungsmedien, wenn Sie den Durchsatz oder den Fortschritt und die Leistung der Sicherungs- und Wiederherstellungsvorgänge auf jedem Medium einzeln bestimmen möchten. Wenn Sie den Durchsatz des gesamten Sicherungs- oder Wiederherstellungsvorgangs der Datenbank überwachen möchten, sollten Sie den Leistungsindikator **Sicherungs-/Wiederherstellungsdurchsatz/Sekunde** des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-Datenbankobjekts** verwenden. Weitere Informationen finden Sie unter [SQL Server, Databases Object](../../relational-databases/performance-monitor/sql-server-databases-object.md).  
  
 In dieser Tabelle wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Leistungsindikator **Sicherungsmedium** beschrieben.  
  
|Sicherungsmedium-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|---------------------------------------|-----------------|  
|**Mediumsdurchsatz Bytes/Sekunde**|Durchsatz von Lese-/Schreibvorgängen für ein Sicherungsmedium. Dieser Leistungsindikator ist nur vorhanden, während der Sicherungs- oder Wiederherstellungsvorgang ausgeführt wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherungsmedien &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
