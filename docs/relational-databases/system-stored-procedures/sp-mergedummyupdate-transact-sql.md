---
description: sp_mergedummyupdate (Transact-SQL)
title: sp_mergedummyupdate (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergedummyupdate_TSQL
- sp_mergedummyupdate
helpviewer_keywords:
- sp_mergedummyupdate
ms.assetid: b834f7f6-9588-4d59-a3e2-83d8e8e722e1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 39558295ad31cfccd1f4df70e89580e2615fea56
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545961"
---
# <a name="sp_mergedummyupdate-transact-sql"></a>sp_mergedummyupdate (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Diese Prozedur führt für die angegebene Zeile ein Pseudoupdate durch, sodass sie beim nächsten Mergevorgang erneut gesendet wird. Diese gespeicherte Prozedur kann auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_mergedummyupdate [ @source_object =] 'source_object', [ @rowguid =] 'rowguid'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @source_object = ] 'source_object'` Der Name des Quell Objekts. *source_object*ist vom Datentyp **nvarchar (386)** und hat keinen Standardwert.  
  
`[ @rowguid = ] 'rowguid'` Der Zeilen Bezeichner. *ROWGUID* ist vom Datentyp **uniqueidentifier**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_mergedummyupdate** wird bei der Mergereplikation verwendet.  
  
 **sp_mergedummyupdate** ist nützlich, wenn Sie eine eigene Alternative zum Replikationskonflikt-Viewer (Wzcnflct.exe) schreiben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **db_owner** Fixed-Daten Bank Rolle können **sp_mergedummyupdate**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
