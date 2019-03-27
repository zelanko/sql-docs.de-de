---
title: Sp_changemergepullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergepullsubscription
- sp_changemergepullsubscription_TSQL
helpviewer_keywords:
- sp_changemergepullsubscription
ms.assetid: 5e0d04f2-6175-44a2-ad96-a8e2986ce4c9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cf650c095e27fe3a270ad9610e959bd6f5f1a6a3
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493112"
---
# <a name="spchangemergepullsubscription-transact-sql"></a>sp_changemergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Eigenschaften des Mergepullabonnements. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changemergepullsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @publisher= ] 'publisher' ]  
    [ , [ @publisher_db= ] 'publisher_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert %.  
  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher*ist **Sysname**, hat den Standardwert %.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Verlegerdatenbank. *Publisher_db*ist **Sysname**, hat den Standardwert %.  
  
`[ @property = ] 'property'` Ist der Name des zu ändernden Eigenschaft. *Eigenschaft* ist **Sysname**, und kann einen der Werte in der Tabelle.  
  
`[ @value = ] 'value'` Ist der neue Wert für die angegebene Eigenschaft. *Wert*ist **nvarchar(255)**, und kann einen der Werte in der Tabelle.  
  
|Eigenschaft|Wert|Description|  
|--------------|-----------|-----------------|  
|**alt_snapshot_folder**||Speicherort des momentaufnahmeordners ist der Speicherort nur oder darüber hinaus am Standardspeicherort.|  
|**description**||Die Beschreibung dieses Mergepullabonnements.|  
|**distributor**||Name des Verteilers.|  
|**distributor_login**||Die Anmelde-ID, die auf dem Verteiler für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendet wird.|  
|**distributor_password**||Kennwort (verschlüsselt) verwendet, auf dem Verteiler für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**distributor_security_mode**|**1**|Verwendet die Windows-Authentifizierung beim Herstellen der Verbindung mit dem Verteiler.|  
||**0**|Verwendet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung beim Herstellen der Verbindung mit dem Verteiler.|  
|**dynamic_snapshot_location**||Pfad zu dem Ordner, in dem die Momentaufnahmedateien gespeichert sind.|  
|**ftp_address**||Nur aus Gründen der Abwärtskompatibilität verfügbar. Ist die Netzwerkadresse des Protokolls FTP (File Transfer)-Diensts für den Verteiler.|  
|**ftp_login**||Nur aus Gründen der Abwärtskompatibilität verfügbar. Der Benutzername wird für die Verbindung mit dem FTP-Dienst verwendet werden.|  
|**ftp_password**||Nur aus Gründen der Abwärtskompatibilität verfügbar. Das Benutzerkennwort, mit dem eine Verbindung zum FTP-Dienst hergestellt wird.|  
|**ftp_port**||Nur aus Gründen der Abwärtskompatibilität verfügbar. Die Anschlussnummer des FTP-Diensts für den Verteiler.|  
|**hostname**||Gibt einen Wert für HOST_NAME() an, wenn diese Funktion in der WHERE-Klausel eines Joinfilters oder einer logischen Datensatzbeziehung verwendet wird.|  
|**internet_login**||Der Anmeldename, der vom Merge-Agent zum Herstellen einer Verbindung mit dem Webserver verwendet wird, der die Websynchronisierung mithilfe der Standardauthentifizierung hostet.|  
|**internet_password**||Das Kennwort für den Anmeldenamen, der vom Merge-Agent zum Herstellen einer Verbindung mit dem Webserver verwendet wird, der die Websynchronisierung mithilfe der Standardauthentifizierung hostet.|  
|**internet_security_mode**|**1**|Verwendet die Windows-Authentifizierung, wenn eine Verbindung mit dem Webserver hergestellt wird, der die Websynchronisierung hostet.|  
||**0**|Verwendet die Standardauthentifizierung, wenn eine Verbindung mit dem Webserver hergestellt wird, der die Websynchronisierung hostet.|  
|**internet_timeout**||Zeit in Sekunden, bevor eine Anforderung für eine Websynchronisierung abläuft.|  
|**internet_url**||URL, die den Speicherort der replikationsüberwachung für die websynchronisierung darstellt.|  
|**merge_job_login**||Anmeldename für das Windows-Konto, unter dem der Agent ausgeführt wird.|  
|**merge_job_password**||Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird.|  
|**priority**||Verfügbar nur für Abwärtskompatibilität. Führen Sie [Sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md) auf dem Verleger stattdessen zum Ändern der Priorität eines Abonnements.|  
|**publisher_login**||Auf dem Verleger für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendete Anmelde-ID.|  
|**publisher_password**||Das Kennwort (verschlüsselt), das auf dem Verleger für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendet wird.|  
|**publisher_security_mode**|**0**|Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung für die Verbindung mit dem Verleger.|  
||**1**|Verwendung der Windows-Authentifizierung für die Verbindung mit dem Verleger.|  
||**2**|Synchronisierungstrigger verwenden einen statischen **Sysservers** Eintrag zu den Remoteprozeduraufruf (RPC), und der Verleger muss definiert werden, der **Sysservers** -Tabelle als Remoteserver oder Verbindungsserver.|  
|**sync_type**|**automatic**|Das Schema und die Ausgangsdaten für veröffentlichte Tabellen werden zuerst an den Abonnenten übertragen.|  
||**Keine**|Der Abonnent verfügt bereits über das Schema und die Ausgangsdaten für veröffentlichte Tabellen; Systemtabellen und Daten werden immer übertragen.|  
|**use_ftp**|**true**|FTP wird anstelle des normalen Protokolls zum Abrufen von Momentaufnahmen verwendet.|  
||**false**|Das normale Protokoll wird zum Abrufen von Momentaufnahmen verwendet.|  
|**use_web_sync**|**true**|Das Abonnement kann über HTTP synchronisiert werden.|  
||**false**|Das Abonnement kann über HTTP nicht synchronisiert werden.|  
|**use_interactive_resolver**|**true**|Der interaktive Konfliktlöser wird während der Konfliktlösung verwendet.|  
||**false**|Der interaktive Konfliktlöser wird nicht verwendet.|  
|**working_directory**||Der vollqualifizierte Pfad zum Verzeichnis, in das die Momentaufnahmedateien mithilfe von FTP übertragen werden, wenn diese Option angegeben ist.|  
|NULL (Standard)||Gibt die Liste der unterstützten Werte für *Eigenschaft*.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changemergepullsubscription** wird bei der Mergereplikation verwendet.  
  
 Der aktuelle Server und die aktuelle Datenbank werden als Abonnent und Abonnentendatenbank angenommen.  
  
 Nach dem Ändern des Anmeldenamens oder Kennworts eines Agents müssen Sie den Agent beenden und neu starten, damit die Änderungen in Kraft treten.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_changemergepullsubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Eigenschaften von Pullabonnements](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
