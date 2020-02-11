---
title: FOR Browse ist in Sichten im Kompatibilitätsmodus 90 oder höher nicht zulässig. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4811a3df80257b1e2d0e903fad562568eeec4ea2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66095178"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a>FOR BROWSE ist in Sichten im Kompatibilitätsmodus 90 oder höher nicht zulässig
  Upgrade Advisor hat die Verwendung der FOR BROWSE-Klausel in einer Sicht erkannt. Die FOR BROWSE-Klausel ist in Sichten zulässig (und wird ignoriert), wenn der Datenbank-Kompatibilitätsmodus auf 80 festgelegt ist. Die FOR BROWSE-Klausel ist nicht in Sichten zulässig, wenn der Datenbank-Kompatibilitätsmodus auf 90 oder höher festgelegt ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Beim Upgrade behalten die Benutzerdatenbanken ihren Kompatibilitätsmodus bei. Bevor Sie den Datenbank-Kompatibilitätsmodus in 90 oder höher ändern, entfernen Sie die FOR BROWSE-Klausel aus den Sichtdefinitionen. Weitere Informationen finden Sie unter "sp_dbcmptlevel" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
