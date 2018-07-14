---
title: MSSQL_ENG021286 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ff5775a87c77ee7b0654ab39f7825f7b7bbe4f1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191750"
---
# <a name="mssqleng021286"></a>MSSQL_ENG021286
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21286|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Die %1!s!-Konflikttabelle ist nicht vorhanden.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler wird ausgelöst, wenn es für einen Artikel in [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) keine Konflikttabelle gibt. Der Fehler kann bei dem Versuch auftreten, einer Tabelle, die für die Mergereplikation veröffentlicht wurde, eine Spalte hinzuzufügen oder aber eine Spalte aus der Tabelle zu entfernen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) für die Datenbank mit der fehlenden Konflikttabelle aus, um sich zu vergewissern, dass keine Probleme mit der Datenkonsistenz bestehen.  
  
 Wenn die Konflikttabelle auf einem Abonnenten fehlt, sollten Sie das Abonnement löschen und es dann gänzlich neu erstellen. Fehlt die Konflikttabelle auf einem Verleger, empfiehlt es sich, alle Abonnements und die Veröffentlichung zu löschen und dann die Veröffentlichung und alle Abonnements neu zu erstellen. Weitere Informationen finden Sie unter [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md) und [Abonnieren von Veröffentlichungen](subscribe-to-publications.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
