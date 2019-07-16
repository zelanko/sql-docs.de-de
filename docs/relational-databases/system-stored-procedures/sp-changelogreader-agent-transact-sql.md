---
title: Sp_changelogreader_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changelogreader_agent
- sp_changelogreader_agent_TSQL
helpviewer_keywords:
- sp_changelogreader_agent
ms.assetid: 929b2fa7-1267-41d0-8b69-e9ab26a62c0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: cfa7196c0ad197a3eb7cb1a31fbdb58e74a78968
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68110819"
---
# <a name="spchangelogreaderagent-transact-sql"></a>sp_changelogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Ändert die Sicherheitseigenschaften eines Protokolllese-Agents. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changelogreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_login = ] 'job_login'` Ist der Anmeldename für das Konto, unter dem der Agent ausgeführt wird. *Job_login* ist **nvarchar(257)** , hat den Standardwert NULL. Verwenden Sie bei Azure SQL-Datenbank verwaltete Instanzen ein SQL Server-Konto. *Dies kann nicht geändert werden, für einen nicht-* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Verleger.*  
  
`[ @job_password = ] 'job_password'` Ist das Kennwort für das Konto, unter dem der Agent ausgeführt wird. *Job_password* ist **Sysname**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Der Sicherheitsmodus wird vom Agent verwendet werden, Herstellen der Verbindung mit dem Verleger. *Publisher_security_mode* ist **Smallint**, hat den Standardwert NULL. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung und **1** gibt die Windows-Authentifizierung.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Der Benutzername, der verwendet wird, Herstellen der Verbindung mit dem Verleger. *Publisher_login* ist **Sysname**, hat den Standardwert NULL. *Publisher_login* muss angegeben werden, wenn *Publisher_security_mode* ist **0**. Wenn *Publisher_login* ist NULL und *Publisher_security_mode* ist **1**, und klicken Sie dann das angegebene Windows-Konto *Job_login* wird verwendet, wenn Herstellen einer Verbindung mit dem Verleger.  
  
`[ @publisher_password = ] 'publisher_password'` Das Kennwort wird verwendet werden, wenn eine Verbindung mit dem Verleger herstellen. *Publisher_password* ist **Sysname**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter wird nur für Nicht-SQL Server-Verleger unterstützt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changelogreader_agent** wird in Transaktionsreplikationen verwendet.  
  
 **Sp_changelogreader_agent** wird verwendet, um das Windows-Konto zu ändern, unter dem ein Protokolllese-Agent ausgeführt wird. Sie können das Kennwort für einen vorhandenen Windows-Anmeldenamen ändern oder einen neuen Windows-Anmeldenamen und ein neues Kennwort angeben.  
  
 Nach dem Ändern des Anmeldenamens oder Kennworts eines Agents müssen Sie den Agent beenden und neu starten, damit die Änderungen in Kraft treten.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_changelogreader_agent**.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern von Replikationssicherheitseinstellungen](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_helplogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md)   
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
