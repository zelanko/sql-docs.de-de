---
title: Anzeigen von Filterinformationen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: abeeac1dc2c6d06a0b1ce89f4dff35415f7189fc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63285614"
---
# <a name="view-filter-information-transact-sql"></a>Anzeigen von Filterinformationen (Transact-SQL)
  In diesem Thema wird beschrieben, wie mit integrierten Funktionen Filterinformationen zur Ablaufverfolgung angezeigt werden.  
  
### <a name="to-view-filter-information"></a>So zeigen Sie Filterinformationen an  
  
1.  Führen Sie **fn_trace_getfilterinfo** aus, indem Sie die ID der Ablaufverfolgung angeben, zu der Filterinformationen benötigt werden. Diese Funktion gibt eine Tabelle mit den Filtern, der Spalte, auf die die Filter angewendet werden, und den Werten, auf die der Filter angewendet wird, zurück.  
  
     Rufen Sie die Funktion folgendermaßen auf:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Gespeicherte Prozeduren von SQL Server Profiler &#40;SQL Server Profiler&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
