---
title: sp_changereplicationserverpasswords (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changereplicationserverpasswords_TSQL
- sp_changereplicationserverpasswords
helpviewer_keywords:
- sp_changereplicationserverpasswords
ms.assetid: 9333da96-3a1c-4adb-9a74-5dac9ce596df
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9feddab12ea972ea4d7764fccfdd91a7f9b89cec
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68762252"
---
# <a name="sp_changereplicationserverpasswords-transact-sql"></a>sp_changereplicationserverpasswords (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ändert gespeicherte Kenn Wörter für [!INCLUDE[msCoName](../../includes/msconame-md.md)] das Windows- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konto oder den-Anmelde Namen, die von Replikations-Agents verwendet werden, wenn eine Verbindung mit Servern in einer Normalerweise müssten Sie das Kennwort für jeden einzelnen Agent ändern, der auf dem Server ausgeführt wird, und zwar selbst dann, wenn alle Agents den gleichen Anmeldenamen oder das gleiche Konto verwenden. Diese gespeicherte Prozedur ermöglicht Ihnen die Änderung des Kennworts für alle Instanzen eines gegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamens oder Windows-Kontos, der bzw. das von allen auf einem Server ausgeführten Replikations-Agents verwendet wird. Die gespeicherte Prozedur wird auf jedem Server in der Replikationstopologie der master-Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changereplicationserverpasswords [ @login_type = ] login_type  
        , [ @login = ] 'login'   
        , [ @password = ] 'password'  
    [ , [ @server = ] 'server' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @login_type = ] login_type`Der Authentifizierungstyp für die angegebenen Anmelde Informationen. *LOGIN_TYPE* ist vom Datentyp **tinyint**und hat keinen Standardwert.  
  
 **1** = integrierte Windows-Authentifizierung  
  
 **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung  
  
`[ @login = ] 'login'`Der Name des Windows-Kontos oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Anmelde Name, der geändert wird. *Login* ist vom Datentyp **nvarchar (257)** und hat keinen Standardwert.  
  
`[ @password = ] 'password'`Das neue Kennwort, das für den angegebenen *Anmelde*Namen gespeichert werden soll. *Password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
> [!NOTE]  
>  Nachdem Sie ein Replikationskennwort geändert haben, müssen Sie jeden Agent, der dieses Kennwort verwendet, beenden und neu starten, damit die Änderung für diesen Agent in Kraft tritt.  
  
`[ @server = ] 'server'`Die Server Verbindung, für die das gespeicherte Kennwort geändert wird. der *Server* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Verleih**|Alle Agentverbindungen zum Verteiler|  
|**Gebers**|Alle Agentverbindungen zum Verleger|  
|**Abonnenten**|Alle Agentverbindungen zum Abonnenten|  
|**%** vorgegebene|Alle Agentverbindungen zu allen Servern in einer Replikationstopologie|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_changereplicationserverpasswords** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_changereplicationserverpasswords**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Replikations Sicherheitseinstellungen](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
