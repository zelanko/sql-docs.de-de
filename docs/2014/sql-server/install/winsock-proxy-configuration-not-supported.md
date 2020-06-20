---
title: Winsock-Proxy Konfiguration wird nicht unterstützt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Winsock proxy configuration [SQL Server]
ms.assetid: abf71f7b-8bd7-49d2-92f7-9ddf72924d8c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 359399852224923d0512372d13058535fdca3c7c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065060"
---
# <a name="winsock-proxy-configuration-not-supported"></a>Winsockproxykonfiguration nicht unterstützt
  Der Winsock-Proxy kann nicht mithilfe von Tools konfiguriert werden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tools können keine Windows-Komponenten konfigurieren.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie Microsoft Internet Security and Acceleration (ISA) Server, um einen Computer zu veröffentlichen. Weitere Informationen zum Konfigurieren von Winsockproxy finden Sie in Ihrer Proxyserverdokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
