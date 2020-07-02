---
title: sp_addpushsubscription_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/09/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpushsubscription_agent_TSQL
- sp_addpushsubscription_agent
helpviewer_keywords:
- sp_addpushsubscription_agent
ms.assetid: 1fdd2052-50d8-4318-8aa7-fc635d5cad18
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f9ff6619109e198a50d15c21aecbe958a6183d2d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716467"
---
# <a name="sp_addpushsubscription_agent-transact-sql"></a>sp_addpushsubscription_agent (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Fügt einen neuen geplanten Agentauftrag hinzu, der zum Synchronisieren eines Pushabonnements mit einer Transaktionsveröffentlichung verwendet wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addpushsubscription_agent [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @job_name = ] 'job_name' ]   
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @distribution_job_name = ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @subscriber_provider = ] 'subscriber_provider' ]   
    [ , [ @subscriber_datasrc = ] 'subscriber_datasrc' ]   
    [ , [ @subscriber_location = ] 'subscriber_location' ]  
    [ , [ @subscriber_provider_string = ] 'subscriber_provider_string' ]   
    [ , [ @subscriber_catalog = ] 'subscriber_catalog' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'`Der Name der Abonnenten Instanz oder der Name des Verfügbarkeits Gruppen-Listener, wenn die Abonnenten Datenbank eine Verfügbarkeits Gruppe ist. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. 

> [!NOTE]
> Der Server Name kann als angegeben werden `<Hostname>,<PortNumber>` . Möglicherweise müssen Sie die Portnummer für die Verbindung angeben, wenn SQL Server unter Linux oder Windows mit einem benutzerdefinierten Port bereitgestellt wird und der-Browser Dienst deaktiviert ist.

`[ @subscriber_db = ] 'subscriber_db'`Der Name der Abonnement Datenbank. *subscriber_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Geben Sie für einen nicht-SQL Server Abonnenten den Wert **(Standardziel)** für *subscriber_db*an.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode`Der Sicherheitsmodus, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Abonnenten verwendet wird. *subscriber_security_mode* ist vom Datentyp **int**und hat den Standardwert 1. **0** gibt die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung an. **1** gibt die Windows-Authentifizierung an.  
  
> [!IMPORTANT]  
>  Bei Abonnements mit verzögertem Update über eine Warteschlange verwenden Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung für Verbindungen mit Abonnenten. Geben Sie für die Verbindung zu den einzelnen Abonnenten jeweils ein anderes Konto an. Verwenden Sie für alle anderen Abonnements die Windows-Authentifizierung.  
  
`[ @subscriber_login = ] 'subscriber_login'`Der Anmelde Name des Abonnenten, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Abonnenten verwendet wird. *subscriber_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subscriber_password = ] 'subscriber_password'`Das Kennwort des Abonnenten. *subscriber_password* ist erforderlich, wenn *subscriber_security_mode* auf **0**festgelegt ist. *subscriber_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Bei Verwendung eines Abonnentenkennworts wird dieses automatisch verschlüsselt.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @job_login = ] 'job_login'`Der Anmelde Name für das Konto, unter dem der Agent ausgeführt wird. Verwenden Sie auf verwaltete Azure SQL-Datenbank-Instanz ein SQL Server Konto. *job_login* ist vom Datentyp **nvarchar (257)** und hat den Standardwert NULL. Dieses Windows-Konto wird immer für Agentverbindungen mit dem Verteiler und für Verbindungen mit dem Abonnenten verwendet, wenn die integrierte Windows-Authentifizierung verwendet wird.  
  
`[ @job_password = ] 'job_password'`Das Kennwort für das Konto, unter dem der Agent ausgeführt wird. *job_password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @job_name = ] 'job_name'`Der Name eines vorhandenen Agentauftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter wird nur angegeben, wenn das Abonnement mithilfe eines vorhandenen Auftrags statt mit einem neu erstellten Auftrag (Standard) synchronisiert wird. Wenn Sie kein Mitglied der festen Server Rolle **sysadmin** sind, müssen Sie *job_login* und *job_password* angeben, wenn Sie *job_name*angeben.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der die Verteilungs-Agent geplant werden soll. *frequency_type* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|On-Demand-Streaming|  
|**4**|Täglich|  
|**8**|Wöchentlich|  
|**16**|Monatlich|  
|**32**|Monatlich, relativ|  
|**64** (Standard)|Autostart|  
|**128**|Wiederholt|  
  
