---
title: Überprüfen von Planhinweislisten nach einem Upgrade | Microsoft-Dokumentation
description: Wenn Sie ein Upgrade Ihrer Anwendung auf ein neues Release von SQL Server ausführen, empfiehlt es sich, die Definitionen der Planhinweislisten nach neu zu bewerten und zu testen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 8486277a3f46775a05c146e411e56e12b2fd3e1f
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96503630"
---
# <a name="validate-plan-guides-after-upgrade"></a>Überprüfen von Planhinweislisten nach einem Upgrade
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Es empfiehlt sich, die Definitionen der Planhinweislisten nach einem Upgrade Ihrer Anwendung auf eine neue Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu zu bewerten und zu testen. Die Anforderungen an die Leistungsoptimierung und das Abgleichverhalten der Planhinweislisten können sich ändern. Eine ungültige Planhinweisliste führt zwar nicht zu einem Abfragefehler, der Plan wird jedoch ohne die Planhinweisliste kompiliert und ist daher eventuell nicht die beste Wahl. Nach dem Upgrade einer Datenbank auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]sollten Sie möglichst die folgenden Aufgaben durchführen:  
  
-   Überprüfen Sie bestehende Planhinweislisten mit der [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) -Funktion.  
  
-   Suchen Sie mit erweiterten Ereignissen einige Zeit lang anhand des [Plan Guide Unsuccessful-Ereignisses](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) nach Plänen ohne Planhinweisliste.  
  
  
