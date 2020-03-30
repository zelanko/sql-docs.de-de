---
title: MSSQLSERVER_3413 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 84f983c9b450e625fdca08c46720a1cf22e8b84c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68098313"
---
# <a name="mssqlserver_3413"></a>MSSQLSERVER_3413
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
