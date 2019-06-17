---
title: MSSQL_ENG014121 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014121 error
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 996b93f04d9e9fc063bbacbb5f4a7588794ad208
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63191520"
---
# <a name="mssqleng014121"></a>MSSQL_ENG014121
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14121|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der Verteiler '%1!s!' konnte nicht gelöscht werden. Dieser Verteiler besitzt zugeordnete Verteilungsdatenbanken.|  
  
## <a name="explanation"></a>Erklärung  
 Eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, die als Verteiler konfiguriert ist, kann nicht aus der Rolle des Verteilers entfernt werden, da der Instanz Verteilungsdatenbanken zugeordnet sind. Dieser Fehler tritt bei dem Versuch auf, eine Verteilungsdatenbank zu löschen, die einem oder mehreren Verleger(n) zugeordnet ist.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn Sie die Namen der Verleger und Verteilungsdatenbanken ermitteln möchten, die diesem Verteiler zugeordnet sind, führen Sie in einer beliebigen Datenbank auf dem Verteiler [sp_helpdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql) aus.  
  
 Führen Sie [sp_dropdistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) für alle Verteilungsdatenbanken aus, die diesem Verteiler zugeordnet. Nachdem alle Verteilungsdatenbankenzuordnungen entfernt sind, können Sie die Verteilung deaktivieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)   
 [Verteilung konfigurieren](configure-distribution.md)  
  
  
