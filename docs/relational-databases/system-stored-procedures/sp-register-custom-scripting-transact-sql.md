---
description: sp_register_custom_scripting (Transact-SQL)
title: sp_register_custom_scripting (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_register_custom_scripting
- sp_register_custom_scripting_TSQL
helpviewer_keywords:
- sp_register_custom_scripting
ms.assetid: a8159282-de3b-4b9e-bdc9-3d3fce485c7f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4f73353cc5d2e0e9be02be5a0e6dc59eaf2f909f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547498"
---
# <a name="sp_register_custom_scripting-transact-sql"></a>sp_register_custom_scripting (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Mithilfe der Replikation ist es möglich, mindestens eine der bei der Transaktionsreplikation verwendeten Standardprozeduren durch benutzerdefinierte gespeicherte Prozeduren zu ersetzen. Wenn an einer replizierten Tabelle eine Schemaänderung vorgenommen wird, werden diese gespeicherten Prozeduren neu erstellt. **sp_register_custom_scripting** registriert eine gespeicherte Prozedur oder [!INCLUDE[tsql](../../includes/tsql-md.md)] Skriptdatei, die ausgeführt wird, wenn eine Schema Änderung auftritt, um die Definition für eine neue benutzerdefinierte gespeicherte Prozedur auszuschreiben. Diese neue, benutzerdefinierte gespeicherte Prozedur sollte das neue Schema für die Tabelle wiedergeben. **sp_register_custom_scripting** wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt, und die registrierte Skriptdatei oder die gespeicherte Prozedur wird auf dem Abonnenten ausgeführt, wenn eine Schema Änderung auftritt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_register_custom_scripting [ @type  = ] 'type'  
    [ @value = ] 'value'   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @type = ] 'type'` Der Typ der benutzerdefinierten gespeicherten Prozedur oder des Skripts, das registriert wird. *Type ist vom Datentyp* **varchar (16)** und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**insert**|Die registrierte, benutzerdefinierte gespeicherte Prozedur wird ausgeführt, wenn eine INSERT-Anweisung repliziert wird.|  
|**update**|Die registrierte, benutzerdefinierte gespeicherte Prozedur wird ausgeführt, wenn eine UPDATE-Anweisung repliziert wird.|  
|**delete**|Die registrierte, benutzerdefinierte gespeicherte Prozedur wird ausgeführt, wenn eine DELETE-Anweisung repliziert wird.|  
|**custom_script**|Das Skript wird am Ende des DDL-Triggers (Data Definition Language) ausgeführt.|  
  
`[ @value = ] 'value'` Der Name einer gespeicherten Prozedur oder eines Namens und der voll qualifizierte Pfad der [!INCLUDE[tsql](../../includes/tsql-md.md)] Skriptdatei, die registriert wird. der Wert ist vom Datentyp **nvarchar (1024)** und hat keinen Standard *Wert* .  
  
> [!NOTE]  
>  Wenn Sie NULL für *value*-Parameter angeben, wird die Registrierung eines zuvor registrierten Skripts aufgehoben. Dies entspricht dem Ausführen von [sp_unregister_custom_scripting](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md).  
  
 Wenn der Wert des *Typs* **custom_script**ist, werden der Name und der vollständige Pfad einer [!INCLUDE[tsql](../../includes/tsql-md.md)] Skriptdatei erwartet. Andernfalls muss *value* der Name einer registrierten gespeicherten Prozedur sein.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, für die die benutzerdefinierte gespeicherte Prozedur oder das Skript registriert wird. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert **null**.  
  
`[ @article = ] 'article'` Der Name des Artikels, für den die benutzerdefinierte gespeicherte Prozedur oder das Skript registriert wird. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert **null**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_register_custom_scripting** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 Diese gespeicherte Prozedur sollte ausgeführt werden, bevor Schemaänderungen an einer replizierten Tabelle vorgenommen werden. Weitere Informationen zur Verwendung dieser gespeicherten Prozedur finden Sie unter [Neugenerieren von benutzerdefinierten Transaktions Prozeduren, um Schema Änderungen widerzuspiegeln](../../relational-databases/replication/transactional/transactional-articles-regenerate-to-reflect-schema-changes.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** oder der festen Daten Bank Rolle **db_ddladmin** können **sp_register_custom_scripting**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_unregister_custom_scripting &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)  
  
  
