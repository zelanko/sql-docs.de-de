---
title: Geschachtelter AFTER-Trigger ausgelöst wird, auch wenn triggerschachtelung OFF ist | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 826961aef9133c001c643c1ee7058d01438fe868
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48098420"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a>Geschachtelter AFTER-Trigger wird sogar ausgelöst, wenn Triggerschachtelung OFF ist
  Der Upgrade Advisor hat einen AFTER-Trigger erkannt, der in einem für eine oder mehrere Tabellen definierten INSTEAD OF-Trigger geschachtelt ist. Geschachtelte AFTER-Trigger werden möglicherweise ausgelöst, wenn die `nested triggers`-Serverkonfigurationsoption auf 0 (null) festgelegt ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Der erste AFTER-Trigger, der in einem INSTEAD OF-Trigger geschachtelt ist, wird auch dann ausgelöst, wenn die `nested triggers`-Serverkonfigurationsoption auf 0 festgelegt ist. Jedoch werden bei dieser Einstellung nachfolgende AFTER-Trigger nicht ausgelöst.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Überprüfen Sie die Anwendungen auf geschachtelte Trigger, um zu ermitteln, ob die Anwendungen in Bezug auf dieses Verhalten bei Festlegung der `nested triggers`-Serverkonfigurationsoption auf 0 (Null) noch Ihren Geschäftsregeln entsprechen. Nehmen Sie dann geeignete Änderungen vor.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
