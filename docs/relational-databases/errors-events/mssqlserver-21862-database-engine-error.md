---
title: MSSQLSERVER_21862 | Microsoft-Dokumentation
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
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3abf49fbbf0a41ffe5e8e25995ea6900c8f2f00f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|MSSQLSERVER|  
|Ereignis-ID|21862|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21862|  
|Meldungstext|FILESTREAM-Spalten können nicht in einer Veröffentlichung mit der Synchronisierungsmethode 'database snapshot' oder 'database snapshot character' veröffentlicht werden.|  
  
## <a name="explanation"></a>Erklärung  
Da der Zugriff auf FILESTREAM-Daten über eine Datenbankmomentaufnahme nicht möglich ist, kann der Momentaufnahme-Agent FILESTREAM-Daten nicht lesen, wenn für die Synchronisierungsmethode der Veröffentlichung der *Datenbankmomentaufnahme* - oder der *database_snapshot_character*-Parameter angegeben wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
Verwenden Sie für die Veröffentlichung eine andere Synchronisierungsmethode als die *Datenbankmomentaufnahme* oder *database_snapshot_character*, oder schließen Sie die FILESTREAM-Spalte aus der Veröffentlichung aus.  
  
