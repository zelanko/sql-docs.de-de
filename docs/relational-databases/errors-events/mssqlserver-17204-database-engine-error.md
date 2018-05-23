---
title: MSSQLSERVER_17204 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c71de5b96a2b849e17c919980b096678bd772b7e
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver17204"></a>MSSQLSERVER_17204
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17204|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBLKIO_DEVOPENFAILED|  
|Meldungstext|% ls: Die Datei %ls für die Dateinummer %d konnte nicht geöffnet werden.  Betriebssystemfehler: %ls.|  
  
## <a name="explanation"></a>Erklärung  
SQL Server konnte die angegebene Datei aufgrund des angegebenen Fehlers nicht öffnen.  
  
## <a name="user-action"></a>Benutzeraktion  
Erstellen Sie eine Diagnose für das Betriebssystem, und korrigieren Sie es, wiederholen Sie dann den Vorgang.  
  
