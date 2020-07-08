---
title: Vergleichen und Analysieren von Ausführungsplänen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 0689bf7815074048c810a47b5784b7bfa8831b8a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85655756"
---
# <a name="compare-and-analyze-execution-plans"></a>Vergleichen und Analysieren von Ausführungsplänen
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
In diesem Abschnitt wird erläutert, wie Ausführungspläne mithilfe von Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verglichen und analysiert werden. Dieses Feature ist ab [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Version 17.4, verfügbar.  
  
Ausführungspläne zeigen grafisch an, welche Datenabrufmethoden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageoptimierer gewählt wurden. Ausführungspläne stellen die Ausführungskosten bestimmter Anweisungen und Abfragen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von Symbolen dar und nicht in der tabellarischen Form, die von den [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md)- oder [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md)-Anweisungen erzeugt wird. Durch diese grafische Darstellung sind die Leistungsmerkmale einer Abfrage wesentlich leichter zu verstehen. 

[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] enthält Funktionen, die es Benutzern ermöglichen, zwei Ausführungspläne zu vergleichen (z.B. wahrgenommene gute und schlechte Pläne für dieselbe Abfrage) und eine Ursachenanalyse durchzuführen. Ebenfalls enthalten ist die Funktionalität zum Ausführen einer einzelnen Abfrageplananalyse, die durch die Analyse des Ausführungsplans Einblicke in Szenarien gewährt, die die Leistung einer Abfrage beeinflussen können.

Weitere Informationen zu Abfrageausführungsplänen finden Sie unter [geschätzter Ausführungsplan](../../relational-databases/performance/display-the-estimated-execution-plan.md), [tatsächlicher Ausführungsplan](../../relational-databases/performance/display-an-actual-execution-plan.md) sowie im [Leitfaden zur Abfrageverarbeitungsarchitektur](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Vergleichen von Ausführungsplänen](../../relational-databases/performance/display-the-estimated-execution-plan.md)     
[Analysieren eines tatsächlichen Ausführungsplans](../../relational-databases/performance/display-an-actual-execution-plan.md)      
  
