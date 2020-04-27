---
title: MSSQLSERVER_3413 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2af9a604c511c50b542fbacd547afb3e09d7ea54
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62868370"
---
# <a name="mssqlserver_3413"></a>MSSQLSERVER_3413
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3413|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|MARKDB|  
|Meldungstext|Datenbank-ID %d. Die Datenbank konnte nicht als fehlerverdächtig gekennzeichnet werden. Fehler beim Getnext-Scan für NC für sys.databases.database_id. Identifizieren Sie die Ursache anhand vorheriger Fehlermeldungen im Fehlerprotokoll, und beheben Sie etwaige damit verbundene Probleme.|  
  
## <a name="explanation"></a>Erklärung  
 Es ist ein unerwarteter Fehler aufgetreten, während versucht wurde, eine Benutzerdatenbank im Katalog als SUSPECT zu markieren. Der Status SUSPECT wird nicht beibehalten.  
  
## <a name="user-action"></a>Benutzeraktion  
 Zeigen Sie vorherige Fehler an, und beheben Sie das Problem.  
  
  
