---
title: MSSQLSERVER_15661 | Microsoft-Dokumentation
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
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 089727123d4edc9ed5f1e30e4e9cd187b5ee0bbf
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver15661"></a>MSSQLSERVER_15661
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|15661|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum15661|  
|Meldungstext|Die gespeicherte Prozedur sp_estimate_data_compression_savings kann nicht für temporäre Tabellen verwendet werden.|  
  
## <a name="explanation"></a>Erklärung  
Eine temporäre Tabelle wurde als Argument für die gespeicherte Prozedur sp_estimate_data_compression_savings verwendet. Obwohl die Komprimierung von temporären Tabellen unterstützt wird, können Sie sp_estimate_data_compression_savings nicht verwenden, um die Komprimierungseinsparungen zu schätzen.  
  
## <a name="user-action"></a>Benutzeraktion  
Entfernen Sie die temporäre Tabelle als Argument für sp_estimate_data_compression_savings.  
  
