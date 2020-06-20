---
title: Überprüfen von Planhinweislisten nach einem Upgrade | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18cc0f93ddec46025f659bcb9489bfff3ca846ef
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066748"
---
# <a name="validate-plan-guides-after-upgrade"></a>Überprüfen von Planhinweislisten nach einem Upgrade
  Es empfiehlt sich, die Definitionen der Planhinweislisten nach einem Upgrade Ihrer Anwendung auf eine neue Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu zu bewerten und zu testen. Die Anforderungen an die Leistungsoptimierung und das Abgleichverhalten der Planhinweislisten können sich ändern. Eine ungültige Planhinweisliste führt zwar nicht zu einem Abfragefehler, der Plan wird jedoch ohne die Planhinweisliste kompiliert und ist daher eventuell nicht die beste Wahl. Nach dem Upgrade einer Datenbank auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]sollten Sie möglichst die folgenden Aufgaben durchführen:  
  
-   Überprüfen Sie bestehende Planhinweislisten mit der [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) -Funktion.  
  
-   Suchen Sie mit erweiterten Ereignissen einige Zeit lang anhand des [Plan Guide Unsuccessful-Ereignisses](../event-classes/plan-guide-unsuccessful-event-class.md) nach Plänen ohne Planhinweisliste.  
  
  
