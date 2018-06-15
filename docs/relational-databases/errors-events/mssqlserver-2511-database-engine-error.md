---
title: MSSQLSERVER_2511 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3954cadaa9f9a9bdd847da05b15accb59ebbece7
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318221"
---
# <a name="mssqlserver2511"></a>MSSQLSERVER_2511
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2511|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_KEYS_OUT_OF_ORDER|  
|Meldungstext|Tabellenfehler: Objekt-ID %d, Index-ID %d, Partitions-ID %I64d, Zuordnungseinheits-ID %I64d (%.*ls-Typ). Falsche Schlüsselreihenfolge auf Seite %S_PGID, Slots %d und %d.|  
  
## <a name="explanation"></a>Erklärung  
Im angegebenen Index wurden Schlüssel mit falscher Reihenfolge erkannt. Die Seite, in der die Schlüssel enthalten sind, ist möglicherweise beschädigt.  
  
## <a name="user-action"></a>Benutzeraktion  
Erstellen Sie den angegebenen Index mithilfe der ALTER INDEX REBUILD-Anweisung neu.  
  
