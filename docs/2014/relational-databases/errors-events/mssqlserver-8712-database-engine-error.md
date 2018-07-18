---
title: MSSQLSERVER_8712 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: db6b162b08fc60a96bda225b1b2118f5644107d2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413759"
---
# <a name="mssqlserver8712"></a>MSSQLSERVER_8712
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|8712|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|USEPLAN_ERR_NO_INDEX|  
|Meldungstext|Der im USE PLAN-Hinweis angegebene Index '%.*ls' ist nicht vorhanden. Geben Sie einen vorhandenen Index an, oder erstellen Sie einen Index mit dem angegebenen Namen.|  
  
## <a name="explanation"></a>Erklärung  
 Ein im USE PLAN-Hinweis angegebener Index ist nicht vorhanden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass alle im USE PLAN-Hinweis angegebenen Indizes vorhanden sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Abfragehinweise (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)   
 [Planhinweislisten](../performance/plan-guides.md)  
  
  
