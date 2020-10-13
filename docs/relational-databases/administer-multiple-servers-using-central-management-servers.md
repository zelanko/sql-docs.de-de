---
title: Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern
description: Erfahren Sie, wie Sie mehrere Server in SQL Server verwalten, indem Sie zentrale Verwaltungsserver festlegen und Servergruppen erstellen.
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
ms.custom: seo-lt-2019
ms.openlocfilehash: 73f2e9153ebfc204a0f63a6f8aea305815da4e59
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810733"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a>Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]
  Sie können mehrere Server verwalten, indem Sie zentrale Verwaltungsserver festlegen und Servergruppen erstellen.  
  
## <a name="what-is-a-central-management-server-and-server-groups"></a>Erläuterung zum zentralen Verwaltungsserver und zu Servergruppen  
 Eine Instanz von SQL Server, die als zentraler Verwaltungsserver festgelegt wurde, verwaltet die Servergruppen, die die Verbindungsinformationen für Instanzen enthalten. Sie können [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen und Richtlinien der richtlinienbasierten Verwaltung gleichzeitig für Servergruppen ausführen. Sie können auch die Protokolldateien in Instanzen anzeigen, die von einem zentralen Verwaltungsserver verwaltet werden. 
 
 Im Grunde ist ein zentraler Verwaltungsserver ein zentrales Repository, das eine Liste Ihrer verwalteten Server enthält. Versionen, die älter sind als [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] , können nicht als zentraler Verwaltungsserver festgelegt werden.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen können auch für lokale Servergruppen in registrierten Servern ausgeführt werden.  
  
## <a name="create-central-management-server-and-server-groups"></a>Erstellen eines zentralen Verwaltungsservers und einer Servergruppe 
 Um einen zentralen Verwaltungsserver und Servergruppen zu erstellen, verwenden Sie das Fenster **Registrierte Server** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Beachten Sie, dass der zentrale Verwaltungsserver nicht Mitglied einer Gruppe sein kann, die er verwaltet. 
 
 Informationen zum Erstellen von zentralen Verwaltungsservern und Servergruppen finden Sie unter [Erstellen eines zentralen Verwaltungsservers und einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
