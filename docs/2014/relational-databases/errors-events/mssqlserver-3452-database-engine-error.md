---
title: MSSQLSERVER_3452 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0e811d36160cf0a4477452acec336c61bf52e793
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62868067"
---
# <a name="mssqlserver_3452"></a>MSSQLSERVER_3452
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3452|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|REC_CHECKIDENTITY|  
|Meldungstext|Bei der Wiederherstellung der '%.*ls'-Datenbank (%d) wurden mögliche inkonsistente Identitätswerte in der Tabelle mit der ID %d erkannt. Führen Sie DBCC CHECKIDENT ('%.\*ls') aus.|  
  
## <a name="explanation"></a>Erklärung  
 Beim Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wurde vom Prozess zum Wiederherstellen der Identitätswerte in der Datenbank eine Inkonsistenz in den Metadaten festgestellt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie DBCC CHECKIDENT aus.  
  
  
