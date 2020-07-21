---
title: MSSQLSERVER_15661 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9ad20f630056ac4e2f0fe37686955012c0239234
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553745"
---
# <a name="mssqlserver_15661"></a>MSSQLSERVER_15661
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|15661|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum15661|  
|Meldungstext|Die gespeicherte Prozedur sp_estimate_data_compression_savings kann nicht für temporäre Tabellen verwendet werden.|  
  
## <a name="explanation"></a>Erklärung  
 Eine temporäre Tabelle wurde als Argument für die gespeicherte Prozedur sp_estimate_data_compression_savings verwendet. Obwohl die Komprimierung von temporären Tabellen unterstützt wird, können Sie sp_estimate_data_compression_savings nicht verwenden, um die Komprimierungseinsparungen zu schätzen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Entfernen Sie die temporäre Tabelle als Argument für sp_estimate_data_compression_savings.  
  
  
