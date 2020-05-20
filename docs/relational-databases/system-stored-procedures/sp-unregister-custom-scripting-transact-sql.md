---
title: sp_unregister_custom_scripting (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_unregister_custom_scripting_TSQL
- sp_unregister_custom_scripting
helpviewer_keywords:
- sp_unregister_custom_scripting
ms.assetid: b6e9e0d2-9144-434d-88af-4874f2582399
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8d54530c7cf6588a6ae07e1e504e3c53e86f8fa5
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820230"
---
# <a name="sp_unregister_custom_scripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mit dieser gespeicherten Prozedur wird eine benutzerdefinierte gespeicherte Prozedur oder [!INCLUDE[tsql](../../includes/tsql-md.md)] Skriptdatei entfernt, die durch Ausführen von [sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)registriert wurde. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @type = ] 'type'`Der Typ der benutzerdefinierten gespeicherten Prozedur oder des Skripts, das entfernt wird. *Type ist vom Datentyp* **varchar (16)** und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**setze**|Registrierte benutzerdefinierte gespeicherte Prozedur oder Skript wird ausgeführt, wenn eine INSERT-Anweisung repliziert wird.|  
|**update**|Registrierte benutzerdefinierte gespeicherte Prozedur oder Skript wird ausgeführt, wenn eine UPDATE-Anweisung repliziert wird.|  
|**delete**|Registrierte benutzerdefinierte gespeicherte Prozedur oder Skript wird ausgeführt, wenn eine DELETE-Anweisung repliziert wird.|  
|**custom_script**|Registrierte benutzerdefinierte gespeicherte Prozedur oder Skript wird am Ende des DDL-Triggers (Data Definition Language) ausgeführt.|  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, für die die benutzerdefinierte gespeicherte Prozedur oder das Skript entfernt wird. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @article = ] 'article'`Der Name des Artikels, für den die benutzerdefinierte gespeicherte Prozedur oder das Skript entfernt wird. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_unregister_custom_scripting** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** oder der festen Daten Bank Rolle **db_ddladmin** können **sp_unregister_custom_scripting**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_register_custom_scripting &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
