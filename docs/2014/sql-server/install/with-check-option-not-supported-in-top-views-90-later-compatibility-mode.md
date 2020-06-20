---
title: WITH Check Option wird in Sichten, die Top in 90 oder höheren Kompatibilitäts Modi enthalten, nicht unterstützt. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee7775c875e33f104341a1da39f5fe6c9326f284
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011776"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a>WITH CHECK OPTION wird nicht in Sichten unterstützt, die die TOP-Klausel im Kompatibilitätsmodus 90 oder höher enthalten
  Der Upgrade Advisor hat eine Sicht erkannt, die WITH CHECK OPTION und eine TOP-Klausel in der SELECT-Anweisung der Sicht oder in einer Sicht verwendet, auf die verwiesen wird. Sichten, die auf diese Weise definiert werden, lassen es fälschlicherweise zu, dass Daten über die Sicht geändert werden, und können zu ungenauen Ergebnissen führen, wenn der Datenbank-Kompatibilitätsmodus auf 80 oder höher festgelegt ist. Daten können nicht über eine Sicht eingegeben oder aktualisiert werden, die WITH CHECK OPTION verwendet, wenn die Sicht oder eine Sicht, auf die verwiesen wird, die TOP-Klausel verwendet und der Datenbank-Kompatibilitätsmodus auf 90 oder höher festgelegt ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Beim Upgrade behalten die Benutzerdatenbanken ihren Kompatibilitätsmodus bei. Bevor Sie den Datenbank-Kompatibilitätsmodus in 100 oder höher ändern, ändern Sie Sichten, die sowohl die WITH CHECK OPTION als auch die TOP-Klausel verwenden, wenn die Datenänderung über die Sicht erforderlich ist. Weitere Informationen finden Sie unter [sp_dbcmptlevel &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
