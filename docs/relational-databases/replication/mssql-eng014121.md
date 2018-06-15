---
title: MSSQL_ENG014121 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014121 error
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 57593511e74a098c4208d154aed044a3032d238f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32958275"
---
# <a name="mssqleng014121"></a>MSSQL_ENG014121
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14121|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der Verteiler '%1!s!' konnte nicht gelöscht werden. Dieser Verteiler besitzt zugeordnete Verteilungsdatenbanken.|  
  
## <a name="explanation"></a>Erklärung  
 Eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, die als Verteiler konfiguriert ist, kann nicht aus der Rolle des Verteilers entfernt werden, da der Instanz Verteilungsdatenbanken zugeordnet sind. Dieser Fehler tritt bei dem Versuch auf, eine Verteilungsdatenbank zu löschen, die einem oder mehreren Verleger(n) zugeordnet ist.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn Sie die Namen der Verleger und Verteilungsdatenbanken ermitteln möchten, die diesem Verteiler zugeordnet sind, führen Sie in einer beliebigen Datenbank auf dem Verteiler [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md) aus.  
  
 Führen Sie [sp_dropdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md) für alle Verteilungsdatenbanken aus, die diesem Verteiler zugeordnet. Nachdem alle Verteilungsdatenbankenzuordnungen entfernt sind, können Sie die Verteilung deaktivieren.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)  
  
  
