---
title: Sp_helpsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpsubscription_TSQL
- sp_helpsubscription
helpviewer_keywords:
- sp_helpsubscription
ms.assetid: ff96bcbf-e2b9-4da8-8515-d80d4ce86c16
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e44e5ce6dac4f04703925b7f216e039acf8ae6cc
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43019344"
---
# <a name="sphelpsubscription-transact-sql"></a>sp_helpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet Abonnementinformationen bezüglich einer bestimmten Veröffentlichung, eines Artikels, eines Abonnenten oder einer Gruppe von Abonnements auf. Diese gespeicherte Prozedur wird auf einem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpsubscription [ [ @publication = ] 'publication' ]   
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]   
    [ , [ @found=] found OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication =** ] **'***publication***'**  
 Der Name der zugeordneten Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert **%**, dem alle Abonnementinformationen für diesen Server zurückgegeben.  
  
 [  **@article=** ] **"***Artikel***"**  
 Der Name des Artikels. *Artikel* ist **Sysname**, hat den Standardwert **%**, dem alle Abonnementinformationen für die ausgewählten Veröffentlichungen und Abonnenten zurückgegeben. Wenn **alle**, nur einen Eintrag für das vollständige Abonnement für eine Veröffentlichung zurückgegeben.  
  
 [  **@subscriber=** ] **"***Abonnenten***"**  
 Der Name des Abonnenten, für den Abonnementinformationen abgerufen werden sollen. *Abonnenten* ist **Sysname**, hat den Standardwert **%**, dem alle Abonnementinformationen für die ausgewählten Veröffentlichungen und Artikel zurückgegeben.  
  
 [  **@destination_db=** ] **"***Destination_db***"**  
 Der Name der Zieldatenbank. *Destination_db* ist **Sysname**, hat den Standardwert **%**.  
  
 [  **@found=** ] **"***gefunden***"** Ausgabe  
 Ein Flag zur Angabe zurückgegebener Zeilen. *finden Sie*ist **Int** und ein OUTPUT-Parameter mit dem Standardwert 23456.  
  
 **1** gibt an, die Veröffentlichung gefunden wurde.  
  
 **0** gibt an, die Veröffentlichung wurde nicht gefunden.  
  
 [ **@publisher**=] **"***Verleger***"**  
 Der Name des Verlegers. *Publisher* ist **Sysname**, und der Standardwert ist der Name des aktuellen Servers.  
  
