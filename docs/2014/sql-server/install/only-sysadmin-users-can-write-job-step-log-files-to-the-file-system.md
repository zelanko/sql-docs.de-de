---
title: Nur sysadmin-Benutzer können Auftrags Schritt-Protokolldateien in das Dateisystem schreiben. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e2bf5095ac1e6b67f6c6f3f87444879913916e1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012180"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Nur Benutzer mit Systemadministratorberechtigungen können Protokolldateien für Auftragsschritte in das Dateisystem schreiben
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erstellt optional ein Protokoll für jeden Auftragsschritt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>BESCHREIBUNG  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann der-Agent Protokolle in das Dateisystem für Aufträge schreiben, die Mitglieder der festen Server Rolle **sysadmin** sind. Wenn der Besitzer des Auftrags kein Mitglied der **sysadmin** -Rolle ist und das Proxy Konto aktiviert ist, kann der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Protokolle in das Dateisystem schreiben, indem er die Anmelde Informationen des Proxy Kontos verwendet.  
  
 Nachdem Sie das Upgrade ausgeführt haben, können Aufträge im Besitz von Benutzern, die keine Mitglieder der festen Server Rolle **sysadmin** sind, keine Protokolle mehr in das Dateisystem schreiben. Stattdessen können diese Benutzer die Option auswählen, um Ihre Protokolle in eine Tabelle in der **msdb** -Datenbank zu schreiben. Mitglieder der **sysadmin** -Rolle können weiterhin Protokolldateien in das Dateisystem schreiben.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Nach dem Upgrade werden Aufträge, die sich im Besitz von Benutzern befinden, die nicht Mitglied der **sysadmin** -Rolle sind, weiterhin ausgeführt, aber es werden keine Protokolle erstellt. Zum Protokollieren von Auftrags Schritten in einer Tabelle müssen Benutzer, die nicht Mitglied der **sysadmin** -Rolle sind, Ihre Aufträge manuell aktualisieren.  
  
 Weitere Informationen finden Sie in den Themen "Erstellen von Aufträgen", "Erstellen von Auftragsschritten" und "Handhaben mehrerer Auftragsschritte" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Probleme beim Aktualisieren des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
