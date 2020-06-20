---
title: Doppelpunkt nach reserviertem Schlüsselwort entfernen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fc6882439338509a3c716129d9504f209ab1e555
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065201"
---
# <a name="remove-colon-following-reserved-keyword"></a>Entfernen des Doppelpunkts hinter einem reservierten Schlüsselwort
  Der Upgrade Advisor hat ein Skript erkannt, das einen Doppelpunkt (:) hinter einem reservierten Schlüsselwort enthält. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurde diese Syntax ignoriert, und die Anweisungen wurden erfolgreich ausgeführt. Jetzt führt diese Syntax zum Fehlschlagen der Anweisung, wenn der Datenbank-Kompatibilitätsmodus auf 100 oder höher festgelegt ist.  
  
 Benutzerdatenbanken behalten ihren Kompatibilitätsmodus bei.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Bevor Sie zum Datenbank-Kompatibilitätsmodus 100 oder höher wechseln, ändern Sie die Skripts, indem Sie Doppelpunkte hinter reservierten Schlüsselwörtern entfernen. Weitere Informationen finden Sie unter "sp_dbcmptlevel" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
