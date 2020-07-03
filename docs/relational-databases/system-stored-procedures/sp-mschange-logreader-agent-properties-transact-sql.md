---
title: sp_MSchange_logreader_agent_properties (T-SQL)
description: Beschreibt die sp_MSchange_logreader_agent_properties gespeicherte Prozedur, die verwendet wird, um die Eigenschaften des Protokolllese-Agent für eine SQL Server-Replikation Topologie zu ändern.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_logreader_agent_properties_TSQL
- sp_MSchange_logreader_agent_properties
helpviewer_keywords:
- sp_MSchange_logreader_agent_properties
ms.assetid: 925df9d3-a041-4046-8e17-c47f40edb86d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 76a3f657600ed2f8f545dd95c1ba85fa682d51c4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891566"
---
# <a name="sp_mschange_logreader_agent_properties-transact-sql"></a>sp_MSchange_logreader_agent_properties (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Eigenschaften eines Protokolllese-Agent Auftrags, der auf einem Verteiler mit oder einer höheren Version ausgeführt wird [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] . Diese gespeicherte Prozedur wird zum Ändern von Eigenschaften verwendet, wenn der Verleger in einer Instanz von [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ausgeführt wird. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_MSchange_logreader_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Der Sicherheitsmodus, der vom Agent beim Herstellen einer Verbindung mit dem Verleger verwendet wird. *publisher_security_mode* ist vom Datentyp **smallint**und hat keinen Standardwert.  
  
 **0** gibt die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung an.  
  
 **1** gibt die Windows-Authentifizierung an.  
  
`[ @publisher_login = ] 'publisher_login'`Der Anmelde Name, der beim Herstellen einer Verbindung mit dem Verleger verwendet wird. *publisher_login* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. *publisher_login* muss angegeben werden, wenn *publisher_security_mode* den Wert **0**hat. Wenn *publisher_login* NULL und *publisher_security_mode* 1 ist, wird das in *job_login* angegebene Windows-Konto verwendet, wenn **eine**Verbindung mit dem Verleger hergestellt wird.  
  
`[ @publisher_password = ] 'publisher_password'`Das Kennwort, das beim Herstellen einer Verbindung mit dem Verleger verwendet wird. *publisher_password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @job_login = ] 'job_login'`Der Anmelde Name für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_login* ist vom Datentyp **nvarchar (257)** und hat keinen Standardwert. *Dies kann nicht geändert werden für eine nicht-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Verleger.*  
  
`[ @job_password = ] 'job_password'`Das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_type = ] 'publisher_type'`Gibt den Verlegertyp an, wenn der Verleger nicht in einer Instanz von ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . *publisher_type* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**MSSQLSERVER**|Gibt einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger an.|  
|**Orakel**|Gibt einen standardmäßigen Oracle-Verleger an.|  
|**ORACLE GATEWAY**|Gibt einen Oracle Gateway-Verleger an.|  
  
 Weitere Informationen zu den Unterschieden zwischen einem Oracle-Verleger und einem Oracle Gateway-Verleger finden Sie unter [Übersicht über die Oracle-Veröffentlichung](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="remarks"></a>Hinweise  
 **sp_MSchange_logreader_agent_properties** wird bei der Transaktions Replikation verwendet.  
  
 Wenn Sie **sp_MSchange_logreader_agent_properties**ausführen, müssen Sie alle Parameter angeben. Führen Sie [sp_helplogreader_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) aus, um die aktuellen Eigenschaften des Protokolllese-Agent Auftrags zurückzugeben.  
  
 Nach dem Ändern des Anmeldenamens oder Kennworts eines Agents müssen Sie den Agent beenden und neu starten, damit die Änderungen in Kraft treten.  
  
 Wenn der Verleger auf einer Instanz von oder einer höheren [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Version ausgeführt wird, sollten Sie [sp_changelogreader_agent](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md) verwenden, um die Eigenschaften des Protokolllese-Agent zu ändern.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verteiler können **sp_MSchange_logreader_agent_properties**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
