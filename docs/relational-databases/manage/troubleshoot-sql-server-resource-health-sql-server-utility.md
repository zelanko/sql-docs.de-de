---
title: Fehlerbehebung für die SQL Server-Ressourcenintegrität (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Problembehandlung bei Ressourcenintegritätsproblemen, die ein SQL Server-UCP identifiziert, z. B. überbeanspruchte CPUs, Dateispeicherplatz oder der zugewiesene Datenträgerspeicher.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c6c6d499d485941d490848b68b5c8142edd0cb4b
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810683"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Fehlerbehebung für die SQL Server-Ressourcenintegrität (SQL Server-Hilfsprogramm)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Die Fehlerbehebung von Problemen mit der Ressourcenintegrität, die von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -UCP identifiziert wurden, schließt möglicherweise die Abhilfe für eine überbeanspruchte CPU auf einem Computer oder einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ein, oder die Abhilfe für eine überbeanspruchte CPU für eine Datenebenenanwendung. Bei anderen Problemen muss möglicherweise eine Abhilfe für überausgelasteten Dateispeicherplatz für Datenbankdateien oder die Überauslastung des zugewiesenen Speicherplatzes auf einem Speichervolume gefunden werden.  
  
 Wenn eine Datenbank den Status „emergency“ (Notfall) aufweist, wird für den Integritätsstatus der überausgelastete Protokolldateispeicherplatz angezeigt.  
  
 Weitere Informationen zu fehlgeschlagenen Datensammlungen, die zu grauen Statussymbolen auf der verwalteten Instanzlistenansicht auf einem UCP führen, finden Sie unter [Problembehandlung beim SQL Server-Hilfsprogramm](/previous-versions/sql/sql-server-2016/ee210592(v=sql.130)). Weitere Informationen zu ersten Schritten mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm finden Sie unter [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Weitere Informationen zur Abhilfe für bestimmte Ressourcenintegritätsprobleme, die von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -UCP identifiziert wurden, finden Sie in den folgenden Themen:  
  
-   [So identifizieren Sie die SQL Server-Version und -Edition](https://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Behandlung von Leistungsproblemen in SQL Server 2008](/previous-versions/sql/sql-server-2008/dd672789(v=sql.100))  
  
