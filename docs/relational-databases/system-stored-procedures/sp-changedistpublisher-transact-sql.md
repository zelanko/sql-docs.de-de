---
title: sp_changedistpublisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedistpublisher_TSQL
- sp_changedistpublisher
helpviewer_keywords:
- sp_changedistpublisher
ms.assetid: 7ef5c89d-faaa-4f8e-aef7-00649ebc8bc9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80eb30fc6b6b2cea9fc058780831af3915fd9007
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771362"
---
# <a name="spchangedistpublisher-transact-sql"></a>sp_changedistpublisher (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ändert die Eigenschaften des Verteilungsverlegers. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changedistpublisher [ @publisher = ] 'publisher'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @storage_connection_string = ] 'storage_connection_string']
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @property = ] 'property'`Eine Eigenschaft, die für den angegebenen Verleger geändert werden soll. *Property* ist vom **Datentyp vom Datentyp sysname** . die folgenden Werte sind möglich.  
  
`[ @value = ] 'value'`Der Wert für die angegebene Eigenschaft. der Wert ist vom Datentyp **nvarchar (255)** und hat den Standard *Wert* NULL.  
  
`[ @storage_connection_string = ] 'storage_connection_string'`Ist für die verwaltete SQL-Datenbank-Instanz erforderlich, sollte mit dem Zugriffsschlüssel für das Azure SQL-Daten Bank Speicher Volume identisch sein. 


 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]
 
 Diese Tabelle beschreibt die Eigenschaften von Verlegern und die Werte für diese Eigenschaften.  
  
|Eigenschaft|Werte|Beschreibung|  
|--------------|------------|-----------------|  
|**enden**|**true**|Aktiviert den Verleger|  
||**false**|Deaktiviert den Verleger|  
|**distribution_db**||Der Name der Verteilungsdatenbank.|  
|**login**||Benutzername|  
|**password**||Sicheres Kennwort für den angegebenen Anmeldenamen.|  
|**security_mode**|**1**|Verwendung der Windows-Authentifizierung für die Verbindung mit dem Verleger. *Dies kann für einen nicht--* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger nicht geändert werden *.*|  
||**0**|Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung für die Verbindung mit dem Verleger. *Dies kann für einen nicht--* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger nicht geändert werden *.*|  
|**working_directory**||Das zum Speichern von Daten- und Schemadateien für die Veröffentlichung verwendete Arbeitsverzeichnis|  
|NULL (Standard)||Alle verfügbaren *Eigenschaften* Optionen werden gedruckt.| 
|**storage_connection_string**| Zugriffstaste | Der Zugriffsschlüssel für das Arbeitsverzeichnis, wenn die Datenbank verwaltete Azure SQL-Datenbank-Instanz wird. 
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_changedistpublisher** wird für alle Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_changedistpublisher**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
