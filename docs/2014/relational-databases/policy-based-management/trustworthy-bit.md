---
title: Bit für die Kennzeichnung der Datenbank als vertrauenswürdig | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 062a63dd52f4641a0ddfcbc20cb9bad3cce6dc61
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047772"
---
# <a name="trustworthy-bit"></a>Bit für die Kennzeichnung der Datenbank als vertrauenswürdig
  Diese Regel ermittelt, ob die dbo-Rolle für eine Datenbank der festen sysadmin-Serverrolle zugewiesen ist und das Bit für die Kennzeichnung der Datenbank als vertrauenswürdig aktiviert ist.  
  
 Werden diese Bedingungen erfüllt, kann ein privilegierter Datenbankbenutzer Berechtigungen auf die sysadmin-Rolle erhöhen. In dieser Rolle kann der Benutzer unsichere Assemblys, die das System beeinträchtigen, erstellen und ausführen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Deaktivieren Sie das Bit zur Kennzeichnung der Datenbank als vertrauenswürdig, oder heben Sie die sysadmin-Berechtigungen für die dbo-Datenbankrolle auf.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