> [!NOTE]  
>  *Publisher* sollte nicht angegeben werden, es sei denn, sie einen Oracle-Verleger.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**subscriber**|**sysname**|Der Name des Abonnenten.|  
|**Veröffentlichung**|**sysname**|Name der Veröffentlichung.|  
|**article**|**sysname**|Der Name des Artikels.|  
|**Zieldatenbank**|**sysname**|Name der Zieldatenbank, in der replizierte Daten gespeichert werden.|  
|**Abonnementstatus**|**tinyint**|Abonnementstatus:<br /><br /> **0** = inaktiv<br /><br /> **1** = abonniert<br /><br /> **2** = aktiv|  
|**Synchronisierungstyp**|**tinyint**|Synchronisierungsart des Abonnements:<br /><br /> **1** = automatisch<br /><br /> **2** = keine|  
|**Abonnementtyp**|**int**|Typ des Abonnements:<br /><br /> **0** = Push<br /><br /> **1** = Pullabonnement<br /><br /> **2** = anonym|  
|**vollständiges Abonnement**|**bit**|Gibt an, ob alle Artikel in der Veröffentlichung abonniert werden:<br /><br /> **0** = Nein<br /><br /> **1** = Ja|  
|**Abonnementname**|**nvarchar(255)**|Name des Abonnements.|  
|**Updatemodus**|**int**|**0** = schreibgeschützt<br /><br /> **1** = Abonnement mit sofortigem Update|  
|**Verteilungsauftrags-id**|**'binary(16)'**|Auftrags-ID des Verteilungs-Agents.|  
|**loopback_detection**|**bit**|Bestimmt, ob der Verteilungs-Agent Transaktionen des Abonnenten zurück an den Abonnenten sendet:<br /><br /> **0** = sendet zurück.<br /><br /> **1** unterstützt = sendet nicht zurück.<br /><br /> Wird bei der bidirektionalen Transaktionsreplikation verwendet. Weitere Informationen finden Sie unter [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).|  
|**offload_enabled**|**bit**|Gibt an, ob festgelegt wurde, dass die Ausführung eines ausgelagerten Replikations-Agents auf dem Abonnenten ausgeführt wird.<br /><br /> Wenn **0**, Agents auf dem Verleger ausgeführt wird.<br /><br /> Wenn **1**, Agents auf dem Abonnenten ausgeführt wird.|  
|**offload_server**|**sysname**|Name des Servers, der für die Aktivierung des Remote-Agents aktiviert ist. Wenn der Wert NULL ist, klicken Sie dann der aktuelle offload_server [MSdistribution_agents](../../relational-databases/system-tables/msdistribution-agents-transact-sql.md) Tabelle verwendet wird.|  
|**dts_package_name**|**sysname**|Gibt den Namen des DTS-Pakets (Data Transformation Services) an.|  
|**dts_package_location**|**int**|Speicherort des DTS-Pakets, wenn dem Abonnement eines zugewiesen wurde. Wenn ein Paket, ein Wert vorhanden ist **0** gibt den Speicherort des Pakets auf die **Verteiler**. Der Wert **1** gibt an, die **Abonnenten**.|  
|**subscriber_security_mode**|**smallint**|Der Sicherheitsmodus auf dem Abonnenten, in denen **1** Windows-Authentifizierung und **0** bedeutet, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**subscriber_login**|**sysname**|Der Anmeldename auf dem Abonnenten.|  
|**subscriber_password**||Das tatsächliche Abonnentenkennwort wird nie zurückgegeben. Das Ergebnis ist maskiert, indem eine "**\*\*\*\*\*\***" Zeichenfolge.|  
|**job_login-Wert**|**sysname**|Name des Windows-Kontos, unter dem der Verteilungs-Agent ausgeführt wird.|  
|**job_password**||Das tatsächliche Auftragskennwort wird nie zurückgegeben. Das Ergebnis ist maskiert, indem eine "**\*\*\*\*\*\***" Zeichenfolge.|  
|**distrib_agent_name**|**nvarchar(100)**|Name des Agentauftrags, der das Abonnement synchronisiert.|  
|**subscriber_type kann**|**tinyint**|Typ des Abonnenten. Folgende Werte sind möglich:<br /><br /> **0** = SQL Server-Abonnenten<br /><br /> **1** = ODBC-Datenquellenserver<br /><br /> **2** = Microsoft JET-Datenbank (veraltet)<br /><br /> **3** = OLE DB-Anbieter|  
|**subscriber_provider**|**sysname**|Eindeutiger Programmbezeichner (PROGID, Programmatic Identifier), mit dem der OLE DB-Anbieter für die Nicht-SQL Server-Datenquelle registriert wird.|  
|**subscriber_datasource**|**nvarchar(4000)**|Name der Datenquelle im vom OLE DB-Anbieter unterstützten Format.|  
|**subscriber_providerstring**|**nvarchar(4000)**|Für den OLE DB-Anbieter spezifische Verbindungszeichenfolge, die die Datenquelle identifiziert.|  
|**subscriber_location**|**nvarchar(4000)**|Speicherort der Datenbank im vom OLE DB-Anbieter unterstützten Format.|  
|**subscriber_catalog**|**sysname**|Katalogsichten Sie verwendet werden soll, wenn eine Verbindung mit dem OLE DB-Anbieter verwendet.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpsubscription** wird bei der Momentaufnahme- und Transaktionsreplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen erhält standardmäßig die **public** -Rolle. Benutzern werden nur Informationen für Abonnements zurückgegeben, die sie erstellt haben. Informationen zu allen Abonnements wird zurückgegeben, auf Mitglieder der der **Sysadmin** auf dem Verleger oder Mitglieder der festen Serverrolle die **Db_owner** -Datenbankrolle in der Veröffentlichungsdatenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
