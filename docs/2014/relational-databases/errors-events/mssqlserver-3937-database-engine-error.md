---
title: MSSQLSERVER_3937 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 819db3b9668aaf8339108ffedaf31fd4db513e5f
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551526"
---
# <a name="mssqlserver_3937"></a>MSSQLSERVER_3937
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|MSSQLSERVER|  
|Ereignis-ID|3937|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|XACT_FILESTREAM_ROLLBACK_ERROR|  
|Meldungstext|Fehler beim Benachrichtigen des FILESTREAM-Filtertreibers über das Rollback einer Transaktion. Fehlercode: 0x%0x.|  
  
## <a name="explanation"></a>Erklärung  
 Beim Ausgeben einer Rollbackbenachrichtigung für eine Transaktion wurde vom RsFx-Treiber ein Fehler zurückgegeben. Dieser Fehler kann auftreten, wenn nicht genügend Ressourcen zur Verfügung stehen. Hierdurch kann ein geringfügiger Speicherverlust im RsFx-Filtertreiber entstehen, jedoch nur bis zum Ende des sqlservr.exe-Prozesses, durch den die Transaktion erstellt wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
  
