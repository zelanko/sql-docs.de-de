---
title: Ablauf des SQL Server-Anmeldekennworts | Microsoft-Dokumentation
description: Überprüfen Sie, ob das Ablaufen von Kennwörtern für einzelne SQL Server-Anmeldungen aktiviert ist, um vor möglichen Angriffen in SQL Server vorzugehen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 50f33195e18af58e782c03118a7e3176f1340cd1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774160"
---
# <a name="sql-server-login-password-expiration"></a>Ablauf des SQL Server-Anmeldekennworts
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel überprüft, ob der Ablauf des Kennworts für jede [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung aktiviert ist. Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung aktiviert ist und die Betriebssystemversion älter ist als [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], könnte ein Angreifer ein bekanntes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldekennwort wiederholt nutzen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Es wird empfohlen, das Betriebssystem auf [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]zu aktualisieren.  
  
 Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung in Ihrer Umgebung nicht erforderlich ist, verwenden Sie die Windows-Authentifizierung. Weitere Informationen finden Sie unter [Auswählen eines Authentifizierungsmodus](../../relational-databases/security/choose-an-authentication-mode.md).  
  
 Aktivieren Sie den Ablauf des Kennworts für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldungen. Verwenden Sie [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) , um die Kennwortrichtlinie für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung zu konfigurieren.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
