---
title: Outer Join-Operatoren *= und =* werden im Kompatibilitätsmodus 90 oder höher nicht unterstützt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 357c729e6d53cc17f2e4c169dd66613b6cfd2f5d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065263"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Die Operatoren für äußere Joins \*= und =\* werden im Kompatibilitätsmodus 90 oder höher nicht unterstützt
  Der Upgrade Advisor hat die Verwendung von Outer Join \* -Operatoren = und = erkannt \* . Diese Operatoren werden im Kompatibilitätsmodus 90 oder höher nicht unterstützt. Beim Upgrade behalten die Benutzerdatenbanken ihren Kompatibilitätsmodus bei. Anweisungen, die diese Operatoren verwenden, führen zu einem Fehler.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Bevor Sie den Datenbank-Kompatibilitätsmodus auf 90 oder höher ändern, ändern Sie die-Anweisungen, die die Outer Join-Operatoren \* = und = verwenden, \* um äquivalente äußere joinschlüsselwörter Im folgenden Beispiel wird eine Abfrage gezeigt, die den `\*=`-Operator verwendet, sowie eine entsprechende Abfrage, die das `LEFT OUTER JOIN`-Schlüsselwort verwendet.  
  
```  
-- This query uses an old-style outer join operator.  
USE pubs  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee, jobs   
WHERE employee.job_id *= jobs.job_id  
ORDER BY employee.job_id  
  
-- This query uses the ANSI standard keywords LEFT OUTER JOIN.  
USE pubs;  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
ORDER BY employee.job_id  
```  
  
 Weitere Informationen zu äußeren Joins finden Sie unter "Verwenden von äußeren Joins" in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
