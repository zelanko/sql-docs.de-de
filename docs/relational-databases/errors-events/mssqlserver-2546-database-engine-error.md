---
title: MSSQLSERVER_2546 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 983c5536d08d9701fd301ace4ca8d2b5d7e76f71
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597748"
---
# <a name="mssqlserver2546"></a>MSSQLSERVER_2546
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2546|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_INDEX_MARKED_DISABLED|  
|Meldungstext|Der 'INDEX_NAME'-Index für die 'OBJECT_NAME'-Tabelle ist als deaktiviert markiert. Erstellen Sie den Index neu, um ihn online zu schalten.|  
  
## <a name="explanation"></a>Erklärung  
Der angegebene Index ist als offline markiert oder deaktiviert. Daher kann dieser Index nicht geprüft werden.  
  
## <a name="user-action"></a>Benutzeraktion  
Erstellen Sie den Index mithilfe von ALTER INDEX neu.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[Neuorganisieren und Neuerstellen von Indizes](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
