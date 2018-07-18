---
title: Fehlerbehebung für die SQL Server-Ressourcenintegrität (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5157d55bedf199d907247c1c13e3b4a11de01061
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32942375"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Fehlerbehebung für die SQL Server-Ressourcenintegrität (SQL Server-Hilfsprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Fehlerbehebung von Problemen mit der Ressourcenintegrität, die von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -UCP identifiziert wurden, schließt möglicherweise die Abhilfe für eine überbeanspruchte CPU auf einem Computer oder einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ein, oder die Abhilfe für eine überbeanspruchte CPU für eine Datenebenenanwendung. Bei anderen Problemen muss möglicherweise eine Abhilfe für überausgelasteten Dateispeicherplatz für Datenbankdateien oder die Überauslastung des zugewiesenen Speicherplatzes auf einem Speichervolume gefunden werden.  
  
 Wenn eine Datenbank den Status "Notfall" aufweist, wird für den Integritätsstatus ein überausgelasteter Protokolldateispeicherplatz angezeigt.  
  
 Weitere Informationen zu fehlgeschlagenen Datensammlungen, die zu grauen Statussymbolen auf der verwalteten Instanzlistenansicht auf einem UCP führen, finden Sie unter [Problembehandlung beim SQL Server-Hilfsprogramm](http://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453). Weitere Informationen zu ersten Schritten mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm finden Sie unter [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Weitere Informationen zur Abhilfe für bestimmte Ressourcenintegritätsprobleme, die von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -UCP identifiziert wurden, finden Sie in den folgenden Themen:  
  
-   [So identifizieren Sie die SQL Server-Version und -Edition](http://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Beheben von Leistungsproblemen in SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
