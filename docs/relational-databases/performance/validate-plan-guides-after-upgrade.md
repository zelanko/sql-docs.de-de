---
title: Überprüfen von Planhinweislisten nach einem Upgrade | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 43c7297f490c913663c8d08f62cabb7a21cca86d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636944"
---
# <a name="validate-plan-guides-after-upgrade"></a>Überprüfen von Planhinweislisten nach einem Upgrade
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Es empfiehlt sich, die Definitionen der Planhinweislisten nach einem Upgrade Ihrer Anwendung auf eine neue Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu zu bewerten und zu testen. Die Anforderungen an die Leistungsoptimierung und das Abgleichverhalten der Planhinweislisten können sich ändern. Eine ungültige Planhinweisliste führt zwar nicht zu einem Abfragefehler, der Plan wird jedoch ohne die Planhinweisliste kompiliert und ist daher eventuell nicht die beste Wahl. Nach dem Upgrade einer Datenbank auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]sollten Sie möglichst die folgenden Aufgaben durchführen:  
  
-   Überprüfen Sie bestehende Planhinweislisten mit der [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) -Funktion.  
  
-   Suchen Sie mit erweiterten Ereignissen einige Zeit lang anhand des [Plan Guide Unsuccessful-Ereignisses](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) nach Plänen ohne Planhinweisliste.  
  
  
