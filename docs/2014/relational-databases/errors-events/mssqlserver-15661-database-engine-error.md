---
title: MSSQLSERVER_15661 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7b407f652dc2ef9bcca807c359120166d5f31f89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046906"
---
# <a name="mssqlserver15661"></a>MSSQLSERVER_15661
    
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
  
  