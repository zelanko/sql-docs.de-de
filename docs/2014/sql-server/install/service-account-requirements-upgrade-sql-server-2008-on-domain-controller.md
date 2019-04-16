---
title: Kontoanforderungen für das Upgrade auf SQL Server 2008 auf einem Domänencontroller-Service | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dc00c4195b54101c24bc05218e4ea7c3abac53e8
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582673"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>Dienstkontoanforderungen für das Upgrade auf SQL Server 2008 auf einem Domänencontroller
  Upgrade Advisor hat erkannt, eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter einem Konto Netzwerkdienst oder lokaler Dienst unter einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] Domänencontroller. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]-Domänencontroller installiert ist, können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste nicht unter Privilegien eines lokalen Dienstkontos oder eines Netzwerkdienstkontos ausgeführt werden.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Stellen Sie sicher, dass alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonten entweder Domänenkonten oder lokalen Systemkonten zugewiesen werden. Wird diese Änderung vor dem Upgrade nicht vorgenommen, kann Setup nicht durchgeführt werden. Die Dienstkonten "SQL Writer", "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]" und "Hilfsdienst für Active Directory" bilden eine Ausnahme, da sie für das Netzwerkdienstkonto hartcodiert sind und nicht geändert werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
