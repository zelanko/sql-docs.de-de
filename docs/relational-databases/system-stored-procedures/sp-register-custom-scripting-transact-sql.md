---
title: Sp_register_custom_scripting (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 85f9104d9a9bb634dd10dfb588cf07e01d1c1fb1
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535918"
---
# <a name="spregistercustomscripting-transact-sql"></a>sp_register_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mithilfe der Replikation ist es möglich, mindestens eine der bei der Transaktionsreplikation verwendeten Standardprozeduren durch benutzerdefinierte gespeicherte Prozeduren zu ersetzen. Wenn an einer replizierten Tabelle eine Schemaänderung vorgenommen wird, werden diese gespeicherten Prozeduren neu erstellt. **Sp_register_custom_scripting** registriert eine gespeicherte Prozedur oder [!INCLUDE[tsql](../../includes/tsql-md.md)] Skriptdatei, die ausgeführt wird, wenn das Skript für die Definition für eine neue benutzerdefinierte benutzerdefinierte gespeicherte Prozedur eine schemaänderung erfolgt. Diese neue, benutzerdefinierte gespeicherte Prozedur sollte das neue Schema für die Tabelle wiedergeben. **Sp_register_custom_scripting** auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt wird und die registrierte Skriptdatei bzw. gespeicherte Prozedur auf dem Abonnenten ausgeführt wird, wenn eine schemaänderung erfolgt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_register_custom_scripting [ @type  = ] 'type'  
    [ @value = ] 'value'   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @type = ] 'type'` Der Typ der benutzerdefinierten gespeicherten Prozedur oder Skript registriert wird. *Typ* ist **varchar(16)** und hat keinen Standardwert und kann die folgenden Werte sind möglich.  
  
|Wert|Description|  
|-----------|-----------------|  
|**insert**|Die registrierte, benutzerdefinierte gespeicherte Prozedur wird ausgeführt, wenn eine INSERT-Anweisung repliziert wird.|  
|**update**|Die registrierte, benutzerdefinierte gespeicherte Prozedur wird ausgeführt, wenn eine UPDATE-Anweisung repliziert wird.|  
|**delete**|Die registrierte, benutzerdefinierte gespeicherte Prozedur wird ausgeführt, wenn eine DELETE-Anweisung repliziert wird.|  
|**custom_script**|Das Skript wird am Ende des DDL-Triggers (Data Definition Language) ausgeführt.|  
  
`[ @value = ] 'value'` Name einer gespeicherten Prozedur oder Namen und den vollqualifizierten Pfad zu der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skriptdatei, die registriert wird. *Wert* ist **nvarchar(1024)**, hat keinen Standardwert.  
  
> [!NOTE]  
>  Angeben von NULL für *Wert*Parameter Registrierung ein zuvor registriertes Skripts, die die gleiche Weise wie das Ausführen ist [Sp_unregister_custom_scripting](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md).  
  
 Wenn der Wert des *Typ* ist **Custom_script**, den Namen und den vollständigen Pfad ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skriptdatei erwartet. Andernfalls *Wert* muss der Name einer registrierten gespeicherten Prozedur sein.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, für die die benutzerdefinierte Prozedur bzw. das Skript gespeicherte, registriert wird. *Veröffentlichung* ist **Sysname**, hat den Standardwert **NULL**.  
  
`[ @article = ] 'article'` Der Name des Artikels für die die benutzerdefinierte Prozedur bzw. das Skript gespeicherte registriert wird. *Artikel* ist **Sysname**, hat den Standardwert **NULL**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_register_custom_scripting** wird bei der Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 Diese gespeicherte Prozedur sollte ausgeführt werden, bevor Schemaänderungen an einer replizierten Tabelle vorgenommen werden. Weitere Informationen zur Verwendung dieser gespeicherten Prozedur finden Sie unter [generieren Transaktionsprozeduren zur Erfassung von Schemaänderungen](../../relational-databases/replication/transactional/transactional-articles-regenerate-to-reflect-schema-changes.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle die **Db_owner** feste Datenbankrolle oder der **Db_ddladmin** feste Datenbankrolle können ausführen **Sp_ Register_custom_scripting**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_unregister_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)  
  
  
