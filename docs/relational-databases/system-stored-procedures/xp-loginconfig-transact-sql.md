---
title: xp_loginconfig (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_loginconfig_TSQL
- xp_loginconfig
dev_langs:
- TSQL
helpviewer_keywords:
- xp_loginconfig
ms.assetid: d380e799-2857-408a-bcbf-5e73a8e6aa5a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: afef091db5038a6ca302c07a6171557577d46797
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890745"
---
# <a name="xp_loginconfig-transact-sql"></a>xp_loginconfig (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Meldet die Anmeldesicherheitskonfiguration einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_loginconfig ['config_name']  
```  
  
## <a name="arguments"></a>Argumente  
 **"** *config_name* **"**  
 Der anzuzeigende Konfigurationswert. Wenn *config_name* nicht angegeben ist, werden alle Konfigurationswerte gemeldet. *config_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**login mode**|Der Anmeldungssicherheitsmodus. Mögliche Werte sind **gemischt** und **Windows-Authentifizierung**.<br /><br /> Ersetzt durch:<br /><br /> `SELECT SERVERPROPERTY('IsIntegratedSecurityOnly'); GO`|  
|**default login**|Der Name der standardmäßigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmelde-ID für autorisierte Benutzer vertrauenswürdiger Verbindungen (für Benutzer ohne entsprechenden Anmeldenamen). Der Standard Anmelde Name lautet **Guest**. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
|**Standarddomäne**|Der Name der standardmäßigen Windows-Domäne für Netzwerkbenutzer vertrauenswürdiger Verbindungen. Die Standarddomäne ist die Domäne des Computers, auf dem Windows und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
|**Überwachungs Ebene**|Die Überwachungsebene. Mögliche Werte sind **None**, **Success**, **Failure**und **all**. Überwachungen werden in das Fehlerprotokoll und in die Windows-Ereignisanzeige geschrieben.|  
|**set hostname**|Gibt an, ob der Hostname aus dem Clientanmeldedatensatz durch den Windows-Netzwerk-Benutzernamen ersetzt wird. Mögliche Werte sind **true** oder **false**. Wenn dies festgelegt ist, wird der Netzwerk Benutzername in der Ausgabe von **sp_who**angezeigt.|  
|**map _**|Meldet, welche Windows-Sonderzeichen dem gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Unterstrich (_) zugeordnet sind. Mögliche Werte sind **Domänen Trennzeichen** (Standard), **leer**Zeichen, **null**oder ein beliebiges einzelnes Zeichen. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
|**Map $**|Meldet, welche Windows-Sonderzeichen dem gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dollarzeichen ($) zugeordnet sind. Mögliche Werte sind **Domänen Trennzeichen**, **leer**Zeichen, **null**oder ein beliebiges einzelnes Zeichen. Der Standardwert ist **Leerzeichen**. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
|**bilden #**|Meldet, welche Windows-Sonderzeichen dem gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Nummernzeichen (#) zugeordnet sind. Mögliche Werte sind **Domänen Trennzeichen**, **leer**Zeichen, **null**oder ein beliebiges einzelnes Zeichen. Der Standard ist der Bindestrich. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Konfigurationswert|  
|**config value**|**sysname**|Die Einstellung für den Konfigurationswert|  
  
## <a name="remarks"></a>Hinweise  
 **xp_loginconfig** können nicht verwendet werden, um Konfigurationswerte festzulegen.  
  
 Verwenden Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], um den Anmeldemodus und die Überwachungsebene festzulegen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für die **Master** -Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-how-to-report-all-configuration-values"></a>A. Ausgeben aller Konfigurationswerte  
 Das folgende Beispiel gibt alle derzeit konfigurierten Einstellungen aus.  
  
```  
EXEC xp_loginconfig;  
GO  
```  
  
### <a name="b-how-to-report-a-specific-configuration-value"></a>B. Ausgeben eines bestimmten Konfigurationswerts  
 Das folgende Beispiel gibt nur die Einstellung für den Anmeldemodus aus.  
  
```  
EXEC xp_loginconfig 'login mode';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_denylogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
