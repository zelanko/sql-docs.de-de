---
title: MSSQLSERVER_8689 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 18c8e591f255b57f8cbb935075695fca7bcc3960
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85637056"
---
# <a name="mssqlserver_8689"></a>MSSQLSERVER_8689
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|8689|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|USEPLAN_ERR_NO_DB|  
|Meldungstext|Die im USE PLAN-Hinweis angegebene Datenbank '%.*ls' ist nicht vorhanden. Geben Sie eine vorhandene Datenbank an.|  
  
## <a name="explanation"></a>Erklärung  
Eine im USE PLAN-Hinweis angegebene Datenbank ist nicht vorhanden.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie sicher, dass alle im USE PLAN-Hinweis angegebenen Datenbanken vorhanden sind.  
  
## <a name="see-also"></a>Weitere Informationen  
[Abfragehinweise &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
  
