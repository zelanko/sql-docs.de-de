---
description: MSSQLSERVER_8712
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
ms.openlocfilehash: fefaaae1f1bed8001fd9c55ff8a26fad71daec51
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491130"
---
# <a name="mssqlserver_8712"></a>MSSQLSERVER_8712
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
  
