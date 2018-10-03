---
title: MSSQLSERVER_9001 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cfc717c63cb85207315d00ae8dc06fdd881a503c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053600"
---
# <a name="mssqlserver9001"></a>MSSQLSERVER_9001
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9001|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LOG_NOT_AVAIL|  
|Meldungstext|Das Protokoll für die '%.*ls'-Datenbank ist nicht verfügbar. Überprüfen Sie das Ereignisprotokoll auf verwandte Fehlermeldungen. Beheben Sie ggf. alle Fehler, und starten Sie die Datenbank neu.|  
  
## <a name="explanation"></a>Erklärung  
 Das Datenbankprotokoll wurde offline geschaltet Normalerweise ist dies ein Zeichen für einen schwerwiegenden Fehle, der einen Neustart der Datenbank erfordert.  
  
## <a name="user-action"></a>Benutzeraktion  
 Diagnostizieren Sie andere Fehler, und starten Sie die Instanz von SQL Server neu, wenn sie sich noch nicht selbst neu gestartet hat.  
  
  
