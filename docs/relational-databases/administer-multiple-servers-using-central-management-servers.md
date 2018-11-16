---
title: Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern | Microsoft-Dokumentation
ms.date: 08/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 67f4b59fc0159a3e93c892defac6f2f44385807b
ms.sourcegitcommit: ddb682c0061c2a040970ea88c051859330b8ac00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51571049"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a>Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Sie können mehrere Server verwalten, indem Sie zentrale Verwaltungsserver festlegen und Servergruppen erstellen.  
  
## <a name="what-is-a-central-management-server-and-server-groups"></a>Erläuterung zum zentralen Verwaltungsserver und zu Servergruppen  
 Eine Instanz von SQL Server, die als zentraler Verwaltungsserver festgelegt wurde, verwaltet die Servergruppen, die die Verbindungsinformationen für Instanzen enthalten. Sie können [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen und Richtlinien der richtlinienbasierten Verwaltung gleichzeitig für Servergruppen ausführen. Sie können auch die Protokolldateien in Instanzen anzeigen, die von einem zentralen Verwaltungsserver verwaltet werden. 
 
 Im Grunde ist ein zentraler Verwaltungsserver ein zentrales Repository, das eine Liste Ihrer verwalteten Server enthält. Versionen, die älter sind als [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] , können nicht als zentraler Verwaltungsserver festgelegt werden.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen können auch für lokale Servergruppen in registrierten Servern ausgeführt werden.  
  
## <a name="create-central-management-server-and-server-groups"></a>Erstellen eines zentralen Verwaltungsservers und einer Servergruppe 
 Um einen zentralen Verwaltungsserver und Servergruppen zu erstellen, verwenden Sie das Fenster **Registrierte Server** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Beachten Sie, dass der zentrale Verwaltungsserver nicht Mitglied einer Gruppe sein kann, die er verwaltet. 
 
 Informationen zum Erstellen von zentralen Verwaltungsservern und Servergruppen finden Sie unter [Erstellen eines zentralen Verwaltungsservers und einer Servergruppe &#40;SQL Server Management Studio&#41;](../tools/sql-server-management-studio/create-a-central-management-server-and-server-group.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
