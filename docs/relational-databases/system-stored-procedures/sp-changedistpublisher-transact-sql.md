---
title: Sp_changedistpublisher (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: ba242dfc6c457bd94c082f151f162b8f6eb06e29
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52819182"
---
# <a name="spchangedistpublisher-transact-sql"></a>sp_changedistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@publisher=** ] **"***Verleger***"**  
 Der Name des Verlegers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@property=** ] **"***Eigenschaft***"**  
 Eine Eigenschaft, die für den angegebenen Verleger geändert werden soll. *Eigenschaft* ist **Sysname** und kann einen der folgenden Werte sein.  
  
 [ **@value=** ] **'***Wert***'**  
 Der Wert für die angegebene Eigenschaft. *Wert* ist **nvarchar(255)**, hat den Standardwert NULL.  
  
 [  **@storage_connection_string =**] **"***Storage_connection_string***"**  
 Erforderlich für die verwaltete SQL-Datenbank-Instanz ist, sollte den Zugriffsschlüssel für das Speichervolume für Azure SQL-Datenbank übereinstimmen. 


 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]
 
 Diese Tabelle beschreibt die Eigenschaften von Verlegern und die Werte für diese Eigenschaften.  
  
|Eigenschaft|Werte|Description|  
|--------------|------------|-----------------|  
|**aktiv**|**true**|Aktiviert den Verleger|  
||**false**|Deaktiviert den Verleger|  
|**distribution_db**||Der Name der Verteilungsdatenbank.|  
|**login**||Benutzername|  
|**password**||Sicheres Kennwort für den angegebenen Anmeldenamen.|  
|**security_mode**|**1**|Verwendung der Windows-Authentifizierung für die Verbindung mit dem Verleger. *Dies kann nicht geändert werden, für einen nicht-* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Verleger.*|  
||**0**|Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung für die Verbindung mit dem Verleger. *Dies kann nicht geändert werden, für einen nicht-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Verleger.*|  
|**working_directory**||Das zum Speichern von Daten- und Schemadateien für die Veröffentlichung verwendete Arbeitsverzeichnis|  
|NULL (Standard)||Alle verfügbaren *Eigenschaft* -Optionen werden ausgegeben.| 
|**storage_connection_string**| Zugriffsschlüssel | Der Zugriffsschlüssel für das Arbeitsverzeichnis, wenn die Datenbank über Azure verwaltete SQL-Datenbankinstanz ist. 
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changedistpublisher** wird in allen Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_changedistpublisher**.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [Sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
