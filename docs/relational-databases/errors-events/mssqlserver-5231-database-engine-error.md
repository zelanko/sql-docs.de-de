---
title: MSSQLSERVER_5231 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6be551a13382279401648b1579b542a71142dd23
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717051"
---
# <a name="mssqlserver_5231"></a>MSSQLSERVER_5231
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|5231|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|Meldungstext|Objekt-ID „O_ID“ (Objekt „NAME“): Deadlock beim Versuch, dieses Objekt für die Überprüfung zu sperren. Das Objekt wurde ausgelassen und wird nicht verarbeitet.|  
  
## <a name="explanation"></a>Erklärung  
Es kam zu einem Deadlock, als von DBCC versucht wurde, das Objekt zu sperren. DBCC wurde als Deadlockopfer ausgewählt. Das Objekt wird nicht verarbeitet.  
  
## <a name="user-action"></a>Benutzeraktion  
Keine  
  
