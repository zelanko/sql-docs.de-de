---
title: MSSQLSERVER_8712 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a9abebe50426f671e444514b29ccc2235e4a2109
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68120480"
---
# <a name="mssqlserver_8712"></a>MSSQLSERVER_8712
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|8712|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|USEPLAN_ERR_NO_INDEX|  
|Meldungstext|Der im USE PLAN-Hinweis angegebene Index '%.*ls' ist nicht vorhanden. Geben Sie einen vorhandenen Index an, oder erstellen Sie einen Index mit dem angegebenen Namen.|  
  
## <a name="explanation"></a>Erklärung  
Ein im USE PLAN-Hinweis angegebener Index ist nicht vorhanden.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie sicher, dass alle im USE PLAN-Hinweis angegebenen Indizes vorhanden sind.  
  
## <a name="see-also"></a>Weitere Informationen  
[Abfragehinweise &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
  
