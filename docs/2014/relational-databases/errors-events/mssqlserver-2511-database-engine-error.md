---
title: MSSQLSERVER_2511 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1748e8b483eecee43da921bd268d419408924af3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62868963"
---
# <a name="mssqlserver_2511"></a>MSSQLSERVER_2511
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2511|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_KEYS_OUT_OF_ORDER|  
|Meldungstext|Tabellenfehler: Objekt-ID %d, Index-ID %d, Partitions-ID %I64d, Zuordnungseinheits-ID %I64d (%.*ls-Typ). Falsche Schlüsselreihenfolge auf Seite %S_PGID, Slots %d und %d.|  
  
## <a name="explanation"></a>Erklärung  
 Im angegebenen Index wurden Schlüssel mit falscher Reihenfolge erkannt. Die Seite, in der die Schlüssel enthalten sind, ist möglicherweise beschädigt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Erstellen Sie den angegebenen Index mithilfe der ALTER INDEX REBUILD-Anweisung neu.  
  
  
