---
title: sp_enumeratependingschemachanges (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3ab8827795c2d65bcd6044102567d9b265c319f4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733279"
---
# <a name="sp_enumeratependingschemachanges-transact-sql"></a>sp_enumeratependingschemachanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Liste aller ausstehenden Schemaänderungen zurück. Diese gespeicherte Prozedur kann mit [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md)verwendet werden, die es einem Administrator ermöglicht, ausgewählte ausstehende Schema Änderungen zu überspringen, sodass Sie nicht repliziert werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_enumeratependingschemachanges [ @publication = ] 'publication'   
    [ , [ @starting_schemaversion = ] starting_schemaversion ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @starting_schemaversion = ] starting_schemaversion`Die niedrigste Anzahl von Schema Änderungen, die im Resultset enthalten sein sollen.  
  
## <a name="result-set"></a>Resultset  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**article_name**|**sysname**|Der Name des Artikels, für den die Schema Änderung gilt, oder die **Veröffentlichungs weite** für Schema Änderungen, die auf die gesamte Veröffentlichung angewendet werden.|  
|**Schema Version**|**int**|Nummer der ausstehenden Schemaänderung.|  
|**schematype**|**sysname**|Der Textwert, der den Typ der Schemaänderung darstellt.|  
|**schematext**|**nvarchar(max)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] zur Beschreibung der Schemaänderung.|  
|**schemastatus**|**nvarchar (10)**|Gibt an, ob eine Schemaänderung für den Artikel aussteht. Folgende Werte sind möglich:<br /><br /> **aktiv** = Schema Änderung steht aus.<br /><br /> **inaktiv** = Schema Änderung ist inaktiv.<br /><br /> **Skip** = Schema Änderung wird nicht repliziert|  
|**schemaguid**|**uniqueidentifier**|Identifiziert die Schemaänderung.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_enumeratependingschemachanges** wird bei der Mergereplikation verwendet.  
  
 **sp_enumeratependingschemachanges**, die mit [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md)verwendet wird, ist für die unter Stütz barkeit der Mergereplikation gedacht und sollte nur verwendet werden, wenn andere Korrekturmaßnahmen, wie z. b. die erneute Initialisierung, die Situation nicht beheben konnten.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_enumeratependingschemachanges**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Replikations Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sysmergeschemachange &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
