---
description: sp_changedistpublisher (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 565ca8d7328446435aa584b614014d0ce22cb2c1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464512"
---
# <a name="sp_changedistpublisher-transact-sql"></a>sp_changedistpublisher (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Ändert die Eigenschaften des Verteilungsverlegers. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changedistpublisher [ @publisher = ] 'publisher'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @storage_connection_string = ] 'storage_connection_string']
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @property = ] 'property'` Eine Eigenschaft, die für den angegebenen Verleger geändert werden soll. *Property* ist vom **Datentyp vom Datentyp sysname** . die folgenden Werte sind möglich.  
  
`[ @value = ] 'value'` Der Wert für die angegebene Eigenschaft. der Wert ist vom Datentyp **nvarchar (255)** und hat den Standard *Wert* NULL.  
  
`[ @storage_connection_string = ] 'storage_connection_string'` Ist für SQL verwaltete Instanz erforderlich und sollte mit dem Zugriffsschlüssel für das Speicher Volume der Azure SQL-Datenbank verglichen werden. 


 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]
 
 Diese Tabelle beschreibt die Eigenschaften von Verlegern und die Werte für diese Eigenschaften.  
  
|Eigenschaft|Werte|Beschreibung|  
|--------------|------------|-----------------|  
|**active**|**true**|Aktiviert den Verleger|  
||**false**|Deaktiviert den Verleger|  
|**distribution_db**||Der Name der Verteilungsdatenbank.|  
|**Anmel**||Benutzername|  
|**password**||Sicheres Kennwort für den angegebenen Anmeldenamen.|  
|**security_mode**|**1**|Verwendung der Windows-Authentifizierung für die Verbindung mit dem Verleger. *Dies kann nicht geändert werden für eine nicht-* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Verleger.*|  
||**0**|Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung für die Verbindung mit dem Verleger. *Dies kann nicht geändert werden für eine nicht-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Verleger.*|  
|**working_directory**||Das zum Speichern von Daten- und Schemadateien für die Veröffentlichung verwendete Arbeitsverzeichnis|  
|NULL (Standard)||Alle verfügbaren *Eigenschaften* Optionen werden gedruckt.| 
|**storage_connection_string**| Zugriffsschüssel | Der Zugriffsschlüssel für das Arbeitsverzeichnis, wenn die Datenbank Azure SQL-verwaltete Instanz ist. 
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_changedistpublisher** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_changedistpublisher**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
