---
description: sp_getmergedeletetype (Transact-SQL)
title: sp_getmergedeletetype (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getmergedeletetype
- sp_getmergedeletetype_TSQL
helpviewer_keywords:
- sp_getmergedeletetype
ms.assetid: 64450e4d-844d-4176-874e-f3845536f7d2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d2a254a81bdd4b1a4d7718e8960ced22666b5705
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538920"
---
# <a name="sp_getmergedeletetype-transact-sql"></a>sp_getmergedeletetype (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt den Typ des Mergelöschvorgangs zurück. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank oder auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_getmergedeletetype [ @source_object = ] 'source_object', [ @rowguid =] 'rowguid', [ @delete_type=] delete_type OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
`[ @source_object = ] 'source_object'` Der Name des Quell Objekts. *source_object* ist vom Datentyp **nvarchar (386)** und hat keinen Standardwert.  
  
`[ @rowguid = ] 'rowguid'` Der Zeilen Bezeichner für den Lösch Datentyp. *ROWGUID* ist vom Datentyp **uniqueidentifier**und hat keinen Standardwert.  
  
`[ @delete_type = ] delete_type OUTPUT` Der Code, der den Typ des Löschvorgang angibt. *delete_type* ist vom Datentyp **int**und hat keinen Standardwert. *delete_type* ist auch ein Output-Parameter und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Löschvorgang durch Benutzer|  
|**5**|Teilweiser Löschvorgang|  
|**6**|Löschvorgang durch System|  
  
## <a name="remarks"></a>Hinweise  
 **sp_getmergedeletetype** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_getmergedeletetype**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
