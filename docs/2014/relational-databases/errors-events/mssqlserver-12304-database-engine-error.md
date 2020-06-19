---
title: MSSQLSERVER_12304 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2347fc46fe5ab83ef2ff46b81500cd737ed02d8
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969640"
---
# <a name="mssqlserver_12304"></a>MSSQLSERVER_12304
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|12304|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|HK_UNSUPPORTED_IDENTITY_TABLE_VAR|  
|Meldungstext|Die Verwendung eines speicheroptimierten Tabellentyps, der die IDENTITY-Eigenschaft für die zugehörigen Spalten einsetzt, wird nicht unterstützt, wenn der Typ außerhalb des Kontexts einer systemintern kompilierten gespeicherten Prozedur auftritt.|  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie keinen speicheroptimierten Tabellentyp, wenn für dessen Spalten die IDENTITY-Eigenschaft eingesetzt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
