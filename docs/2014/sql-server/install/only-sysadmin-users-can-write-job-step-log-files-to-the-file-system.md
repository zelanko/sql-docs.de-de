---
title: Nur Benutzer mit Systemadministratorberechtigungen Protokolldateien für Auftragsschritte in das Dateisystem schreiben können | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e0b7638bbbf33cdd820467cd21edc40a6f5c42ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061070"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Nur Benutzer mit Systemadministratorberechtigungen können Protokolldateien für Auftragsschritte in das Dateisystem schreiben
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erstellt optional ein Protokoll für jeden Auftragsschritt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Protokolle schreiben kann, im Dateisystem für Aufträge, die von Mitgliedern der gehören die **Sysadmin** festen Serverrolle "". Wenn der Auftragsbesitzer kein Mitglied von ist das **Sysadmin** Rolle und das Proxykonto aktiviert ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent kann Protokolle in das Dateisystem schreiben, mit den Anmeldeinformationen des Proxykontos.  
  
 Nach dem upgrade können Aufträge, die Benutzern gehören, die nicht Mitglieder sind von der **Sysadmin** festen Serverrolle "" kann nicht mehr Protokolle in das Dateisystem schreiben. Stattdessen können diese Benutzer die Möglichkeit, ihre Protokolle in eine Tabelle schreiben auswählen der **Msdb** Datenbank. Mitglieder der **Sysadmin** Rolle kann immer noch Protokolldateien in das Dateisystem schreiben.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Nach dem upgrade können Aufträge, die Benutzern gehören, die nicht Mitglieder sind von der **Sysadmin** Rolle wird weiterhin ausgeführt, aber die Protokolle werden nicht erstellt werden. Auftragsschritte in eine Tabelle, die Benutzer anmelden, die keine Mitglieder sind von der **Sysadmin** Rolle muss ihre Aufträge manuell aktualisieren.  
  
 Weitere Informationen finden Sie in den Themen "Erstellen von Aufträgen", "Erstellen von Auftragsschritten" und "Handhaben mehrerer Auftragsschritte" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent-Upgradeprobleme](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  