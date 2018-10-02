---
title: MSSQLSERVER_3437 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 80732b100808f6af60e5fb07c68197096dc49b21
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663879"
---
# <a name="mssqlserver3437"></a>MSSQLSERVER_3437
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
