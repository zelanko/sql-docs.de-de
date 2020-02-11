---
title: Anforderungen an das Dienst Konto für das Upgrade auf SQL Server 2008 auf einem Domänen Controller | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
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
ms.openlocfilehash: bb703e42edcbf128ff78ca294e08fc487f06d8f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66092258"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>Dienstkontoanforderungen für das Upgrade auf SQL Server 2008 auf einem Domänencontroller
  Der Upgrade Advisor hat eine Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von erkannt, die unter einem Netzwerkdienst Konto oder einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] lokalen Dienst Konto auf einem Domänen Controller ausgeführt wird. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]-Domänencontroller installiert ist, können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste nicht unter Privilegien eines lokalen Dienstkontos oder eines Netzwerkdienstkontos ausgeführt werden.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Stellen Sie sicher, dass alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonten entweder Domänenkonten oder lokalen Systemkonten zugewiesen werden. Wird diese Änderung vor dem Upgrade nicht vorgenommen, kann Setup nicht durchgeführt werden. Die Dienstkonten "SQL Writer", "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]" und "Hilfsdienst für Active Directory" bilden eine Ausnahme, da sie für das Netzwerkdienstkonto hartcodiert sind und nicht geändert werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
