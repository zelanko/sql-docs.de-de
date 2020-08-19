---
description: sp_addsynctriggers (Transact-SQL)
title: sp_addsynctriggers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsynctriggers_TSQL
- sp_addsynctriggers
helpviewer_keywords:
- sp_addsynctriggers
ms.assetid: e37d0c3b-19bf-4719-9535-96ba361372b3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 400b6ef96cd841c2115fcb13bd5e8b782816ce43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486262"
---
# <a name="sp_addsynctriggers-transact-sql"></a>sp_addsynctriggers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Erstellt auf dem Abonnenten Trigger, die mit allen Typen aktualisierbarer Abonnements verwendet werden können (sofortiges Aktualisieren, verzögertes Aktualisieren über eine Warteschlange, sofortiges Aktualisieren mit verzögertem Aktualisieren über eine Warteschlange als Failover). Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Die [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) Prozedur sollte anstelle **sp_addsynctrigger**verwendet werden. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) generiert ein Skript, das die **sp_addsynctrigger** Aufrufe enthält.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addsynctriggers [ @sub_table = ] 'sub_table'  
        , [ @sub_table_owner = ] 'sub_table_owner'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @ins_proc = ] 'ins_proc'   
        , [ @upd_proc = ] 'upd_proc'   
        , [ @del_proc = ] 'del_proc'   
        , [ @cftproc = ] 'cftproc'  
        , [ @proc_owner = ] 'proc_owner'  
    [ , [ @identity_col = ] 'identity_col' ]  
    [ , [ @ts_col = ] 'timestamp_col' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]   
        , [ @primary_key_bitmap = ] 'primary_key_bitmap'  
    [ , [ @identity_support = ] identity_support ]  
    [ , [ @independent_agent = ] independent_agent ]  
        , [ @distributor = ] 'distributor'   
    [ , [ @pubversion = ] pubversion  
```  
  
## <a name="arguments"></a>Argumente  
`[ @sub_table = ] 'sub_table'` Der Name der Abonnenten Tabelle. *sub_table* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @sub_table_owner = ] 'sub_table_owner'` Der Name des Besitzers der Abonnenten Tabelle. *sub_table_owner* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher = ] 'publisher'` Der Name des Verleger Servers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Mit NULL wird die aktuelle Datenbank verwendet.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @ins_proc = ] 'ins_proc'` Der Name der gespeicherten Prozedur, die synchrone Transaktions Einfügungen auf dem Verleger unterstützt. *ins_proc* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @upd_proc = ] 'upd_proc'` Der Name der gespeicherten Prozedur, die synchrone Transaktions Aktualisierungen auf dem Verleger unterstützt. *ins_proc* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @del_proc = ] 'del_proc'` Der Name der gespeicherten Prozedur, die synchrone Transaktions Löschungen auf dem Verleger unterstützt. *ins_proc* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @cftproc = ] 'cftproc'` Der Name der automatisch generierten Prozedur, die von Veröffentlichungen verwendet wird, die ein verzögertes Update über eine Warteschlange zulassen. *cftproc* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Für Veröffentlichungen mit sofortigem Update ist dieser Wert NULL. Dieser Parameter wird auf Veröffentlichungen angewendet, die verzögerte Updates über eine Warteschlange ermöglichen (verzögertes Update über eine Warteschlange bzw. sofortiges Update mit verzögertem Update über eine Warteschlange als Failover).  
  
`[ @proc_owner = ] 'proc_owner'` Gibt das Benutzerkonto auf dem Verleger an, unter dem alle automatisch generierten gespeicherten Prozeduren zum Aktualisieren der Veröffentlichung (in der Warteschlange und/oder unmittelbar) erstellt wurden. *proc_owner* ist vom **Datentyp vom Datentyp sysname** und hat keinen Standard.  
  
`[ @identity_col = ] 'identity_col'` Der Name der Identitäts Spalte auf dem Verleger. *identity_col* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @ts_col = ] 'timestamp_col'` Der Name der **Zeitstempel** -Spalte auf dem Verleger. *timestamp_col* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @filter_clause = ] 'filter_clause'` Eine Einschränkungs Klausel (WHERE), die einen horizontalen Filter definiert. Wenn Sie die Einschränkungs Klausel eingeben, lassen Sie das Schlüsselwort aus. *filter_clause*ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL.  
  
`[ @primary_key_bitmap = ] 'primary_key_bitmap'` Ist eine Bitmap der Primärschlüssel Spalten in der Tabelle. *primary_key_bitmap* ist vom Datentyp **varbinary (4000)** und hat keinen Standardwert.  
  
`[ @identity_support = ] identity_support` Aktiviert und deaktiviert die automatische Behandlung von Identitäts Bereichen, wenn ein verzögertes Update über eine Warteschlange verwendet wird *identity_support* ist ein **Bit**, der Standardwert ist **0**. **0** bedeutet, dass keine Unterstützung für den Identitäts Bereich vorhanden ist, **1** aktiviert die automatische Handhabung von Identitäts Bereichen.  
  
`[ @independent_agent = ] independent_agent` Gibt an, ob ein einzelner Verteilungs-Agent (ein unabhängiger Agent) für diese Veröffentlichung oder ein Verteilungs-Agent pro Veröffentlichungs Datenbank und Abonnement Datenbank-Paar (ein frei gegebener Agent) vorhanden ist. Dieser Wert reflektiert den Wert der independent_agent-Eigenschaft von der auf Verlegerebene definierten Veröffentlichung. *independent_agent* ist ein Bit mit einem Standardwert von **0**. Wenn der Wert **0**ist, ist der Agent ein frei gegebener Agent. Wenn der Wert **1**ist, ist der Agent ein unabhängiger Agent.  
  
`[ @distributor = ] 'distributor'` Der Name des Verteilers. *Distributor* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @pubversion = ] pubversion` Gibt die Version des Verlegers an. *pubversion* ist vom Datentyp **int**und hat den Standardwert 1. **1** bedeutet, dass die Verleger Version [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 2 oder früher ist. **2** bedeutet, dass es sich bei dem Verleger um [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 3 (SP3) oder höher handelt. *pubversion* muss explizit auf **2** festgelegt werden, wenn die Verleger Version [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] SP3 oder höher ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addsynctriggers** wird von der Verteilungs-Agent als Teil der Abonnement Initialisierung verwendet. Diese gespeicherte Prozedur wird normalerweise nicht von Benutzern ausgeführt, kann jedoch hilfreich sein, wenn der Benutzer manuell ein nosync-Abonnement einrichten muss.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addsynctriggers**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
