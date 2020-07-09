---
title: MSSQLSERVER_10520 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f83b574d6201d0845f23c9194ea2e873d90daa5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781482"
---
# <a name="mssqlserver_10520"></a>MSSQLSERVER_10520
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|10520|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_PARAM_NOT_ALLOWED|  
|Meldungstext|Die Planhinweisliste „%.*ls“ kann nicht erstellt werden, weil @type als „%ls“ angegeben und ein Wert ungleich NULL für den „%ls“-Parameter festgelegt wurde. Dieser Typ erfordert einen NULL-Wert für den Parameter. Geben Sie NULL für den Parameter an, oder ändern Sie den Typ in einen Typ, der Werte ungleich NULL für den Parameter zulässt.|  
  
## <a name="explanation"></a>Erklärung  
Der in @type angegebene Typ erfordert einen Wert NULL für den angegebenen Parameter. Es wurde jedoch ein Wert ungleich NULL angegeben.  
  
## <a name="user-action"></a>Benutzeraktion  
Geben Sie NULL für den Parameter an, oder ändern Sie den Typ in einen Typ, der Werte ungleich NULL für den Parameter zulässt.  
  
## <a name="see-also"></a>Weitere Informationen  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
  
