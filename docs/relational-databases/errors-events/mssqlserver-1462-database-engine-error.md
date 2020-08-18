---
description: MSSQLSERVER_1462
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
ms.openlocfilehash: 26254a4cac29b4295c3cf163c0f09b2ce6d818aa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88334076"
---
# <a name="mssqlserver_1462"></a>MSSQLSERVER_1462
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
  
