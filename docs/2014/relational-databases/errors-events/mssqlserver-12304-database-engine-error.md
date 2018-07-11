---
title: MSSQLSERVER_12304 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
caps.latest.revision: 4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f38066cfe673c68bb77cd0a5f83fa39b988fc4b5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421939"
---
# <a name="mssqlserver12304"></a>MSSQLSERVER_12304
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|12304|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|HK_UNSUPPORTED_IDENTITY_TABLE_VAR|  
|Meldungstext|Die Verwendung eines speicheroptimierten Tabellentyps, der die IDENTITY-Eigenschaft für die zugehörigen Spalten einsetzt, wird nicht unterstützt, wenn der Typ außerhalb des Kontexts einer systemintern kompilierten gespeicherten Prozedur auftritt.|  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie keinen speicheroptimierten Tabellentyp, wenn für dessen Spalten die IDENTITY-Eigenschaft eingesetzt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
