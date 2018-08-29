---
title: Sp_helpmergefilter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpmergefilter
- sp_helpmergefilter_TSQL
helpviewer_keywords:
- sp_helpmergefilter
ms.assetid: f133a094-0009-4771-b93b-e86a5c01e40b
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 327e47c5dbb48b7944a8389c2fd56ccec96b8668
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43030816"
---
# <a name="sphelpmergefilter-transact-sql"></a>sp_helpmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu Mergefiltern zurück. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergefilter [ @publication= ] 'publication'   
    [ , [ @article= ] 'article']  
    [ , [ @filtername= ] 'filtername']  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@article=**] **"***Artikel***"**  
 Der Name des Artikels. *Artikel* ist **Sysname**, hat den Standardwert **%**, die Namen aller Artikel zurückgegeben.  
  
 [  **@filtername=**] **"***Filtername***"**  
 Der Name des Filters, zu dem Informationen zurückgegeben werden sollen. *Filtername* ist **Sysname**, hat den Standardwert **%**, Informationen zu allen auf dem Artikel oder die Veröffentlichung definierten Filtern zurückgegeben.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**join_filterid**|**int**|ID des Joinfilters.|  
|**Filtername**|**sysname**|Name des Filters.|  
|**Name des Join-Artikels**|**sysname**|Name des Join-Artikels.|  
|**join_filterclause**|**Datentyp nvarchar(2000)**|Filterklausel für den Join.|  
|**join_unique_key**|**int**|Gibt an, ob der Join einen eindeutigen Schlüssel betrifft.|  
|**Besitzer der Basistabelle**|**sysname**|Name des Besitzers der Basistabelle.|  
|**Name der Basistabelle**|**sysname**|Name der Basistabelle.|  
|**Besitzer des Join-Tabelle**|**sysname**|Name des Besitzers der Tabelle, die mit der Basistabelle verknüpft wird.|  
|**Join-Tabellenname**|**sysname**|Name der Tabelle, die mit der Basistabelle verknüpft wird.|  
|**Artikelname**|**sysname**|Name des Tabellenartikels, der mit der Basistabelle verknüpft wird.|  
|**filter_type**|**tinyint**|Typ des Mergefilters. Die folgenden Werte sind möglich:<br /><br /> **1** = nur joinfilter<br /><br /> **2** = logische datensatzbeziehung<br /><br /> **3** = beide|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpmergefilter** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** Serverrolle und die **Db_owner** feste Datenbankrolle können ausführen **Sp_helpmergefilter**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
