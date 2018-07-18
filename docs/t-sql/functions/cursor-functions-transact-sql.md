---
title: Cursorfunktionen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], cursors
- cursor functions
ms.assetid: 7d9daa10-4c50-4212-9400-42120222b2b8
caps.latest.revision: 27
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d19f119043a64ff5ae42152a09037bf8d9425d2f
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37787581"
---
# <a name="cursor-functions-transact-sql"></a>Cursorfunktionen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Skalarfunktionen geben Informationen über Cursor zurück:
  
|||  
|-|-|  
|[@@CURSOR_ROWS](../../t-sql/functions/cursor-rows-transact-sql.md)|[CURSOR_STATUS](../../t-sql/functions/cursor-status-transact-sql.md)|  
|[@@FETCH_STATUS](../../t-sql/functions/fetch-status-transact-sql.md)||  
  
Alle Cursorfunktionen sind nicht deterministisch. Das heißt, dass diese Funktionen nicht bei jeder Ausführung stets dieselben Ergebnisse zurückgeben, selbst wenn sie mit denselben Eingabewerten aufgerufen wurden. Weitere Informationen zu Funktionsdeterminismus finden Sie unter [Deterministische und nicht deterministische Funktionen](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="see-also"></a>Siehe auch
[Integrierte Funktionen &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)
  
  
