---
title: MSSQLSERVER_611 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d32d67f02af9c377720480ec27dd7e3078c069a1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver611"></a>MSSQLSERVER_611
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|611|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|VAR_SIZE_TOO_BIG|  
|Meldungstext|Es kann keine Zeile eingefügt oder aktualisiert werden, da die Gesamtgröße der Variablenspalte, einschließlich Verwaltungsbytes, die maximal zulässige Größe um %d Bytes überschreitet.|  
  
## <a name="explanation"></a>Erklärung  
Die Maximalgröße der Variablenspalte übersteigt die vom Schema zugelassene Größe. Fehler 611 wird zurückgegeben, wenn die Variablenspalte die maximal zulässige Größe überschreitet, sofern das vardecimal-Speicherformat aktiviert ist, oder wenn die Größe der Variablenspalte die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] für komprimierte Datensätze maximal zulässige Größe überschreitet.  
  
## <a name="user-action"></a>Benutzeraktion  
Reduzieren Sie die Größe des Datensatzes.  
  
