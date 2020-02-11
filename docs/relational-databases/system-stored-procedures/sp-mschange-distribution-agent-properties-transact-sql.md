---
title: sp_MSchange_distribution_agent_properties (T-SQL)
description: Beschreibt die sp_MSchange_distribution_agent_properties gespeicherte Prozedur, die verwendet wird, um die Eigenschaften des Verteilungs-Agent für eine SQL Server-Replikation Topologie zu ändern.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_distribution_agent_properties
- sp_MSchange_distribution_agent_properties_TSQL
helpviewer_keywords:
- sp_MSchange_distribution_agent_properties
ms.assetid: 7dac5e68-bf84-433a-a531-66921f35126f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1a2e2e3c0074c3fcc53298c2556c786c9b7057db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75322268"
---
# <a name="sp_mschange_distribution_agent_properties-transact-sql"></a>sp_MSchange_distribution_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Eigenschaften eines Verteilungs-Agent Auftrags, der auf einem Verteiler [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] mit oder einer höheren Version ausgeführt wird. Diese gespeicherte Prozedur wird zum Ändern von Eigenschaften verwendet, wenn der Verleger in einer Instanz von [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ausgeführt wird. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_MSchange_distribution_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @subscriber = ] 'subscriber'   
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @property = ] 'property'   
        , [ @value = ] 'value' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subscriber_db = ] 'subscriber_db'`Der Name der Abonnement Datenbank. *subscriber_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @property = ] 'property'`Die Veröffentlichungs Eigenschaft, die geändert werden soll. *Property* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @value = ] 'value'`Der neue Eigenschafts Wert. der Wert ist vom Datentyp **nvarchar (524)** und hat den Standard *Wert* NULL.  
  
 Diese Tabelle beschreibt die änderbaren Eigenschaften des Verteilungs-Agent-Auftrags sowie die Einschränkungen für die Werte dieser Eigenschaften.  
  
|Eigenschaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||Anmeldename für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto, unter dem der Agent ausgeführt wird.|  
|**distrib_job_password**||Kennwort für das Windows-Konto, unter dem der Agentauftrag ausgeführt wird.|  
|**subscriber_catalog**||Der Katalog, der beim Herstellen einer Verbindung mit dem OLE DB-Anbieter verwendet werden soll. *Diese Eigenschaft ist nur für nicht--* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Abonnenten gültig.*|  
|**subscriber_datasource**||Name der Datenquelle im vom OLE DB-Anbieter unterstützten Format. *Diese Eigenschaft ist nur für nicht--* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Abonnenten gültig.*|  
|**subscriber_location**||Der Speicherort der Datenbank, wie vom OLE DB Anbieter verstanden. *Diese Eigenschaft ist nur für nicht--* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Abonnenten gültig.*|  
|**subscriber_login**||Anmeldename, der beim Herstellen der Verbindung mit einem Abonnenten zum Synchronisieren des Abonnements verwendet werden soll.|  
|**subscriber_password**||Kennwort des Abonnenten.<br /><br /> [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]|  
|**subscriber_provider**||Eindeutiger Programmbezeichner (PROGID, Programmatic Identifier), mit dem der OLE DB-Anbieter für die Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle registriert wird. *Diese Eigenschaft ist nur für nicht--* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Abonnenten gültig.*|  
|**subscriber_providerstring**||Für den OLE DB-Anbieter spezifische Verbindungszeichenfolge, die die Datenquelle identifiziert. *Diese Eigenschaft ist nur für andere Abonnenten als SQL Server-Abonnenten gültig.*|  
|**subscriber_security_mode**|**1**|Windows-Authentifizierung.<br /><br /> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]|  
||**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Genehmigung.|  
|**subscriber_type**|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Abonnenten|  
||**1**|ODBC-Datenquellenserver|  
||**€**|OLE DB-Anbieter|  
|**SubscriptionStreams**||Bezeichnet die Anzahl zulässiger Verbindungen pro Verteilungs-Agent, um Änderungsbatches parallel auf einen Abonnenten anzuwenden. *Wird für nicht--* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Abonnenten, Oracle-Verleger oder Peer-zu-Peer-Abonnements* nicht unterstützt.|  
  
> [!NOTE]  
>  Nach dem Ändern des Anmeldenamens oder Kennworts eines Agents müssen Sie den Agent beenden und neu starten, damit die Änderungen in Kraft treten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_MSchange_distribution_agent_properties** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 Wenn der Verleger auf einer Instanz von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder einer höheren Version ausgeführt wird, sollten Sie [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md) verwenden, um die Eigenschaften eines Merge-Agent Auftrags zu ändern, der ein Pushabonnement synchronisiert, das auf dem Verteiler ausgeführt wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verteiler können **sp_MSchange_distribution_agent_properties**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addpushsubscription_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)   
 [sp_addsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)  
  
  
