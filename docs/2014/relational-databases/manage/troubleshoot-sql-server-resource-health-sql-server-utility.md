---
title: Fehlerbehebung für die SQL Server-Ressourcenintegrität (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a37e1a0bcf0232b2e29520adde986b32542f7539
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48186340"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Fehlerbehebung für die SQL Server-Ressourcenintegrität (SQL Server-Hilfsprogramm)
  Die Fehlerbehebung von Problemen mit der Ressourcenintegrität, die von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -UCP identifiziert wurden, schließt möglicherweise die Abhilfe für eine überbeanspruchte CPU auf einem Computer oder einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ein, oder die Abhilfe für eine überbeanspruchte CPU für eine Datenebenenanwendung. Bei anderen Problemen muss möglicherweise eine Abhilfe für überausgelasteten Dateispeicherplatz für Datenbankdateien oder die Überauslastung des zugewiesenen Speicherplatzes auf einem Speichervolume gefunden werden.  
  
 Wenn eine Datenbank den Status "Notfall" aufweist, wird für den Integritätsstatus ein überausgelasteter Protokolldateispeicherplatz angezeigt.  
  
 Weitere Informationen zu fehlgeschlagenen Datensammlungen, die zu grauen Statussymbolen auf der verwalteten Instanzlistenansicht auf einem UCP führen, finden Sie unter [Problembehandlung beim SQL Server-Hilfsprogramm](../../database-engine/troubleshoot-the-sql-server-utility.md). Weitere Informationen zu ersten Schritten mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm finden Sie unter [Funktionen und Tasks im SQL Server-Hilfsprogramm](sql-server-utility-features-and-tasks.md).  
  
 Weitere Informationen zur Abhilfe für bestimmte Ressourcenintegritätsprobleme, die von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -UCP identifiziert wurden, finden Sie in den folgenden Themen:  
  
-   [So identifizieren Sie die SQL Server-Version und -Edition](http://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Beheben von Leistungsproblemen in SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
