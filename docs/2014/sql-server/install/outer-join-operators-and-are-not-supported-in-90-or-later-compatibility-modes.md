---
title: Operatoren für äußere Joins *= und =* werden im Kompatibilitätsmodus 90 oder höher nicht unterstützt | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 62a6f9e016abf24f28660b04e7a6242fdd6606ce
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66093687"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Die Operatoren für äußere Joins \*= und =\* werden im Kompatibilitätsmodus 90 oder höher nicht unterstützt
  Der Upgrade Advisor hat festgestellt, dass Operatoren für äußere Joins \*= und =\*. Diese Operatoren werden im Kompatibilitätsmodus 90 oder höher nicht unterstützt. Beim Upgrade behalten die Benutzerdatenbanken ihren Kompatibilitätsmodus bei. Anweisungen, die diese Operatoren verwenden, führen zu einem Fehler.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Bevor Sie die Datenbank-Kompatibilitätsmodus auf 90 oder höher ändern, ändern Sie Anweisungen, Operatoren für äußere Joins verwenden \*= und =\* entsprechende OUTER JOIN-Schlüsselwörter verwenden. Im folgenden Beispiel wird eine Abfrage gezeigt, die den `\*=`-Operator verwendet, sowie eine entsprechende Abfrage, die das `LEFT OUTER JOIN`-Schlüsselwort verwendet.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
