---
description: sp_helpreplicationdboption (Transact-SQL)
title: sp_helpreplicationdboption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6733b1f473c91094bd8af177bce4b13f3cf1b03e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89526973"
---
# <a name="sp_helpreplicationdboption-transact-sql"></a>sp_helpreplicationdboption (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Zeigt an, ob die Datenbanken auf dem Verleger für die Replikation aktiviert sind. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt. *Diese Option wird für Oracle-Verleger nicht unterstützt.*  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpreplicationdboption [ [ @dbname =] 'dbname' ]  
    [ , [ @type = ] 'type' ]  
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'dbname'` Der Name der Datenbank. *dbname* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert **%** . Wenn **%** der Wert ist, enthält das Resultset alle Datenbanken auf dem Verleger; andernfalls werden nur Informationen über die angegebene Datenbank zurückgegeben. Es werden keine Informationen für Datenbanken zurückgegeben, für die der Benutzer wie nachstehend beschrieben keine entsprechenden Berechtigungen besitzt.  
  
`[ @type = ] 'type'` Schränkt das Resultset so ein, dass es nur Datenbanken enthält, für die der angegebene Wert des Replikations options *Typs* aktiviert wurde *Type ist vom Datentyp* **vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**veröffentlichen**|Transaktionsreplikation ist zulässig.|  
|**Zusammenführen der Veröffentlichung**|Mergereplikation ist zulässig.|  
|**Replikation zulässig** (Standard)|Transaktionsreplikation und Mergereplikation sind zulässig.|  
  
`[ @reserved = ] reserved` Gibt an, ob Informationen zu vorhandenen Veröffentlichungen und Abonnements zurückgegeben werden. *reserved* ist vom Typ **Bit**und hat den Standardwert 0. Wenn der Wert **1**ist, enthält das Resultset Informationen dazu, ob die angegebene Datenbank über vorhandene Veröffentlichungen oder Abonnements verfügt.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Datenbank.|  
|**id**|**int**|Datenbankbezeichner.|  
|**transpublish**|**bit**|, Wenn die Datenbank für die Momentaufnahme-oder Transaktions Veröffentlichung aktiviert wurde. der Wert **1** bedeutet, dass die Momentaufnahme-oder Transaktions Veröffentlichung aktiviert ist.|  
|**mergepublish**|**bit**|, Wenn die Datenbank für die Mergeveröffentlichung aktiviert wurde. der Wert **1** bedeutet, dass die Mergeveröffentlichung aktiviert ist.|  
|**dbowner**|**bit**|, Wenn der Benutzer ein Mitglied der **db_owner** Fixed-Daten Bank Rolle ist. mit dem Wert **1** wird angegeben, dass der Benutzer ein Mitglied dieser Rolle ist.|  
|**dbreadonly**|**bit**|Gibt an, ob die Datenbank als schreibgeschützt gekennzeichnet ist. der Wert **1** bedeutet, dass die Datenbank schreibgeschützt ist.|  
|**haspublications**|**bit**|Gibt an, ob die Datenbank über vorhandene Veröffentlichungen verfügt. der Wert **1** bedeutet, dass vorhandene Veröffentlichungen vorhanden sind.|  
|**haspullsubscriptions**|**bit**|Ist, wenn die Datenbank über vorhandene Pullabonnements verfügt. der Wert **1** bedeutet, dass vorhandene Pullabonnements vorhanden sind.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helpreplicationdboption** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der festen Server Rolle **sysadmin** können **sp_helpreplicationdboption** für beliebige Datenbanken ausführen. Mitglieder der **db_owner** Fixed-Daten Bank Rolle können **sp_helpreplicationdboption** für diese Datenbank ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_replicationdboption &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
