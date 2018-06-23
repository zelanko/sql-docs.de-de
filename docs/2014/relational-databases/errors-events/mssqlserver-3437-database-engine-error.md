---
title: MSSQLSERVER_3437 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 40452b7900bf51c718917e4e6360e596261476d4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058291"
---
# <a name="mssqlserver3437"></a>MSSQLSERVER_3437
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3437|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NODTC|  
|Meldungstext|Fehler beim Wiederherstellen der '%.*ls'-Datenbank. Es konnte keine Verbindung mit Microsoft Distributed Transaction Coordinator (MS DTC) hergestellt werden, um den Beendigungsstatus von Transaktion %S_XID zu überprüfen. Korrigieren Sie MS DTC, und führen Sie die Wiederherstellung erneut aus.|  
  
## <a name="explanation"></a>Erklärung  
 Eine oder mehrere verteilte Transaktionen, für die MS DTC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator) verwendet wurde, waren nicht abgeschlossen, als die Datenbank beendet wurde. Bei der Wiederherstellung dieser Datenbank sind Fehler aufgetreten, da in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Verbindung mit MS DTC hergestellt werden kann, um die Transaktionen abzuschließen oder einen Rollback für die Transaktionen auszuführen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Zum Wiederherstellen dieser Datenbank müssen Sie zunächst das Problem mit MS DTC lösen. Weitere Informationen zu diesem Problem mit MS DTC finden Sie in den Windows-Ereignisprotokollen. Wenn das Problem mit MS DTC nicht gelöst und die Datenbank nicht wiederhergestellt werden kann, führen Sie die Wiederherstellung einer Sicherungskopie der Datenbank aus.  
  
  