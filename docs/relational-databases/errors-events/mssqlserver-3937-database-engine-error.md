---
title: MSSQLSERVER_3937 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3cb93f99d996cc992fc47873b2a3863caec7ec6d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63028754"
---
# <a name="mssqlserver3937"></a>MSSQLSERVER_3937
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
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
