---
title: MSSQLSERVER_2511 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c28be4ae43225cc4593291285c09115829be8da2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780446"
---
# <a name="mssqlserver_2511"></a>MSSQLSERVER_2511
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
  
