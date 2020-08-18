---
description: MSSQLSERVER_10534
title: MSSQLSERVER_10534 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c649266f1eabb1c4d667060e78f96ac8574c026
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338556"
---
# <a name="mssqlserver_10534"></a>MSSQLSERVER_10534
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|10534|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_INVALID_PARAMS|  
|Meldungstext|Die Planhinweisliste '%.\*ls' kann nicht erstellt werden, weil der für **\@params** angegebene Wert ungültig ist. Verwenden Sie für den Wert das Format *parameter_name parameter_type*, oder geben Sie NULL an.|  
  
## <a name="explanation"></a>Erklärung  
Der für **\@params** angegebene Wert ist ungültig.  
  
## <a name="user-action"></a>Benutzeraktion  
Verwenden Sie für den Wert das Format *parameter_name parameter_type*, oder geben Sie NULL an.  
  
## <a name="see-also"></a>Weitere Informationen  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
