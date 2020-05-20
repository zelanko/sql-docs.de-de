---
title: sp_changesubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- changesubscription
- sp_changesubscription
- changesubscription_TSQL
- sp_changesubscription_TSQL
helpviewer_keywords:
- sp_changesubscription
ms.assetid: f9d91fe3-47cf-4915-b6bf-14c9c3d8a029
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c88e0f545a19c1f486c5c6927c11fd2707112963
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824091"
---
# <a name="sp_changesubscription-transact-sql"></a>sp_changesubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ändert die Eigenschaften eines Momentaufnahme- oder Transaktionspushabonnements bzw. eines Pullabonnements, das an einem verzögerten Update über eine Warteschlange beteiligt ist. Verwenden Sie [sp_change_subscription_properties &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), um die Eigenschaften aller anderen Typen von Pullabonnements zu ändern. **sp_changesubscription** wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changesubscription [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
        , [ @property = ] 'property'  
        , [ @value = ] 'value'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der zu ändernden Veröffentlichung. *Publication*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert  
  
`[ @article = ] 'article'`Der Name des Artikels, der geändert werden soll. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @destination_db = ] 'destination_db'`Der Name der Abonnement Datenbank. *destination_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @property = ] 'property'`Die Eigenschaft, die für das angegebene Abonnement geändert werden soll. die *Eigenschaft* ist vom Datentyp **nvarchar (30)**, und es kann sich um einen der Werte in der Tabelle handeln.  
  
`[ @value = ] 'value'`Der neue Wert für die angegebene *Eigenschaft*. der Wert ist vom Datentyp **nvarchar (4000)**. der *Wert* kann einer der Werte in der Tabelle sein.  
  
|Eigenschaft|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||Anmeldename für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto, unter dem der Agent ausgeführt wird.|  
|**distrib_job_password**||Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird.|  
|**subscriber_catalog**||Der Katalog, der beim Herstellen einer Verbindung mit dem OLE DB-Anbieter verwendet werden soll. Diese Eigenschaft ist nur für nicht-- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten gültig.|  
|**subscriber_datasource**||Name der Datenquelle im vom OLE DB-Anbieter unterstützten Format. *Diese Eigenschaft ist nur gültig für nicht-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Abonnenten.*|  
|**subscriber_location**||Der Speicherort der Datenbank, wie vom OLE DB Anbieter verstanden. *Diese Eigenschaft ist nur gültig für nicht-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Abonnenten.*|  
|**subscriber_login**||Anmeldename auf dem Abonnenten.|  
|**subscriber_password**||Sicheres Kennwort für den angegebenen Anmeldenamen.|  
|**subscriber_security_mode**|**1**|Verwendung der Windows-Authentifizierung für die Verbindung mit dem Abonnenten.|  
||**0**|Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung für die Verbindung mit dem Abonnenten.|  
|**subscriber_provider**||Eindeutiger Programmbezeichner (PROGID, Programmatic Identifier), mit dem der OLE DB-Anbieter für die Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle registriert wird. *Diese Eigenschaft ist nur gültig für nicht-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Abonnenten.*|  
|**subscriber_providerstring**||Für den OLE DB-Anbieter spezifische Verbindungszeichenfolge, die die Datenquelle identifiziert. *Diese Eigenschaft ist nur gültig für nicht-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Abonnenten.*|  
|**SubscriptionStreams**||Die pro Verteilungs-Agent zulässige Anzahl von Verbindungen, um Batches von Änderungen parallel auf einen Abonnenten anzuwenden. Für Verleger wird ein Wertebereich zwischen **1** und **64** unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Diese Eigenschaft muss für **0** nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten, Oracle-Verleger oder Peer-zu-Peer-Abonnements den Wert 0 aufweisen.|  
|**subscriber_type**|**1**|ODBC-Datenquellenserver|  
||**3**|OLE DB-Anbieter|  
|**memory_optimized**|**bit**|Gibt an, dass das Abonnement Speicher optimierte Tabellen unterstützt. *memory_optimized* ist " **Bit**", wobei "1" true ist (das Abonnement unterstützt Speicher optimierte Tabellen).|  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* darf nicht für einen Verleger angegeben werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_changesubscription** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 **sp_changesubscription** können nur zum Ändern der Eigenschaften von Pushabonnements oder Pullabonnements verwendet werden, die an einer verzögertem Update-Transaktions Replikation beteiligt sind. Verwenden Sie [sp_change_subscription_properties &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), um die Eigenschaften aller anderen Typen von Pullabonnements zu ändern.  
  
 Nach dem Ändern des Anmeldenamens oder Kennworts eines Agents müssen Sie den Agent beenden und neu starten, damit die Änderungen in Kraft treten.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_changesubscription**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
