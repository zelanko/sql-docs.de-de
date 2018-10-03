---
title: Bit für die Kennzeichnung der Datenbank als vertrauenswürdig | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 524c1c330288579649fd7744366cf8f3866fe8a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072110"
---
# <a name="trustworthy-bit"></a>Bit für die Kennzeichnung der Datenbank als vertrauenswürdig
  Diese Regel ermittelt, ob die dbo-Rolle für eine Datenbank der festen sysadmin-Serverrolle zugewiesen ist und das Bit für die Kennzeichnung der Datenbank als vertrauenswürdig aktiviert ist.  
  
 Werden diese Bedingungen erfüllt, kann ein privilegierter Datenbankbenutzer Berechtigungen auf die sysadmin-Rolle erhöhen. In dieser Rolle kann der Benutzer unsichere Assemblys, die das System beeinträchtigen, erstellen und ausführen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Deaktivieren Sie das Bit zur Kennzeichnung der Datenbank als vertrauenswürdig, oder heben Sie die sysadmin-Berechtigungen für die dbo-Datenbankrolle auf.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
