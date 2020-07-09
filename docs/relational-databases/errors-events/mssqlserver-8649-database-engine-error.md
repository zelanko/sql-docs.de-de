---
title: MSSQLSERVER_8649 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d305866fb884b62540cfbe2cc13a613981999749
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765279"
---
# <a name="mssqlserver_8649"></a>MSSQLSERVER_8649
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|8649|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|COST_TOO_HIGH|  
|Meldungstext|Die Abfrage wurde abgebrochen, da die geschätzten Kosten der Abfrage (%d) den konfigurierten Schwellenwert %d überschreiten. Wenden Sie sich an den Systemadministrator.|  
  
## <a name="explanation"></a>Erklärung  
Die Abfrage wurde abgebrochen, weil die geschätzten Kosten dieser Abfrage den für QUERY_GOVERNOR_COST_LIMIT festgelegten konfigurierten Schwellenwert überschreiten.  
  
## <a name="user-action"></a>Benutzeraktion  
Setzen Sie die Option QUERY_GOVERNOR_COST_LIMIT auf einen höheren Wert.  
  
## <a name="see-also"></a>Weitere Informationen  
[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  
