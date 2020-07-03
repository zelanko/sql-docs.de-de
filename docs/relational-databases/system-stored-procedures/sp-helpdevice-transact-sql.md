---
title: sp_helpdevice (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cda03415378577a061bb308c0b19e7fcd0659d49
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893605"
---
# <a name="sp_helpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Meldet Informationen zu Microsoft® SQL Server™-Sicherungsmedien.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Es wird empfohlen, stattdessen die [sys. backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) -Katalog Sicht zu verwenden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @devname = ] 'name'`Der Name des Sicherungs Mediums, für das Informationen gemeldet werden. Der Wert von *name* ist immer **sysname**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|Logischer Medienname.|  
|**physical_name**|**nvarchar(260)**|Physischer Dateiname.|  
|**description**|**nvarchar(255)**|Beschreibung des Mediums.|  
|**status**|**int**|Eine Nummer, die der Statusbeschreibung in der **description** -Spalte entspricht.|  
|**cntrltype**|**smallint**|Controllertyp des Mediums:<br /><br /> 2 = Datenträgermedium<br /><br /> 5 = Bandmedium|  
|**size**|**int**|Mediengröße in Seiten von je 2 KB.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn *name* angegeben wird, zeigt **sp_helpdevice** Informationen zu dem angegebenen Sicherungsmedium an. Wenn *name* nicht angegeben wird, zeigt **sp_helpdevice** Informationen zu allen Sicherungsmedien in der **sys.backup_devices** -Katalogsicht an.  
  
 Sicherungsmedien werden dem System mithilfe von **sp_addumpdevice**hinzugefügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zu allen Sicherungsmedien in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gemeldet.  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
