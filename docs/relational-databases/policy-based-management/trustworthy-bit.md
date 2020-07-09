---
title: Bit für die Kennzeichnung der Datenbank als vertrauenswürdig | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7c0fe0b7b8890b3ef9ee2671b4926c8be99cc679
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727293"
---
# <a name="trustworthy-bit"></a>Bit für die Kennzeichnung der Datenbank als vertrauenswürdig
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel ermittelt, ob die dbo-Rolle für eine Datenbank der festen sysadmin-Serverrolle zugewiesen ist und das Bit für die Kennzeichnung der Datenbank als vertrauenswürdig aktiviert ist.  
  
 Werden diese Bedingungen erfüllt, kann ein privilegierter Datenbankbenutzer Berechtigungen auf die sysadmin-Rolle erhöhen. In dieser Rolle kann der Benutzer unsichere Assemblys, die das System beeinträchtigen, erstellen und ausführen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Deaktivieren Sie das Bit zur Kennzeichnung der Datenbank als vertrauenswürdig, oder heben Sie die sysadmin-Berechtigungen für die dbo-Datenbankrolle auf.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
