---
title: MSSQLSERVER_2546 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 41e4f62a27a3f4a126c9d25b00c03f7f4c31b933
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047158"
---
# <a name="mssqlserver2546"></a>MSSQLSERVER_2546
    
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
  
## <a name="see-also"></a>Siehe auch  
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [Neuorganisieren und Neuerstellen von Indizes](../indexes/indexes.md)  
  
  
