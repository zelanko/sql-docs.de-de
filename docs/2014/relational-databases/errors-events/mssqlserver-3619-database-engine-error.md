---
title: MSSQLSERVER_3619 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6a82902d69a1d5214b29f43d19ded58c76293ec4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914026"
---
# <a name="mssqlserver3619"></a>MSSQLSERVER_3619
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3619|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SYS_NOLOG|  
|Meldungstext|In die Datenbank mit der ID %d konnte kein Prüfpunktdatensatz geschrieben werden, da für das Protokoll kein Speicherplatz mehr zur Verfügung steht. Bitten Sie den Datenbankadministrator, das Protokoll abzuschneiden oder den Datenbankprotokolldateien mehr Speicherplatz zuzuordnen.|  
  
## <a name="explanation"></a>Erklärung  
 Für das Transaktionsprotokoll steht kein Speicherplatz mehr zur Verfügung.  
  
## <a name="user-action"></a>Benutzeraktion  
 Schneiden Sie das Protokoll ab, um Speicherplatz freizugeben, oder ordnen Sie dem Protokoll mehr Speicherplatz zu. Weitere Informationen finden Sie unter "Problembehandlung bei vollen Transaktionsprotokollen (Fehler 9002)" in der SQL Server-Onlinedokumentation.  
  
  
