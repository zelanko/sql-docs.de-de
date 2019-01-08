---
title: Sp_enumeratependingschemachanges (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_enumeratependingschemachanges
- sp_enumeratependingschemachanges_TSQL
helpviewer_keywords:
- sp_enumeratependingschemachanges
ms.assetid: df169b21-d10a-41df-b3a1-654cfb58bc21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 027e2f2f423024a374533decd6f35bb9bf7ccb3e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52760222"
---
# <a name="spenumeratependingschemachanges-transact-sql"></a>sp_enumeratependingschemachanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste aller ausstehenden Schemaänderungen zurück. Diese gespeicherte Prozedur kann verwendet werden, mit [Sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), ermöglicht dem Administrator, ausgewählte ausstehende schemaänderungen auszulassen, sodass sie nicht repliziert werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_enumeratependingschemachanges [ @publication = ] 'publication'   
    [ , [ @starting_schemaversion = ] starting_schemaversion ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=** ] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@starting_schemaversion=** ] *Starting_schemaversion*  
 Die Schemaänderung mit der niedrigsten Nummer, die im Resultset enthalten sein soll.  
  
## <a name="result-set"></a>Resultset  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Artikelname**|**sysname**|Name des Artikels, für die die schemaänderung gilt, oder **veröffentlichungsweiten** für schemaänderungen, die für die gesamte Veröffentlichung gelten.|  
|**Schemaversion**|**int**|Nummer der ausstehenden Schemaänderung.|  
|**SchemaType**|**sysname**|Der Textwert, der den Typ der Schemaänderung darstellt.|  
|**Schematext**|**nvarchar(max)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] zur Beschreibung der Schemaänderung.|  
|**Schemastatus**|**nvarchar(10)**|Gibt an, ob eine Schemaänderung für den Artikel aussteht. Folgende Werte sind möglich:<br /><br /> **aktive** = schemaänderung steht aus<br /><br /> **Inaktive** = schemaänderung ist inaktiv<br /><br /> **Überspringen Sie** = schemaänderung wird nicht repliziert.|  
|**SchemaGuid**|**uniqueidentifier**|Identifiziert die Schemaänderung.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_enumeratependingschemachanges** wird bei der Mergereplikation verwendet.  
  
 **Sp_enumeratependingschemachanges**verwendet mit [Sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), richtet sich die Unterstützung für die Mergereplikation und sollte verwendet werden, nur, wenn andere Abhilfemaßnahmen, wie z. B. erneute Initialisierung, nicht das Problem zu beheben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_enumeratependingschemachanges**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Sysmergeschemachange &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
