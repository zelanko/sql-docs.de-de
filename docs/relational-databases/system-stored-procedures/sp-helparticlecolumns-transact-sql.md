---
title: Sp_helparticlecolumns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticlecolumns
- sp_helparticlecolumns_TSQL
helpviewer_keywords:
- sp_helparticlecolumns
ms.assetid: 9ea55df3-2e99-4683-88ad-bde718288bc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd7a493a3126aecbf816d364e5b7497f2bf494d5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084965"
---
# <a name="sphelparticlecolumns-transact-sql"></a>sp_helparticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt alle Spalten in der zugrunde liegenden Tabelle zurück. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt. Für Oracle-Verleger wird diese gespeicherte Prozedur auf dem Verteiler auf jeder Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helparticlecolumns [ @publication = ] 'publication'   
        , [ @article = ] 'article'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung, die der Artikel enthält. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @article = ] 'article'` Ist der Name des Artikels, dessen Spalten zurückgegeben. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht beim Veröffentlichen des angeforderten Artikels von angegeben werden eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Spalten, die nicht veröffentlicht werden) oder **1** (Spalten, die veröffentlicht werden)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**Spalten-id**|**int**|Bezeichner der Spalte.|  
|**column**|**sysname**|Der Name der Spalte.|  
|**published**|**bit**|Gibt an, ob die Spalte veröffentlicht wird:<br /><br /> **0** = Nein<br /><br /> **1** = Ja|  
|**verlegertyp**|**sysname**|Datentyp der Spalte auf dem Verleger.|  
|**Abonnententyp**|**sysname**|Datentyp der Spalte auf dem Abonnenten.|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helparticlecolumns** wird bei der Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 **Sp_helparticlecolumns** eignet sich für eine vertikale Partition zu überprüfen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle, die **Db_owner** feste Datenbankrolle oder der veröffentlichungszugriffsliste für die aktuelle Veröffentlichung kann ausführen **Sp_helparticlecolumns**.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren und Ändern eines Spaltenfilters](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
