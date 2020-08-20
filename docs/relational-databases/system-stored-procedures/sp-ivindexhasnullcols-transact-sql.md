---
description: sp_ivindexhasnullcols (Transact-SQL)
title: sp_ivindexhasnullcols (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_ivindexhasnullcols
- sp_ivindexhasnullcols_TSQL
helpviewer_keywords:
- sp_ivindexhasnullcols
ms.assetid: ed2cde63-37e1-43cf-b6ba-3b6114a0f797
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86fef9d3b131770e11edde117ea12e96d336de24
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464204"
---
# <a name="sp_ivindexhasnullcols-transact-sql"></a>sp_ivindexhasnullcols (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Überprüft, ob der gruppierte Index der indizierten Sicht eindeutig ist und keine Spalten enthält, die NULL-Werte zulassen, wenn die indizierte Sicht verwendet wird, um eine Transaktionsveröffentlichung zu erstellen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_ivindexhasnullcols [ @viewname = ] 'view_name'  
        , [ @fhasnullcols= ] field_has_null_columns OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
`[ @viewname = ] 'view_name'` Der Name der Sicht, die überprüft werden soll. *view_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @fhasnullcols = ] field_has_null_columns OUTPUT` Das Flag, das angibt, ob der Sicht Index über Spalten verfügt, die NULL zulassen. *view_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Gibt den Wert **1** zurück, wenn der Ansichts Index Spalten enthält, die NULL zulassen. Gibt den Wert **0** zurück, wenn die Sicht keine Spalten enthält, die NULL-Werte zulassen.  
  
> [!NOTE]  
>  Wenn die gespeicherte Prozedur selbst einen Rückgabecode von **1**zurückgibt, was bedeutet, dass bei der Ausführung der gespeicherten Prozedur ein Fehler aufgetreten ist, ist dieser Wert **0** und sollte ignoriert werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_ivindexhasnullcols** wird von der Transaktions Replikation verwendet.  
  
 Standardmäßig werden Artikel für indizierte Sichten in einer Veröffentlichung als Tabellen bei den Abonnenten erstellt. Wenn die indizierte Spalte jedoch NULL-Werte zulässt, wird die indizierte Sicht auf dem Abonnenten als indizierte Sicht erstellt und nicht als Tabelle. Durch die Ausführung dieser gespeicherten Prozedur kann der Benutzer gewarnt werden, wenn dieses Problem mit der aktuellen indizierten Sicht besteht.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_ivindexhasnullcols**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
