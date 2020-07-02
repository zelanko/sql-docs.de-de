---
title: sp_schemafilter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_schemafilter_TSQL
- sp_schemafilter
helpviewer_keywords:
- sp_schemafilter
ms.assetid: 199e869b-2cd2-44ee-b2ee-69edb06a1bc4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d6414be15bcd33e8ae2a0ab267baaa039761fc04
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750454"
---
# <a name="sp_schemafilter-transact-sql"></a>sp_schemafilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Ändert Informationen im Schema, die beim Auflisten von für die Veröffentlichung in Frage kommenden Oracle-Tabellen ausgeschlossen werden, und zeigt diese an.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_schemafilter [ @publisher = ] 'publisher'   
   [ , [ @schema = ] 'schema' ]   
   [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des nicht-- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @schema = ] 'schema'`Der Name des Schemas. *Schema* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @operation = ] 'operation'`Die Aktion, die für dieses Schema ausgeführt werden soll. der *Vorgang* ist vom Datentyp **nvarchar (4)**. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**add**|Fügt das angegebene Schema der Liste der Schemas hinzu, die für die Veröffentlichung nicht in Frage kommen.|  
|**Dropdown**|Löscht das angegebene Schema aus der Liste der Schemas, die für die Veröffentlichung nicht in Frage kommen.|  
|**help**|Gibt die Liste der Schemas zurück, die für die Veröffentlichung nicht in Frage kommen.|  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Schema Name**|**sysname**|Der Name des Schemas, das für die Veröffentlichung nicht in Frage kommt.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_schemafilter** sollten nur für heterogene Verleger verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verteiler können **sp_schemafilter**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
