---
title: sp_helpremotelogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpremotelogin_TSQL
- sp_helpremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpremotelogin
ms.assetid: 93f50869-2627-4642-899f-8f626f8833f4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d912271e1f772ed0161b6c97977917d525b7d771
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899513"
---
# <a name="sp_helpremotelogin-transact-sql"></a>sp_helpremotelogin (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu Remoteanmeldenamen für einen bestimmten Remoteserver oder für alle Remoteserver zurück, die auf dem lokalen Server definiert sind.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Verwenden Sie stattdessen Verbindungsserver und gespeicherte Prozeduren, die über Verbindungsserver ausgeführt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpremotelogin [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @remoteserver **=** ] **'***Remote Server***'**  
 Der Remoteserver, für den Informationen zu Remoteanmeldenamen zurückgegeben werden. *Remote Server* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *Remote Server* nicht angegeben wird, werden Informationen zu allen Remote Servern zurückgegeben, die auf dem lokalen Server definiert sind.  
  
 [ @remotename **=** ] **'***remote_name***'**  
 Ein bestimmter Remoteanmeldename auf dem Remoteserver. *remote_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Wenn *remote_name* nicht angegeben wird, werden Informationen zu allen Remote Benutzern, die für *Remote Server* definiert sind, zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|server|**sysname**|Name des Remoteservers, der auf dem lokalen Server definiert ist.|  
|local_user_name|**sysname**|Anmeldename auf dem lokalen Server, dem Remoteanmeldenamen vom Server zugeordnet werden.|  
|remote_user_name|**sysname**|Anmeldename auf dem Remoteserver, der local_user_name zugeordnet wird.|  
|Optionen|**sysname**|Vertrauenswürdig = Der Remoteanmeldename muss beim Herstellen der Verbindung zum lokalen Server vom Remoteserver aus kein Kennwort angeben.<br /><br /> Nicht vertrauenswürdig (oder leer) = Der Remoteanmeldename wird beim Herstellen der Verbindung zum lokalen Server vom Remoteserver aus zur Eingabe eines Kennworts aufgefordert.|  
  
## <a name="remarks"></a>Hinweise  
 Mit sp_helpserver listen Sie die Namen der auf dem lokalen Server definierten Remoteserver auf.  
  
## <a name="permissions"></a>Berechtigungen  
 Es werden keine Berechtigungen geprüft.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-reporting-help-on-a-single-server"></a>A. Anzeigen der Hilfe zu einem einzelnen Server  
 Im folgenden Beispiel werden Informationen zu allen Remotebenutzern auf dem Remoteserver `Accounts` angezeigt.  
  
```  
EXEC sp_helpremotelogin 'Accounts';  
```  
  
### <a name="b-reporting-help-on-all-remote-users"></a>B. Anzeigen der Hilfe zu allen Remotebenutzern  
 Im folgenden Beispiel werden Informationen zu allen Remotebenutzern auf allen Remoteservern angezeigt, die dem lokalen Server bekannt sind.  
  
```  
EXEC sp_helpremotelogin;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addremotelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
