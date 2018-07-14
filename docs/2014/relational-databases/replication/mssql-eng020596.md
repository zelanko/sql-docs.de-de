---
title: MSSQL_ENG020596 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a05b9dc595bf27d2912c13792702f680b67a6be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179667"
---
# <a name="mssqleng020596"></a>MSSQL_ENG020596
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20596|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Nur '%s' und Mitglieder der db_owner-Rolle können den anonymen Agent löschen.|  
  
## <a name="explanation"></a>Erklärung  
 Sie besitzen nicht die erforderlichen Berechtigungen, um den Agent für das anonyme Abonnement zu löschen. Der Anmeldename, der zum Aufrufen von [sp_dropanonymousagent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql) verwendet wird, muss Mitglied der festen **sysadmin**-Serverrolle auf dem Verteiler bzw. Mitglied der festen **db_owner**-Datenbankrolle in der Verteilungsdatenbank sein, oder der Benutzer muss derjenige sein, der die erstmalige Ausführung des Agents initialisiert hat.  
  
## <a name="user-action"></a>Benutzeraktion  
 Melden Sie sich mit den entsprechenden Anmeldeinformationen an, und führen Sie **sp_dropanonymousagent**aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
