---
title: MSSQLSERVER_948 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: cb36765216f906b92cdd6b87e7890b94f3b15d37
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162047"
---
# <a name="mssqlserver948"></a>MSSQLSERVER_948
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|948|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NA|  
|Meldungstext|Die '%.*ls'-Datenbank kann nicht geöffnet werden, weil sie die Version %d aufweist. Dieser Server unterstützt Version %d und früher. Ein Herabstufungspfad wird nicht unterstützt.|  
  
## <a name="explanation"></a>Erklärung  
 Bestimmte funktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wirken sich auf die Struktur der Datenbankdateien aus. Wenn Sie eine Datenbank an eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anfügen, ist das Dateiformat möglicherweise mit einer anderen Version von [!INCLUDE[ssDE](../../includes/ssde-md.md)] nicht kompatibel.  
  
 Dieser Fehler kann beispielsweise verursacht werden, wenn das vardecimal-Speicherformat in einer höheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird und dann versucht wird, die Datenbankdateien in einer niedrigeren Version als [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 anzufügen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ermitteln Sie die Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die auf dem ursprünglichen Server ausgeführt wird. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], entweder mit der rechten Maustaste in des Servers, und klicken Sie dann auf **Eigenschaften** oder Typ `SELECT @@VERSION` in einem Abfragefenster. Öffnen Sie die Datenbank mithilfe der ursprünglichen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ermitteln Sie die funktionen, die für die ursprüngliche Datenbank in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktiviert sind. Ändern Sie diese Einstellungen, um mit der Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu arbeiten, in der die Datenbank angefügt wird.  
  
  