> [!NOTE]  
>  Das Angeben des Werts **64** bewirkt, dass die Verteilungs-Agent im kontinuierlichen Modus ausgeführt wird. Dies entspricht dem Festlegen des **-Continuous-** Parameters für den Agent. Weitere Informationen finden Sie unter [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
`[ @frequency_interval = ] frequency_interval`Der Wert, der auf die von *frequency_type*festgelegte Häufigkeit angewendet werden soll. *frequency_interval* ist vom Datentyp **int**und hat den Standardwert 1.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Datum der Verteilungs-Agent. Dieser Parameter wird verwendet, wenn *frequency_type* auf **32** (monatlich, relativ) festgelegt ist. *frequency_relative_interval* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1** (Standard)|First|  
|**2**|Second|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Last (Letzter)|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert 0.  
  
`[ @frequency_subday = ] frequency_subday`Gibt an, wie oft innerhalb des definierten Zeitraums neu geplant werden soll. *frequency_subday* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|Second|  
|**4** (Standard)|Minute|  
|**8**|Stunde|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Das Intervall für die *frequency_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert 5.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der die Verteilungs-Agent zum ersten Mal geplant ist. dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert 0.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der die Verteilungs-Agent nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert 235959.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem die Verteilungs-Agent zum ersten Mal geplant ist, formatiert als YYYYMMDD. *active_start_date* ist vom Datentyp **int**und hat den Standardwert 0.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Verteilungs-Agent nicht mehr geplant ist, formatiert als YYYYMMDD. *active_end_date* ist vom Datentyp **int**und hat den Standardwert 99991231.  
  
`[ @dts_package_name = ] 'dts_package_name'`Gibt den Namen des DTS-Pakets (Data Transformation Services) an. *dts_package_name* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL. Zum Angeben des Paketnamens `DTSPub_Package` wird beispielsweise der `@dts_package_name = N'DTSPub_Package'`-Parameter verwendet.  
  
`[ @dts_package_password = ] 'dts_package_password'`Gibt das Kennwort an, das zum Ausführen des Pakets erforderlich ist. *dts_package_password* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Wenn *dts_package_name* angegeben ist, müssen Sie ein Kennwort angeben.  
  
`[ @dts_package_location = ] 'dts_package_location'`Gibt den Speicherort des Pakets an. *dts_package_location* ist vom Datentyp **nvarchar (12)** und hat den Standardwert Distributor. Der Speicherort des Pakets kann **Distributor** oder **Subscriber**sein.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'`Gibt an, ob das Abonnement über den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Synchronisierungs-Manager synchronisiert werden kann. *enabled_for_syncmgr* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. Wenn der Wert **false**ist, wird das Abonnement nicht bei der Synchronisierungs Verwaltung registriert. Wenn der Wert **true**ist, wird das Abonnement bei der Synchronisierungs Verwaltung registriert und kann synchronisiert werden, ohne zu starten [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
`[ @distribution_job_name = ] 'distribution_job_name'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subscriber_provider = ] 'subscriber_provider'`Der eindeutige Programm Bezeichner (ProgID), mit dem der OLE DB-Anbieter für die nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquelle registriert wird. *subscriber_provider* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. *subscriber_provider* muss für den OLE DB Anbieter, der auf dem Verteiler installiert ist, eindeutig sein. *subscriber_provider* wird nur für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten unterstützt.  
  
`[ @subscriber_datasrc = ] 'subscriber_datasrc'`Der Name der Datenquelle, wie er vom OLE DB-Anbieter interpretiert wird. *subscriber_datasrc* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL. *subscriber_datasrc* wird als DBPROP_INIT_DATASOURCE Eigenschaft zum Initialisieren des OLE DB Anbieters übermittelt. *subscriber_datasrc* wird nur für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten unterstützt.  
  
`[ @subscriber_location = ] 'subscriber_location'`Der Speicherort der Datenbank, der vom OLE DB-Anbieter interpretiert wird. *subscriber_location* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL. *subscriber_location* wird als DBPROP_INIT_LOCATION Eigenschaft zum Initialisieren des OLE DB Anbieters übermittelt. *subscriber_location* wird nur für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten unterstützt.  
  
`[ @subscriber_provider_string = ] 'subscriber_provider_string'`Die OLE DB anbieterspezifische Verbindungs Zeichenfolge, die die Datenquelle identifiziert. *subscriber_provider_string* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL. *subscriber_provider_string* wird an IDataInitialize weitergegeben oder als DBPROP_INIT_PROVIDERSTRING-Eigenschaft festgelegt, um den OLE DB-Anbieter zu initialisieren. *subscriber_provider_string* wird nur für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten unterstützt.  
  
`[ @subscriber_catalog = ] 'subscriber_catalog'`Der Katalog, der beim Herstellen einer Verbindung mit dem OLE DB-Anbieter verwendet werden soll. *subscriber_catalog* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. *subscriber_catalog* wird als DBPROP_INIT_CATALOG Eigenschaft zum Initialisieren des OLE DB Anbieters übermittelt. *subscriber_catalog* wird nur für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten unterstützt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_addpushsubscription_agent** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addpushsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addpushsubscription_agent**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Pushabonnements](../../relational-databases/replication/create-a-push-subscription.md)   
 [Erstellen eines Abonnements für einen nicht-SQL Server Abonnenten](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [Gespeicherte Replikations Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_addsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
