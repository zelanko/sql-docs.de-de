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
manager: craigg
ms.openlocfilehash: 84d04729e2f4c00c5d127a706727567c44855cd6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093683"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Nur Benutzer mit Systemadministratorberechtigungen können Protokolldateien für Auftragsschritte in das Dateisystem schreiben
  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erstellt optional ein Protokoll für jeden Auftragsschritt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Büros  
  
## <a name="description"></a>BESCHREIBUNG  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der-Agent Protokolle in das Dateisystem für Aufträge schreiben, die Mitglieder der festen Server Rolle **sysadmin** sind. Wenn der Besitzer des Auftrags kein Mitglied der **sysadmin** -Rolle ist und das Proxy Konto aktiviert ist, kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der-Agent Protokolle in das Dateisystem schreiben, indem er die Anmelde Informationen des Proxy Kontos verwendet.  
  
 Nachdem Sie das Upgrade ausgeführt haben, können Aufträge im Besitz von Benutzern, die keine Mitglieder der festen Server Rolle **sysadmin** sind, keine Protokolle mehr in das Dateisystem schreiben. Stattdessen können diese Benutzer die Option auswählen, um Ihre Protokolle in eine Tabelle in der **msdb** -Datenbank zu schreiben. Mitglieder der **sysadmin** -Rolle können weiterhin Protokolldateien in das Dateisystem schreiben.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Nach dem Upgrade werden Aufträge, die sich im Besitz von Benutzern befinden, die nicht Mitglied der **sysadmin** -Rolle sind, weiterhin ausgeführt, aber es werden keine Protokolle erstellt. Zum Protokollieren von Auftrags Schritten in einer Tabelle müssen Benutzer, die nicht Mitglied der **sysadmin** -Rolle sind, Ihre Aufträge manuell aktualisieren.  
  
 Weitere Informationen finden Sie in den Themen "Erstellen von Aufträgen", "Erstellen von Auftragsschritten" und "Handhaben mehrerer Auftragsschritte" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Probleme beim Aktualisieren des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
