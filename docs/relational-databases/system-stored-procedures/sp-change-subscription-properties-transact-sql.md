---
title: sp_change_subscription_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_subscription_properties_TSQL
- sp_change_subscription_properties
helpviewer_keywords:
- sp_change_subscription_properties
ms.assetid: cf8137f9-f346-4aa1-ae35-91a2d3c16f17
author: stevestein
ms.author: sstein
ms.openlocfilehash: e033e446fc771ad87542474edb1e90caf08faebd
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528784"
---
# <a name="sp_change_subscription_properties-transact-sql"></a>sp_change_subscription_properties (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Aktualisiert Informationen für Pullabonnements. Diese gespeicherte Prozedur wird auf dem Abonnenten in der Abonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_change_subscription_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @property = ] 'property'  
        , [ @value = ] 'value'  
    [ , [ @publication_type = ] publication_type ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist **sysname**, ohne Standard.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Publisher-Datenbank. *publisher_db* ist **sysname**, ohne Standardeinstellung.  
  
`[ @publication = ] 'publication'`Der Name der Publikation. *Publikation* ist **sysname**, ohne Standard.  
  
`[ @property = ] 'property'`Die zu ändernde Eigenschaft. *Eigenschaft* ist **sysname**.  
  
`[ @value = ] 'value'`Der neue Wert der Eigenschaft. *Wert* ist **nvarchar(1000)**, ohne Standardwert.  
  
`[ @publication_type = ] publication_type`Gibt den Replikationstyp der Publikation an. *publication_type* ist **int**und kann einer dieser Werte sein.  
  
|Wert|Veröffentlichungstyp|  
|-----------|----------------------|  
|**0**|Transaktionsreplikation|  
|**1**|Momentaufnahme|  
|**2**|Merge|  
|NULL (Standard)|Die Replikation bestimmt den Veröffentlichungstyp. Da die gespeicherte Prozedur mehrere Tabellen durchsuchen muss, ist diese Option langsamer, als wenn der genaue Veröffentlichungstyp angegeben wird.|  
  
 Diese Tabelle beschreibt die Eigenschaften von Artikeln und die Werte für diese Eigenschaften.  
  
|Eigenschaft|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**alt_snapshot_folder**||Gibt den Speicherort des anderen Ordners für die Momentaufnahme an. Wenn NULL festgelegt ist, werden die Momentaufnahmedateien aus dem vom Verleger angegebenen Standardspeicherort übernommen.|  
|**distrib_job_login**||Anmeldename für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto, unter dem der Agent ausgeführt wird.|  
|**distrib_job_password**||Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird.|  
|**distributor_login**||Verteilerbenutzername.|  
|**distributor_password**||Verteilerkennwort.|  
|**distributor_security_mode**|**1**|Verwendet die Windows-Authentifizierung beim Herstellen der Verbindung mit dem Verteiler.|  
||**0**|Verwendet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung beim Herstellen der Verbindung mit dem Verteiler.|  
|**dts_package_name**||Gibt den Namen des SQL Server 2000 DTS-Pakets (Data Transformation Services) an. Dieser Wert kann nur bei einer Transaktions- oder Momentaufnahmeveröffentlichung angegeben werden.|  
|**dts_package_password**||Gibt das Kennwort für das Paket an. *dts_package_password* ist **sysname** mit dem Standardwert NULL, der angibt, dass die kennwortüberlegt bleiben soll.<br /><br /> Hinweis: Ein DTS-Paket muss über ein Kennwort verfügen.<br /><br /> Dieser Wert kann nur bei einer Transaktions- oder Momentaufnahmeveröffentlichung angegeben werden.|  
|**dts_package_location**||Speicherort, an dem das DTS-Paket gespeichert ist. Dieser Wert kann nur bei einer Transaktions- oder Momentaufnahmeveröffentlichung angegeben werden.|  
|**dynamic_snapshot_location**||Gibt den Pfad zum Ordner an, in dem die Momentaufnahmedateien gespeichert werden. Dieser Wert kann nur bei einer Mergeveröffentlichung angegeben werden.|  
|**ftp_address**||Nur aus Gründen der Abwärtskompatibilität beibehalten|  
|**ftp_login**||Nur aus Gründen der Abwärtskompatibilität beibehalten|  
|**ftp_password**||Nur aus Gründen der Abwärtskompatibilität beibehalten|  
|**ftp_port**||Nur aus Gründen der Abwärtskompatibilität beibehalten|  
|**Hostname**||Hostname, der beim Herstellen der Verbindung mit dem Verleger verwendet wird.|  
|**internet_login**||Der Anmeldename, der vom Merge-Agent zum Herstellen einer Verbindung mit dem Webserver verwendet wird, der die Websynchronisierung mithilfe der Standardauthentifizierung hostet.|  
|**internet_password**||Das vom Merge-Agent verwendete Kennwort für die Herstellung einer Verbindung mit dem Webserver, der die Websynchronisierung hostet, wobei die Verbindung über die Standardauthentifizierung erfolgt.|  
|**internet_security_mode**|**1**|Verwendet für die Websynchronisierung die integrierte Windows-Authentifizierung. Wir empfehlen, bei der Websynchronisierung die Standardauthentifizierung zu verwenden. Weitere Informationen finden Sie unter [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).|  
||**0**|Verwendet für die Websynchronisierung die Standardauthentifizierung.<br /><br /> Hinweis: Für die Websynchronisierung ist eine TLS-Verbindung zum Webserver erforderlich.|  
|**internet_timeout**||Zeit in Sekunden, bevor eine Anforderung für eine Websynchronisierung abläuft.|  
|**internet_url**||URL, die den Speicherort des Replikationslisteners für die Websynchronisierung darstellt.|  
|**merge_job_login**||Anmeldename für das Windows-Konto, unter dem der Agent ausgeführt wird.|  
|**merge_job_password**||Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird.|  
|**publisher_login**||Der Benutzername des Verlegers. Das Ändern *publisher_login* wird nur für Abonnements zum Zusammenführen von Publikationen unterstützt.|  
|**publisher_password**||Publisher-Kennwort. Das Ändern *publisher_password* wird nur für Abonnements zum Zusammenführen von Publikationen unterstützt.|  
|**publisher_security_mode**|**1**|Verwendung der Windows-Authentifizierung für die Verbindung mit dem Verleger. Das Ändern *publisher_security_mode* wird nur für Abonnements zum Zusammenführen von Publikationen unterstützt.|  
||**0**|Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung für die Verbindung mit dem Verleger.|  
|**use_ftp**|**true**|Verwendet FTP anstelle des regulären Protokolls zum Abrufen von Momentaufnahmen.|  
||**false**|Verwendet das reguläre Protokoll zum Abrufen von Momentaufnahmen.|  
|**use_web_sync**|**true**|Aktiviert die Websynchronisierung.|  
||**false**|Deaktiviert die Websynchronisierung.|  
|**working_directory**||Name des Arbeitsverzeichnisses für die temporäre Speicherung von Daten und Schemadateien für die Veröffentlichung, wenn für das Übertragen von Momentaufnahmedateien FTP (File Transfer Protocol) verwendet wird.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_change_subscription_properties** wird in allen Replikationstypen verwendet.  
  
 **sp_change_subscription_properties** wird für Pullabonnements verwendet.  
  
 Bei Oracle Publishers wird der Wert von *publisher_db* ignoriert, da Oracle nur eine Datenbank pro Instanz des Servers zulässt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **sysadmin** Fixed Server-Rolle oder **db_owner** feste Datenbankrolle können **sp_change_subscription_properties**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Pullabonnementeigenschaften](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_addmergepullsubscription_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_addpullsubscription &#40;transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_addpullsubscription_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
