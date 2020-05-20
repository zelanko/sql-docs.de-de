---
title: sp_helptrigger (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helptrigger
- sp_helptrigger_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helptrigger
ms.assetid: e486d39b-771d-488d-a786-7136433a2203
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c01290f0f95a7e240931a9398ab7acea1b287be
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824402"
---
# <a name="sp_helptrigger-transact-sql"></a>sp_helptrigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die Typen der DML-Trigger zurück, die in der angegebenen Tabelle für die aktuelle Datenbank definiert sind. sp_helptrigger kann nicht mit DDL-Triggern verwendet werden. Fragen Sie stattdessen die Katalog Sicht der [gespeicherten System Prozeduren](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) ab.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helptrigger [ @tabname = ] 'table'   
     [ , [ @triggertype = ] 'type' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @tabname = ] 'table'`Der Name der Tabelle in der aktuellen Datenbank, für die die auslöserinformationen zurückgegeben werden sollen. *Table ist vom Datentyp* **nvarchar (776)** und hat keinen Standardwert.  
  
`[ @triggertype = ] 'type'`Der Typ des DML-Triggers, über den Informationen zurückgegeben werden sollen. *Type ist vom Datentyp* **char (6)** und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**DELETE**|Gibt DELETE-Triggerinformationen zurück.|  
|**INSERT**|Gibt INSERT-Triggerinformationen zurück.|  
|**UPDATE**|Gibt UPDATE-Triggerinformationen zurück.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Die folgende Tabelle zeigt die im Resultset enthaltenen Informationen an.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**trigger_name**|**sysname**|Name des Triggers.|  
|**trigger_owner**|**sysname**|Name des Besitzers der Tabelle, für die der Trigger definiert ist.|  
|**isupdate**|**int**|1=UPDATE-Trigger<br /><br /> 0=Kein UPDATE-Trigger|  
|**isdelete**|**int**|1=DELETE-Trigger<br /><br /> 0=Kein DELETE-Trigger|  
|**isinsert**|**int**|1=INSERT-Trigger<br /><br /> 0=Kein INSERT-Trigger|  
|**isafter**|**int**|1=AFTER-Trigger<br /><br /> 0=Kein AFTER-Trigger|  
|**isinsteadof**|**int**|1=INSTEAD OF-Trigger<br /><br /> 0=Kein INSTEAD OF-Trigger|  
|**trigger_schema**|**sysname**|Name des Schemas, zu dem der Trigger gehört.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Konfigurations Berechtigung für die [Sichtbarkeit von Metadaten](../../relational-databases/security/metadata-visibility-configuration.md) für die Tabelle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `sp_helptrigger` ausgeführt, um Informationen zu den Triggern in der `Person.Person`-Tabelle zu erzeugen.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptrigger 'Person.Person';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
