---
title: MSSQLSERVER_2508 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 37a5f8976dabed380173dc56bb99edd07daec4df
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver2508"></a>MSSQLSERVER_2508
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2508|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|Meldungstext|Die %.*ls-Anzahl für das "%.\*ls"-Objekt, Index-ID %d, Partitions-ID %I64d, Zuordnungseinheits-ID %I64d (%.\*ls-Typ) ist nicht richtig. Führen Sie DBCC UPDATEUSAGE aus.|  
  
## <a name="explanation"></a>Erklärung  
In Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ist es möglich, dass für die Zeilen- und Seitenanzahl von Tabellen und Indizes falsche Werte entstehen. Datenbanken, die in Versionen vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] erstellt wurden, können falsche Zählwerte enthalten. DBCC CHECKDB wurde verbessert, sodass diese Fehler nun erkannt werden und diese Meldung zurückgegeben wird, wenn der Fehler erkannt wird.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie DBCC UPDATEUSAGE für das angegebene Objekt bzw. den angegeben Index oder für die Datenbank aus, in der das Objekt enthalten ist, um die falsche Anzahl zu korrigieren.  
  
