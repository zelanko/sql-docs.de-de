---
title: sp_helpsubscription_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpsubscription_properties
- sp_helpsubscription_properties_TSQL
helpviewer_keywords:
- sp_helpsubscription_properties
ms.assetid: 7a76a645-97eb-47ac-b3ea-e2d75012cbed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28305f4676c9323b364703feb0b668615a159e6b
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771565"
---
# <a name="sphelpsubscriptionproperties-transact-sql"></a>sp_helpsubscription_properties (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ruft Sicherheitsinformationen aus der [MSsubscription_properties](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) -Tabelle ab. Diese gespeicherte Prozedur wird auf dem Abonnenten ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpsubscription_properties [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db =] 'publisher_db' ]   
    [ , [ @publication =] 'publication' ]  
    [ , [ @publication_type = ] publication_type ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert, mit dem Informationen zu allen Verlegern zurückgegeben werden.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Verleger Datenbank. *publisher_db* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert, mit dem Informationen zu allen Verleger Datenbanken zurückgegeben werden.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert, mit dem Informationen zu allen Veröffentlichungen zurückgegeben werden.  
  
`[ @publication_type = ] publication_type`Der Typ der Veröffentlichung. *publication_type* ist vom Datentyp **int**und hat den Standardwert NULL. Wenn angegeben, muss *publication_type* einer der folgenden Werte sein:  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Transaktionsveröffentlichung|  
|**1**|Momentaufnahmeveröffentlichung|  
|**2**|Mergeveröffentlichung|  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Name des Verlegers.|  
|**publisher_db**|**sysname**|Name der Verlegerdatenbank.|  
|**publication**|**sysname**|Name der Veröffentlichung.|  
|**publication_type**|**int**|Typ der Veröffentlichung:<br /><br /> **0** = transaktional<br /><br /> **1** = Momentaufnahme<br /><br /> **2** = zusammenführen|  
|**publisher_login**|**sysname**|Auf dem Verleger für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendete Anmelde-ID.|  
|**publisher_password**|**nvarchar(524)**|Das Kennwort, das auf dem Verleger für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendet wird (verschlüsselt).|  
|**publisher_security_mode**|**int**|Auf dem Verleger verwendeter Sicherheitsmodus:<br /><br /> 0 =  -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung<br /><br /> **1** = Windows-Authentifizierung|  
|**distributor**|**sysname**|Name des Verteilers.|  
|**distributor_login**|**sysname**|Verteilerbenutzername.|  
|**distributor_password**|**nvarchar(524)**|Verteilerkennwort (verschlüsselt).|  
|**distributor_security_mode**|**int**|Auf dem Verteiler verwendeter Sicherheitsmodus:<br /><br /> 0 =  -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung<br /><br /> **1** = Windows-Authentifizierung|  
|**ftp_address**|**sysname**|Nur aus Gründen der Abwärtskompatibilität beibehalten Die Netzwerkadresse des FTP-Dienstes für den Verteiler.|  
|**ftp_port**|**int**|Nur aus Gründen der Abwärtskompatibilität beibehalten Die Nummer des Anschlusses für den FTP-Dienst des Verteilers.|  
|**ftp_login**|**sysname**|Nur aus Gründen der Abwärtskompatibilität beibehalten Der Benutzername, mit dem eine Verbindung mit dem FTP-Dienst hergestellt wird.|  
|**ftp_password**|**nvarchar(524)**|Nur aus Gründen der Abwärtskompatibilität beibehalten Benutzer Kennwort, das zum Herstellen einer Verbindung mit dem FTP-Dienst verwendet|  
|**alt_snapshot_folder**|**nvarchar(255)**|Gibt den Speicherort des anderen Ordners für die Momentaufnahme an.|  
|**working_directory**|**nvarchar(255)**|Der Name des Arbeitsverzeichnisses, das zum Speichern der Daten- und Schemadateien verwendet wird.|  
|**use_ftp**|**bit**|Gibt anstelle des normalen Protokolls FTP an, um Momentaufnahmen abzurufen. Bei **einem**Wert von 1 wird FTP verwendet.|  
|**dts_package_name**|**sygleich**|Gibt den Namen des DTS-Pakets (Data Transformation Services) an.|  
|**dts_package_password**|**nvarchar(524)**|Gibt gegebenenfalls das Kennwort des Pakets an.|  
|**dts_package_location**|**int**|Speicherort, an dem das DTS-Paket gespeichert wird.<br /><br /> **0** = der Speicherort des Pakets befindet sich auf dem Verteiler.<br /><br /> **1** = der Speicherort des Pakets befindet sich auf dem Abonnenten.|  
|**offload_agent**|**bit**|Gibt an, ob der Agent remote aktiviert werden kann. Wenn der Wert **0**ist, kann der Agent nicht remote aktiviert werden.|  
|**offload_server**|**sysname**|Gibt den Netzwerknamen des Servers an, der für die Remoteaktivierung verwendet wird.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Gibt den Pfad zum Ordner an, in dem die Momentaufnahmedateien gespeichert werden.|  
|**use_web_sync**|**bit**|Gibt an, ob das Abonnement über HTTPS synchronisiert werden kann, wobei der Wert **1** bedeutet, dass diese Funktion aktiviert ist.|  
|**internet_url**|**nvarchar(260)**|URL, die den Speicherort des Replikations-Listener für die Websynchronisierung darstellt.|  
|**internet_login**|**nvarchar(128)**|Der Anmeldename, der vom Merge-Agent zum Herstellen einer Verbindung mit dem Webserver verwendet wird, der die Websynchronisierung mithilfe der Standardauthentifizierung hostet.|  
|**internet_password**|**nvarchar(524)**|Das Kennwort für den Anmeldenamen, der vom Merge-Agent zum Herstellen einer Verbindung mit dem Webserver verwendet wird, der die Websynchronisierung mithilfe der Standardauthentifizierung hostet.|  
|**internet_security_mode**|**int**|Der Authentifizierungsmodus, der beim Herstellen einer Verbindung mit dem Webserver verwendet wird, der die Websynchronisierung verwendet. der Wert **1** steht für die Windows-Authentifizierung und der Wert **0** für die Standard Authentifizierung.|  
|**internet_timeout**|**int**|Zeit in Sekunden, bevor eine Anforderung für eine Websynchronisierung abläuft.|  
|**hostname**|**nvarchar(128)**|Gibt den Wert für HOST_NAME() an, wenn diese Funktion in der WHERE-Klausel eines parametrisierten Zeilenfilters verwendet wird.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helpsubscription_properties** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_helpsubscription_properties**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
