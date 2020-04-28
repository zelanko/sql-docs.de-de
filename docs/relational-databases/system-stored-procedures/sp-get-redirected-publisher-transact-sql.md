---
title: sp_get_redirected_publisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_get_redirected_publisher_TSQL
- sp_get_redirected_publisher
ms.assetid: d47a9ab5-f2cc-42a8-8be9-a33895ce44f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: a3972d2d92274c3454f8add9fb7b92a001dda359
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124049"
---
# <a name="sp_get_redirected_publisher-transact-sql"></a>sp_get_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Wird von Replikations-Agents verwendet, um einen Verteiler abzufragen und zu bestimmen, ob der ursprüngliche Verleger umgeleitet wurde.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_get_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @bypass_publisher_validation = ] [0 | 1 ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @original_publisher = ] 'original_publisher'`Der Name der Instanz von SQL Server, die die Datenbank ursprünglich veröffentlicht hat. *original_publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Datenbank, die veröffentlicht wird. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @bypass_publisher_validation = ] [0 | 1 ]`Wird verwendet, um die Validierung des umgeleiteten Verlegers zu umgehen. Wenn der Wert 0 ist, wird die Validierung ausgeführt. Bei 1 wird keine Überprüfung durchgeführt. *bypass_publisher_validation* ist vom Typ **Bit**. der Standardwert ist 0.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**redirected_publisher**|**sysname**|Der Name des Verlegers nach der Umleitung.|  
|**error_number**|**int**|Die Fehlernummer des Überprüfungsfehlers.|  
|**error_severity**|**int**|Der Schweregrad des Überprüfungsfehlers.|  
|**error_message**|**nvarchar(4000)**|Der Text der Überprüfungsfehlermeldung.|  
  
## <a name="remarks"></a>Bemerkungen  
 *redirected_publisher* gibt den Namen des aktuellen Verlegers zurück. Gibt NULL zurück, wenn der Verleger und die Veröffentlichungs Datenbanken nicht mithilfe von **sp_redirect_publisher**umgeleitet wurden.  
  
 Wenn keine Überprüfung angefordert wird oder wenn kein Eintrag für den Verleger und die Veröffentlichungs Datenbank vorhanden ist, wird *ERROR_NUMBER* und *ERROR_SEVERITY* 0 zurückgegeben und *ERROR_MESSAGE* NULL zurückgegeben.  
  
 Wenn eine Überprüfung angefordert wird, wird die gespeicherte Überprüfungs Prozedur [sp_validate_redirected_publisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md) aufgerufen, um zu überprüfen, ob das Ziel der Umleitung ein geeigneter Host für die Veröffentlichungs Datenbank ist. Wenn die Überprüfung erfolgreich ist, gibt **sp_get_redirected_publisher** den umgeleiteten Herausgeber Namen, 0 für die *ERROR_NUMBER* -und *ERROR_SEVERITY* Spalten und NULL in der *ERROR_MESSAGE* Spalte zurück.  
  
 Wenn eine Überprüfung angefordert wird und fehlschlägt, wird der umgeleitete Verlegername zusammen mit Fehlerinformationen zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Der Aufrufer muss entweder ein Mitglied der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** für die Verteilungs Datenbank oder ein Mitglied einer Veröffentlichungs Zugriffsliste für eine der Verleger Datenbank zugeordnete definierte Veröffentlichung sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Replikations Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
