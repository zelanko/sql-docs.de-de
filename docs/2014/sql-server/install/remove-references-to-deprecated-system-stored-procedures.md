---
title: Entfernen von Verweisen auf veraltete gespeicherte System Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system stored procedures [SQL Server]
- system stored procedures [SQL Server]
ms.assetid: 487d24fc-41d5-495e-843c-0ac974ec472f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65e7da666beaf84050dd8d60caf4cac5bfc013c7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036609"
---
# <a name="remove-references-to-deprecated-system-stored-procedures"></a>Entfernen von Verweisen auf veraltete gespeicherte Systemprozeduren
  Upgrade Advisor hat Anweisungen erkannt, die auf nicht dokumentierte gespeicherte Systemprozeduren sowie erweiterte gespeicherte Prozeduren verweisen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht mehr verfügbar sind. Anweisungen, die auf diese Objekte verweisen, schlagen fehl. Verwenden Sie keine nicht dokumentierten Systemobjekte oder APIs, da die Funktionalität in einer späteren Version möglicherweise ohne Vorankündigung geändert oder entfernt wird.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
  
### <a name="documented-system-stored-procedures"></a>Dokumentierte gespeicherte Systemprozeduren  
 Die folgenden dokumentierten gespeicherten Systemprozeduren wurden entfernt:  
  
-   sp_addalias  
  
-   sp_addgroup  
  
-   sp_changegroup  
  
-   sp_dropgroup  
  
-   sp_helpgroup  
  
### <a name="undocumented-system-stored-procedures"></a>Nicht dokumentierte gespeicherte Systemprozeduren  
 Die folgenden nicht dokumentierten gespeicherten Systemprozeduren und erweiterten gespeicherten Prozeduren wurden entfernt:  
  
-   sp_articlesynctranprocs  
  
-   sp_diskdefault  
  
-   sp_EventLog  
  
-   sp_GetMBCSCharLen  
  
-   sp_helplog  
  
-   sp_helpsql  
  
-   sp_IsMBCSLeadByte  
  
-   sp_lock2  
  
-   sp_MSget_current_activity  
  
-   sp_MSset_current_activity  
  
-   sp_MSobjessearch  
  
-   xp_enum_ActiveScriptEngines  
  
-   xp_eventlog  
  
-   xp_GetAdminGroupName  
  
-   xp_GetFileDetails  
  
-   xp_GetLocalSystemAccountName  
  
-   xp_IsNTAdmin  
  
-   xp_MSLocalSystem  
  
-   xp_MSnt2000  
  
-   xp_MSplatform  
  
-   xp_SetSecurity  
  
-   xp_varbintohexstr  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
  
### <a name="documented-system-stored-procedures"></a>Dokumentierte gespeicherte Systemprozeduren  
 Ändern Sie die Anwendungen entsprechend der folgenden Tabelle.  
  
|Statt|Aktion|  
|----------------|-------------|  
|sp_addalias|Ersetzen Sie Aliase durch eine Kombination von Benutzerkonten und Datenbankrollen. Weitere Informationen hierzu finden Sie in den Themen "CREATE USER (Transact-SQL)" und "CREATE ROLE (Transact-SQL)" in der SQL Server-Onlinedokumentation. Entfernen Sie Aliase in aktualisierten Datenbanken mithilfe von sp_dropalias.|  
|sp_addgroupsp_changegroup<br /><br /> sp_dropgroup<br /><br /> sp_helpgroup|Verwenden Sie Rollen. Weitere Informationen finden Sie in den Themen "Rollen auf Serverebene" und "Rollen auf Datenbankebene" in der SQL Server-Onlinedokumentation.|  
  
### <a name="undocmented-system-stored-procedures"></a>Nicht docmentierte gespeicherte System Prozeduren  
 Sie können gespeicherte CLR-Prozeduren mit entsprechender Funktionalität erstellen, um die nicht dokumentierten gespeicherten Systemprozeduren zu ersetzen. Weitere Informationen finden Sie im Thema "CLR-gespeicherte Prozeduren" in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
