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
ms.openlocfilehash: cac466e6eb50ad4b7a8848a1159963cb0fd35e22
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033300"
---
# <a name="mssqlserver_3937"></a>MSSQLSERVER_3937
    
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
  
