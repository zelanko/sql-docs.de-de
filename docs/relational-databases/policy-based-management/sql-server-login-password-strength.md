---
description: Sicherheit des SQL Server-Anmeldekennworts
title: Sicherheit des SQL Server-Anmeldekennworts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: cf90a1541ed047ce17b405dfc5727ed41a0b7d1b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465263"
---
# <a name="sql-server-login-password-strength"></a>Sicherheit des SQL Server-Anmeldekennworts
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel überprüft, ob Kennwortrichtlinie erzwingen für jede [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung aktiviert ist. Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung aktiviert ist und die Betriebssystemversion älter ist als [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], könnte ein Angreifer ein bekanntes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldekennwort wiederholt nutzen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Es wird empfohlen, das Betriebssystem auf [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]zu aktualisieren.  
  
 Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung in Ihrer Umgebung nicht erforderlich ist, verwenden Sie die Windows-Authentifizierung.  
  
 Aktivieren Sie Kennwortrichtlinie erzwingen für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldungen. Verwenden Sie [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) , um die Kennwortrichtlinie für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung zu konfigurieren.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
