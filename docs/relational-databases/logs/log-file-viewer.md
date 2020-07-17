---
title: Protokolldatei-Viewer | Microsoft-Dokumentation
description: Verwenden Sie den Protokolldatei-Viewer in SQL Server Management Studio, um Informationen über Fehler und Ereignisse zu erhalten, die in Protokolldateien erfasst wurden.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7425bb2175b9a2e7b813f63e7d78aec7e73ef5ec
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85668129"
---
# <a name="log-file-viewer"></a>Protokolldatei-Viewer
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Sie können mithilfe des Protokolldatei-Viewers in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf Informationen zu Fehlern und Ereignissen zugreifen, die in Protokollen aufgezeichnet wurden.  
  
## <a name="benefits-of-using-log-file-viewer"></a>Vorteile der Verwendung des Protokolldatei-Viewers  
 Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Protokolldateien aus einer lokalen oder Remoteinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzeigen, wenn die Zielinstanz offline ist oder nicht gestartet werden kann. Auf die Offlineprotokolldateien können Sie von Registrierte Server oder programmgesteuert mit WMI- und WQL (WMI Query Language)-Abfragen zugreifen. Weitere Informationen finden Sie unter [Anzeigen von Offlineprotokolldateien](../../relational-databases/logs/view-offline-log-files.md). Mithilfe des Protokolldatei-Viewers können Sie auf die folgenden Arten von Protokolldateien zugreifen:  
  
-   Überwachungsauflistung  
  
-   Datensammlung  
  
-   Datenbank-E-Mail  
  
-   Auftragsverlauf  
  
-   Wartungspläne  
  
-   Remotewartungspläne  
  
-   SQL Server  
  
-   SQL Server-Agent  
  
-   Windows NT (Windows-Ereignisse, auf die auch mithilfe der Windows-Ereignisanzeige zugegriffen werden kann.)  
  
## <a name="log-file-viewer-tasks"></a>Tasks im Protokolldatei-Viewer  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie der Protokolldatei-Viewer in Abhängigkeit der Informationen, die Sie anzeigen möchten, geöffnet wird.|[Öffnen des Protokolldatei-Viewers](../../relational-databases/logs/open-log-file-viewer.md)|  
|Beschreibt, wie Offlineprotokolldateien über registrierte Server angezeigt werden und wie WMI-Berechtigungen überprüft werden.|[Anzeigen von Offlineprotokolldateien](../../relational-databases/logs/view-offline-log-files.md)|  
|Öffnet die F1-Hilfe für den Protokolldatei-Viewer.|[Protokolldatei-Viewer (F1-Hilfe)](../../relational-databases/logs/log-file-viewer-f1-help.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [SQL Server-Agent-Fehlerprotokoll](../../ssms/agent/sql-server-agent-error-log.md)  
  
  
