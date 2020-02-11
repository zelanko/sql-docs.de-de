---
title: sp_enum_proxy_for_subsystem (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_proxy_for_subsystem_TSQL
- sp_enum_proxy_for_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_proxy_for_subsystems
ms.assetid: 580cc3be-1068-4a96-8d15-78ca3a5bb719
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 93a55b28325bd9b04af569120ad34baeb689e8f9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124662"
---
# <a name="sp_enum_proxy_for_subsystem-transact-sql"></a>sp_enum_proxy_for_subsystem (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet die Berechtigungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Proxys für den Zugriff auf Subsysteme auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_enum_proxy_for_subsystem  
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @proxy_id = ] proxy_id`Die ID des Proxys, für den Informationen aufgelistet werden sollen. Der *proxy_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es kann entweder die *ID* oder die *proxy_name* angegeben werden.  
  
`[ @proxy_name = ] 'proxy_name'`Der Name des Proxys, für den Informationen aufgelistet werden sollen. Der *proxy_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es kann entweder die *ID* oder die *proxy_name* angegeben werden.  
  
`[ @subsystem_id = ] subsystem_id`Die ID des Subsystems, für das Informationen aufgelistet werden sollen. Der *subsystem_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es kann entweder die *subsystem_id* oder die *subsystem_name* angegeben werden.  
  
`[ @subsystem_name = ] 'subsystem_name'`Der Name des Subsystems, für das Informationen aufgelistet werden sollen. Der *subsystem_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es kann entweder die *subsystem_id* oder die *subsystem_name* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|ID des Subsystems|  
|**subsystem_name**|**sysname**|Der Name des Subsystems.|  
|**proxy_id**|**int**|ID des Proxys.|  
|**proxy_name**|**sysname**|Der Name des Proxys.|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="remarks"></a>Bemerkungen  
 Wenn keine Parameter angegeben werden, werden in **sp_enum_proxy_for_subsystem** Informationen zu allen Proxys in der Instanz für jedes Subsystem aufgelistet.  
  
 Wenn eine Proxy-ID oder ein Proxy Name bereitgestellt wird, werden in **sp_enum_proxy_for_subsystem** Subsysteme aufgelistet, auf die der Proxy Zugriff hat. Wenn eine Subsystem-ID oder ein Subsystemname bereitgestellt wird, werden **sp_enum_proxy_for_subsystem** Proxys aufgelistet, die Zugriff auf dieses Subsystem haben.  
  
 Wenn sowohl Proxy- als auch Subsysteminformationen angegeben werden, gibt das Resultset eine Zeile zurück, falls der angegebene Proxy auf das angegebene Subsystem zugreifen kann.  
  
 Diese gespeicherte Prozedur befindet sich in **msdb**.  
  
## <a name="permissions"></a>Berechtigungen  
 Ausführungs Berechtigungen für diese Prozedur werden standardmäßig Mitgliedern der festen Server Rolle **sysadmin** zugewiesen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-all-associations"></a>A. Auflisten aller Zuordnungen  
 Mit dem folgenden Beispiel werden alle Berechtigungen aufgelistet, die für die aktuelle Instanz zwischen Proxys und Subsystemen eingerichtet wurden.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem ;  
GO  
```  
  
### <a name="b-determining-if-a-proxy-has-access-to-a-specific-subsystem"></a>B. Bestimmen der Zugriffsmöglichkeiten eines Proxys für ein bestimmtes Subsystem  
 Das folgende Beispiel gibt eine Zeile zurück, falls der Proxy `Catalog application proxy` auf das `ActiveScripting`-Subsystem zugreifen kann. Andernfalls wird durch den Beispielcode ein leeres Resultset zurückgegeben.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem  
    @subsystem_name = 'ActiveScripting',  
    @proxy_name = 'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
