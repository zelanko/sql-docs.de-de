---
title: Anzeigen der SQL Server-Fehlerprotokoll | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cycling SQL Server error log
- viewing SQL Server error log
- errors [SQL Server], logs
- SQL Server error log
- displaying SQL Server error log
- logs [SQL Server], SQL Server error logs
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88c5b77b4ac0f2d0f8ed579f2ff32eae8c263610
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150293"
---
# <a name="viewing-the-sql-server-error-log"></a>Anzeigen des SQL Server-Fehlerprotokolls
  Zeigen Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll an, um sicherzustellen, dass bestimmte Prozesse erfolgreich abgeschlossen wurden (z.B. Sicherungs- und Wiederherstellungsvorgänge, Batchbefehle oder andere Skripts und Prozesse). Dies ist hilfreich, um aktuelle oder potenzielle Problembereiche zu ermitteln, einschließlich automatischer Wiederherstellungsmeldungen (insbesondere, wenn eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angehalten und neu gestartet wurde), Kernelmeldungen oder anderer Fehlermeldungen auf Serverebene.  
  
 Um das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll anzuzeigen, können Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder einen beliebigen Text-Editor verwenden. Weitere Informationen zum Anzeigen des Fehlerprotokolls finden Sie unter [Open Log File Viewer](../../relational-databases/logs/log-file-viewer.md). Standardmäßig befindet sich das Fehlerprotokoll unter `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` und `ERRORLOG.`*n* .  
  
 Es wird immer dann ein neues Fehlerprotokoll erstellt, wenn eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestartet wird, obwohl die gespeicherte Systemprozedur [sp_cycle_errorlog](/sql/relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql) zum Durchlaufen der Fehlerprotokolldateien verwendet werden kann, ohne dass die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu gestartet werden muss. In der Regel behält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherungen der letzten sechs Protokolle bei. Dabei erhält die letzte Sicherung die Erweiterung .1, die zweitletzte Sicherung die Erweiterung .2 usw. Das aktuelle Fehlerprotokoll hat keine Erweiterung.  
  
 Beachten Sie, dass Sie auch das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll zu Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzeigen können, die offline sind oder nicht gestartet werden können. Weitere Informationen finden Sie unter [Anzeigen von Offlineprotokolldateien](../../relational-databases/logs/view-offline-log-files.md).  
  
  
