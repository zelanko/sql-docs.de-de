---
title: Sp_get_redirected_publisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_get_redirected_publisher_TSQL
- sp_get_redirected_publisher
ms.assetid: d47a9ab5-f2cc-42a8-8be9-a33895ce44f0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2c98f0eb28efd7a3f4a125d5f4cb281d9d726be5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595128"
---
# <a name="spgetredirectedpublisher-transact-sql"></a>sp_get_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Wird von Replikations-Agents verwendet, um einen Verteiler abzufragen und zu bestimmen, ob der ursprüngliche Verleger umgeleitet wurde.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_get_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @bypass_publisher_validation = ] [0 | 1 ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@original_publisher** =] **"***Original_publisher***"**  
 Der Name der zu veröffentlichenden Datenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@publisher_db** = ] **'***publisher_db***'**  
 Der Name der zu veröffentlichenden Datenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@bypass_publisher_validation** = ] [0 | 1 ]  
 Wird verwendet, um die Überprüfung des umgeleiteten Verlegers zu umgehen. Wenn der Wert 0 ist, wird die Überprüfung ausgeführt. Bei 1 wird keine Überprüfung durchgeführt. *Bypass_publisher_validation* ist **Bit**, hat den Standardwert 0.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**redirected_publisher**|**sysname**|Der Name des Verlegers nach der Umleitung.|  
|**error_number**|**int**|Die Fehlernummer des Überprüfungsfehlers.|  
|**error_severity**|**int**|Der Schweregrad des Überprüfungsfehlers.|  
|**error_message**|**nvarchar(4000)**|Der Text der Überprüfungsfehlermeldung.|  
  
## <a name="remarks"></a>Hinweise  
 *Redirected_publisher* gibt die Namen des aktuellen Verlegers zurück. Gibt zurück, null, wenn der Verleger und veröffentlichte Datenbanken nicht umgeleitet wurden mithilfe von **Sp_redirect_publisher**.  
  
 Wenn keine Überprüfung angefordert wird, oder wenn kein Eintrag für den Verleger und die Veröffentlichungsdatenbank vorhanden ist *Error_number* und *Error_severity* gibt 0 zurück und *Error_message* Gibt null zurück.  
  
 Wenn eine Überprüfung angefordert wird, wird die gespeicherte Prozedur [Sp_validate_redirected_publisher &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md) aufgerufen, um sicherzustellen, dass das Ziel der Umleitung ein geeigneter Host für die Veröffentlichung die Datenbank. Wenn die Überprüfung erfolgreich ist, **Sp_get_redirected_publisher** gibt den umgeleiteten Verlegernamen, 0 für die *Error_number* und *Error_severity* Spalten und NULL-Wert in die *Error_message* Spalte.  
  
 Wenn eine Überprüfung angefordert wird und fehlschlägt, wird der umgeleitete Verlegername zusammen mit Fehlerinformationen zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Aufrufer muss entweder ein Mitglied der **Sysadmin** festen Serverrolle, die **Db_owner** -Datenbankrolle für die Verteilungsdatenbank oder ein Mitglied einer veröffentlichungszugriffsliste für eine definierte Veröffentlichung die Publisher-Datenbank zugeordnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [Sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [Sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
