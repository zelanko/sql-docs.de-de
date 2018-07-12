---
title: MSSQLSERVER_3169 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "3169"
helpviewer_keywords:
- 3169 (Database Engine error)
ms.assetid: 7d4dbed6-bb94-4908-bc03-2040a9cf63bc
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cc119c1ebfc2c587bf12fb8337194e7516e4781c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423369"
---
# <a name="mssqlserver3169"></a>MSSQLSERVER_3169
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3169|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NA|  
|Meldungstext|Die Datenbank wurde auf einem Server der Version %ls gesichert. Diese Version ist mit diesem Server inkompatibel, da auf ihm die Version %ls ausgeführt wird. Stellen Sie die Datenbank auf einem Server wieder her, der die Sicherung unterstützt, oder verwenden Sie eine mit diesem Server kompatible Sicherung.|  
  
## <a name="explanation"></a>Erklärung  
 Bestimmte funktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wirken sich auf die Struktur der Datenbankdateien aus. Wenn Sie eine Datenbank auf einer anderen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wiederherstellen, ist das Dateiformat möglicherweise mit einer anderen Version von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nicht kompatibel.  
  
 Dieser Fehler kann beispielsweise verursacht werden, wenn das Vardecimal-Speicherformat in einer höheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird und dann versucht wird, die Datenbankdateien in einer niedrigeren Version als [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 wiederherzustellen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ermitteln Sie die Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die auf dem ursprünglichen Server ausgeführt wird. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], entweder mit der rechten Maustaste in des Servers, und klicken Sie dann auf **Eigenschaften** oder `SELECT @@VERSION` in einem Abfragefenster. Öffnen Sie die Datenbank mithilfe der ursprünglichen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ermitteln Sie die funktionen, die für die ursprüngliche Datenbank in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktiviert sind. Ändern Sie diese Einstellungen, um mit der Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu arbeiten, in der die Datenbank wiederhergestellt wird.  
  
  
