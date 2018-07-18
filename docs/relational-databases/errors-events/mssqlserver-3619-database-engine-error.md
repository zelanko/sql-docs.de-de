---
title: MSSQLSERVER_3619 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3593c8282b650a45f061bc3f7fb3dece5ffa6228
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318661"
---
# <a name="mssqlserver3619"></a>MSSQLSERVER_3619
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3619|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SYS_NOLOG|  
|Meldungstext|In die Datenbank mit der ID %d konnte kein Prüfpunktdatensatz geschrieben werden, da für das Protokoll kein Speicherplatz mehr zur Verfügung steht. Bitten Sie den Datenbankadministrator, das Protokoll abzuschneiden oder den Datenbankprotokolldateien mehr Speicherplatz zuzuordnen.|  
  
## <a name="explanation"></a>Erklärung  
Für das Transaktionsprotokoll steht kein Speicherplatz mehr zur Verfügung.  
  
## <a name="user-action"></a>Benutzeraktion  
Schneiden Sie das Protokoll ab, um Speicherplatz freizugeben, oder ordnen Sie dem Protokoll mehr Speicherplatz zu. Weitere Informationen finden Sie unter "Problembehandlung bei vollen Transaktionsprotokollen (Fehler 9002)" in der SQL Server-Onlinedokumentation.  
  
