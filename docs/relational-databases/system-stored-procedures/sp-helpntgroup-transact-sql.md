---
title: sp_helpntgroup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpntgroup
- sp_helpntgroup_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpntgroup
ms.assetid: 02b4f7c1-480a-436c-8bae-7a2488be45d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 76da15896b5947d0fb66c717fcaeadcab045326e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834434"
---
# <a name="sp_helpntgroup-transact-sql"></a>sp_helpntgroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Meldet Informationen zu Windows-Gruppen mit Konten in der aktuellen Datenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpntgroup [ [ @ntname= ] 'name' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @ntname = ] 'name'`Der Name der Windows-Gruppe. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL. *name* muss eine gültige Windows-Gruppe mit Zugriff auf die aktuelle Datenbank sein. Wird *name* nicht angegeben, umfasst die Ausgabe alle Windows-Gruppen mit Zugriff auf die aktuelle Datenbank.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**NTGroupName**|**sysname**|Name der Windows-Gruppe.|  
|**NTGroupId**|**smallint**|Gruppenbezeichner (ID).|  
|**SID**|**varbinary(85)**|Sicherheits-ID (SID) von **NTGroupName**.|  
|**Hasdbaccess**|**int**|1 = Windows-Gruppe hat Zugriffsberechtigungen für die Datenbank.|  
  
## <a name="remarks"></a>Bemerkungen  
 Mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_helprole **können Sie eine Liste der**-Rollen in der aktuellen Datenbank anzeigen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Liste der Windows-Gruppen mit Zugriff auf die aktuelle Datenbank ausgegeben.  
  
```  
EXEC sp_helpntgroup;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_helprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
