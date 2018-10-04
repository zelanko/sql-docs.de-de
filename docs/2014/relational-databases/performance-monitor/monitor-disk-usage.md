---
title: Überwachen der Datenträgerverwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9520c304cc98183a66bc60409fbefe9dcfa79985
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133670"
---
# <a name="monitor-disk-usage"></a>Überwachen der Datenträgerverwendung
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet Aufrufe für die Microsoft Windows-Betriebssystemeingabe/-ausgabe, um Lese- und Schreibvorgänge auf dem Datenträger auszuführen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwaltet wann und wie Datenträger-E/A ausgeführt wird, aber das Windows-Betriebssystem führt die zugrunde liegenden E/A-Vorgänge aus. Das E/A-Teilsystem umfasst Systembus, Datenträgercontrollerkarten, Datenträger, Bandlaufwerke, CD-ROM-Laufwerk und zahlreiche andere E/A-Geräte. Datenträger-E/A ist häufig die Ursache von Engpässen in einem System.  
  
 Die Überwachung der Datenträgeraktivitäten ist auf zwei Bereiche konzentriert:  
  
-   Überwachen der Datenträger-E/A und Erkennen von zu häufigem Auslagern  
  
-   Isolieren der Datenträgeraktivitäten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Weitere Informationen finden Sie unter [Überwachen der Datenträgernutzung](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)  
  
  
