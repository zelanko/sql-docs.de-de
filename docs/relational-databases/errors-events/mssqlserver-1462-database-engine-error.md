---
title: MSSQLSERVER_1462 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 185a7d78f10656dc932259fb1098570190941afa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62859340"
---
# <a name="mssqlserver1462"></a>MSSQLSERVER_1462
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1462|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBM_DISABLED_DUE_TO_FAILED_REDO|  
|Meldungstext|Die Datenbankspiegelung wird aufgrund eines Fehlers beim Wiederholungsvorgang deaktiviert. Der Vorgang kann nicht fortgesetzt werden.|  
  
## <a name="explanation"></a>Erklärung  
Bei der Datenbankspiegelung ist beim Wiederholungsvorgang für einen Protokolldatensatz für den Spiegel ein Fehler aufgetreten.  
  
### <a name="possible-causes"></a>Mögliche Ursachen  
Die wahrscheinlichste Ursache besteht darin, dass ein Vorgang zum Hinzufügen einer Datei für die Prinzipaldatenbank abgeschlossen wurde, bei diesem Vorgang auf der Spiegeldatenbank jedoch ein Fehler aufgetreten ist, da sich Dateinamen oder Verzeichnisstrukturen auf dem Prinzipalserver und dem Spiegelserver unterscheiden.  
  
## <a name="user-action"></a>Benutzeraktion  
Suchen Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll nach der Fehlerursache. Versuchen Sie, die Fehlerursache zu beheben, und setzen Sie anschließend die Datenbankspiegelung fort.  
  
## <a name="see-also"></a>Weitere Informationen  
[Problembehandlung für die Datenbankspiegelungskonfiguration &#40;SQL Server&#41;](~/database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
