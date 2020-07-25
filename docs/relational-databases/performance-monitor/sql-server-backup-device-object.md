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
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 116a4cc015e74fd737c5e9fb9d5f1f920abaf377
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458843"
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
  
  
